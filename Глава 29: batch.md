Фильтр ```batch``` разбивает переданный список на "пачки" (куски, серии) определенного размера. Второй параметр может быть использован для заполнения недостающих значений:

```twig
{% set items = ['a', 'b', 'c', 'd', 'e', 'f', 'g'] %}

<table>
  {% for row in items|batch(3, 'No item') %}
    <tr>
      {% for column in row %}
        <td>{{ column }}</td>
      {% endfor %}
    </tr>
  {% endfor %}
</table>
```

Приведенный выше пример сгенерирует следующий HTML-код:

```twig
<table>
  <tr>
    <td>a</td>
    <td>b</td>
    <td>c</td>
  </tr> 
  <tr>
    <td>d</td>
    <td>e</td>
    <td>f</td>
  </tr>
  <tr>
    <td>g</td>
    <td>No item</td>
    <td>No item</td>
  </tr>
</table>
```

###### Аргументы

- ```size```: размер "пачки" (куска, серии). Дробные значения будут округлены до ближайшего целого вверх.
- ```fill```: значение по-умолчанию для отсутствующих мест.
