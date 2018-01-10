Фильтр ```url_encode``` кодирует строку или массив в строку, безопасную для передачи в URL:

```twig
{{ 'path_seg*ment'|url_encode }}
{# вывод: path_seg%2Ament #}

{{ 'string with spaces'|url_encode }}
{# вывод: 'string%20with%20spaces' #}

{{ {'param': 'value', 'foo': 'bar'}|url_encode }}
{# вывод: 'param=value&foo=bar' #}
```

Twig использует PHP-функцию ```rawurlencode```.
