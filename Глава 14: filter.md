Теги фильтров позволяют применить стандартные фильтры Twig к блокам данных шаблона. Для этого достаточно обернуть код в специальный тег ```filter```:

```twig
{% filter upper %}
  Этот текст станет полностью состоять из прописных букв.
{% endfilter %}
```

Фильтры можно объединять в цепочки:

```twig
{% filter lower|escape %}
  <strong>SOME TEXT</strong>
{% endfilter %}

{# результат: "&lt;strong&gt;some text&lt;/strong&gt;" #}
```
