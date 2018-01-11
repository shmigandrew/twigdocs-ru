Функция ```template_from_string``` загружает шаблон из строки:

```twig
{{ include(template_from_string('Hello {{ name }}')) }}
{{ include(template_from_string(page.template)) }}
```

По-умолчанию функция ```template_from_string``` недоступна. При создании Twig-окружения необходимо явно добавить расширение ```Twig_Extension_StringLoader```:

```php
$twig = new Twig_Environment(...);
$twig->addExtension(new Twig_Extension_StringLoader());
```

Несмотря на то, что в большинстве случаев вы будете использовать функцию ```template_from_string``` в комбинации с функцией ```include```, функцию ```template_from_string``` можно использовать и с другими тегами / функциями, которые принимают в качестве аргументов шаблоны (например, ```embed``` и ```extends```).

###### Аргументы

- ```template```: шаблон
