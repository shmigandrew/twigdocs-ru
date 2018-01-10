Когда шаблон использует наследование или есть необходимость использовать один блок несколько раз, то рекомендуется воспользоваться функцией ```block```:

```twig
<title>{% block title %}{% endblock %}</title>

<h1>{{ block('title') }}</h1>

{% block body %}{% endblock %}
```

Функция ```block``` может быть так же использована для отображения определенного блока из другого шаблона:

```twig
{{ block('title', 'common_tempalate.twig') }}
```

Используйте ```defined```-тест, чтобы определить, существует ли блок в текущем контексте:

```twig
{% if block('footer') is defined %}
  ...
{% endif %}

{% if block('footer', 'common_blocks.twig') is defined %}
{% endif %}
```

