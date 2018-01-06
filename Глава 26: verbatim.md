Тег ```verbatim``` позволяет отметить текст, как не требущий парсинга. Например, для отображения отрывка кода Twig:

```twig
{% verbatim %}
  <ul>
    {% for item in seq %}
      <li>{{ item }}</li>
    {% endfor %}
  </ul>
{% endverbatim %}
```

