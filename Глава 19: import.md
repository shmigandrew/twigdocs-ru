Twig поддерживает возможность повторного использования кода путём выноса его в макросы. Эти макросы могут находиться в различных файлах шаблонов, а затем импортироваться в любой другой шаблон.

Есть два способа импортирования шаблонов. У вас есть возможность импортировать как весь шаблон в переменную, так и запросить определенный макрос и импортировать только его.

Представьте, что у нас есть вспомогательный модуль, который содержит методы отображения полей форм и находится в файле ```forms.html```:

```twig
{% macro input(name, value, type, size) %}
  <input type="{{ type|default('text') }}" name="{{ name }}" value="{{ value|e }}" size="size|default(20)" />
{% endmacro %}

{% macro textarea(name, value, rows, cols) %}
  <textarea name="{{ name }}" rows="{{ rows|default(10) }}" cols="{{ cols|default(40) }}">{{ value|e }}</textarea>
{% endmacro %}
```

Самый простой способ воспользоваться объявленными макросами - импортировать весь модуль в переменну, а затем обращаться к макросам, как к аттрибутам объекта:

```twig
{% import 'forms.html' as forms %}

<dl>
  <dt>Username</dt>
  <dd>{{ forms.input('username') }}</dd>
  <dt>Password</dt>
  <dd>{{ forms.input('password', null, 'password') }}</dd>
</dl>
<p>{{ forms.textarea('comment') }}</p>
```

Альтернативный вариант - импортировать в текущее пространство имён только те макросы, которые вам понадобятся:

```twig
{% from 'forms.html' import input as input_field, textarea %}

<dl>
  <dt>Username</dt>
  <dd>{{ input_field('username') }}</dd>
  <dt>Password</dt>
  <dd>{{ input_field('password', null, 'password') }}</dd>
</dl>
<p>{{ textarea('comment') }}</p>
```

Чтобы импортировать максрос из текущего файла, то в качестве источника воспользуйтесь специальной переменной ```_self```.
