Фильтр ```nl2br``` заменяет все переходы на новую строку (```\n```) на HTML-тег ```<br />```:

```twig
{{ "I like Twig.\nYou will like it too."|nl2br }}

{# вывод:
  I like Twig.<br />
  You will like it too.
#}
```
