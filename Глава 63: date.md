Преобразует аргумент в дату для сравнения:

```twig
{% if date(user.created_at) < date("-2days") %}
  ...
{% endif %}
```

Аргумент должен быть в одном из поддерживаемых PHP форматов даты и времени.

В качестве второго аргумента возможна передача временной зоны:

```twig
{% if date(user.created_at) < days("-2days", "Europe/Paris") %}
  ...
{% endif %}
```

Если никакие аргументы не были переданы, то функция возвращает текущую дату:

```twig
{% if date(user.created_at) < date() %}
  {# ... всегда выполняется ... #}
{% endif %}
```

Для глобальной установки значения временной зоны воспользуйтесь функцией ```setTimezone()``` модуля ```core```:

```php
$twig = new Twig_Environment($loader);
$twig->getExtension("Twig_Extension_Core")->setTimezone("Europe/Paris");
```

###### Аргументы

- ```date```: дата
- ```timezone```: временная зона
