Функция ```constant``` возвращает значение константы заданное указанной строковой переменной:

```twig
{{ some_date|date(constant('DATE_W3C')) }}
{{ constant('Namespace\\Classname::CONSTANT_NAME') }}
```

Присутствует возможность читать константы из объектов:

```twig
{{ constant('RSS', date) }}
```

Воспользуйтесь ```defined```-тестом для проверки существования константы:

```twig
{% if constant('SOME_CONST') is defined %}
  ...
{% endif %}
```
