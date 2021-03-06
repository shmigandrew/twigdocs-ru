Фильтр ```escape``` позволяет экранировать выводимые данные для безопасного отображения. Фильтр поддерживает различные стратегии экранирования в зависимости от контекста шаблона.

По-умолчанию используется HTML-стратегия экранирования:

```twig
{{ user.username|escape }}
```

Для удобство использование у фильтра ```escape``` есть псевдоним ```e```:

```twig
{{ user.username|e }}
```

Благодаря опциональному аргументу фильтр может применять различные стратегии:

```twig
{{ user.username|e }}
{# равносильно #}
{{ user.username|e('html') }}
```

А вот так возможно экранировать переменные в JS-коде:

```twig
{{ user.username|e('js') }}
{{ user.username|escape('js') }}
```

Фильтр ```escape``` поддерживает следующие стратегии экранирования:

- ```html```: экранирует строку в контексте HTML-кода.
- ```js```: экранирует строку в контексте JS-кода.
- ```css```: экранирует строку в контексте CSS-кода.
- ```url```: экранирует строку в контексте параметров URL.
- ```html_attr```: экранирует строку в контексте HTML-аттрибута.

Фильтр ```escape``` в Twig использует PHP-функцию ```htmlspecialchars``` для экранирования строк в контексте HTML-кода (HTML-стратегия).

При использовании автоматического экранирования Twig старается не экранировать повторно переменную используемую в том же контексте для которого работает экранирование, но это не работает, если в качестве стратегии экранирования в фильтр ```escape``` передаётся переменная со значением стратегии, нежели статичная строка.

```twig
{% set strategy = 'html' %}

{% autoescape 'html' %}
  {{ var|escape('html') }} {# переменная var не будет два раза экранирована #}
  {{ var|escape(strategy) }} {# переменная var будет второй раз экранирована #}
{% endautoescape %}
```

При использовании переменной для указания стратегии экранирования воспользуйтесь фильтром ```raw``` для избежания двойного экранирования:

```twig
{% set strategy = 'html' %}

{% autoescape 'html' %}
  {% var|escape(strategy)|raw %} {# переменная var не будет два раза экранирована #}
{% endautoescape %}
```

###### Произвольные экранировщики

В Twig возможно определить собственные стратегии экранирования, для этого необходимо вызвать метод ```setEscaper()``` экземпляра класса ```core```. Первый аргумент - название экранировщика (которое будет использоваться при вызове фильтра ```escape``` и ```e```), второй - действительный PHP-callable объект:

```php
$twig = new Twig_Environment($loader);
$twig->getExtension('Twig_Extension_Core')->setEscaper('csv', 'csv_escaper');
```

При вызове из Twig PHP-callable переменная получает 3 параметра: экземпляр класса окружения, строку для экранирования, кодировку. Стоит помнить, что встроенные экранировщики не могут быть переопределены в целях сохранения скорости работы.

###### Аргументы

- ```strategy```: стратегия экранирования
- ```charset```: кодировка передаваемой строки
