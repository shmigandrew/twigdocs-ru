Тест ```same as``` проверяет если одна переменная идентична другой. Тест эквивалентен оператору ```===``` в PHP:

```twig
{% if foo.attribute is same as(false) %}
  значение аттрибута attribute объекта foo действительно равно false
{% endif %}
```
