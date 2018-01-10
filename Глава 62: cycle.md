Функция ```cycle``` производит циклическое чтение элементов массива:

```twig
{% set start_year = date() | date('Y') %}
{% set end_year = start_year + 5 %}

{% for year in start_year..end_year %}
  {{ cycle(['odd', 'even'], loop.index0) }}
{% endfor %}
```

Массив может содержать любое количество значений:

```twig
{% set fruits = ['apple', 'orange', 'citrus'] %}

{% for i in 0..10 %}
  {{ cycle(fruits, i) }}
{% endfor %}
```

###### Аргументы

- ```position```: позиция цикла
