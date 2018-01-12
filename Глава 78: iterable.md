Тест ```iterable``` проверяет если переменная является массивом или перечисляемым объектом:

```twig
{# результат выражения true, если переменная foo является массивом или перечисляемым объектом #}
{% if users is iterable %}
  {% for user in users %}
    Hello, {{ user }}!
  {% endfor %}
{% else %}
  Hello, {{ users }}!
{% endif %}
```
