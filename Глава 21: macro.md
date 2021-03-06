Макросы подобны функциям в обычных языках программирования. Они полезны при частом использование одинаковых HTML-сущностей, которые можно вынести в отдельные макросы и повторно использовать не прибегая к копированию.

Пример простого макроса, который отображает текстовый элементы формы:

```twig
{% macro input(name, value, type, size) %}
  <input type="{{ type|default('text') }}" name="{{ name }}" value="{{ value|e }}" size="{{ size|default(20) }}">
{% endmacro %}
```

Макросы отличаются от PHP-функций несколькими моментами:

- Значения по-умолчанию для аргументов описываются фильтром ```default``` в теле самого макроса.
- Аргументы макроса всегда опциональны.
- Если в макрос переданы дополнительные аргументы (кроме определенных в самом макросе), то они окажутся в специальной переменной ```varargs``` в виде списка значений.

Однако, как и PHP-функции, макросы не имеют доступа к текущим переменным контекста. Если необходимо передать весь контекст, то можно воспользоваться специальной переменной ```_context```.

##### import

Макросы могут быть определены в любом шаблоне и перед любым использованием они должны быть импортированы:

```twig
{% import 'forms.html' as forms %}
```

В приведенном выше примере файл шаблона ```forms.html``` импортируется в переменную ```forms```, в которой, затем, будут доступны описанные макросы:

```twig
<p>{{ forms.input('username') }}</p>
<p>{{ forms.input('password', null, 'password') }}</p>
```

Если макрос определён и используется в том же файле, то для его импорта необходимо воспользоваться специальной переменной ```_self```:

```twig
{% import _self as forms %}

<p>{{ forms.input('username') }}</p>
```

Если необходимо использовать один макрос в другом макросе, то для этого понадобится импортировать используемый макрос локально:

```twig
{% macro input(name, value, type, size) %}
  <input type="{{ type|default('text') }}" name="{{ name }}" value="{{ value|e }}" size="{{ size|default(20) }}" />
{% endmacro %}

{% macro wrapped_input(name, value, type, size) %}
  {% import _self as forms %}
  
  <div class="field">
    {{ forms.input(name, value, type, size) }}
  </div>
{% endmacro %}
```

##### Именованные закрывающие теги макросов

Twig даёт возможность использовать имя макроса в его закрывающем теге для лучше читаемости:

```twig
{% macro input() %}
{% endmacro input %}
```
