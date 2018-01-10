Фильтр ```trim``` позволяет удалить символы пробелов в начале и конце строки:

```twig
{{ ' I like Twig! '|trim }}
{# вывод: 'I like Twig!' #}

{{ ' I like Twig.'|trim('.') }}
{# вывод: ' I like Twig' #}

{{ ' I like Twig. '|trim(side='left') }}
{# вывод: 'I like Twig. ' #}

{{ ' I like Twig! '|trim(side='right') }}
{# вывод: ' I like Twig!' #}
```

Twig использует PHP-функции ```trim```, ```ltrim``` и ```rtrim```.

###### Аргументы

- ```character_mask```: cимволы для удаления
- ```side```: сторона с которой необходимо удалить символы; по-умолчанию символы удаляются как с левой, так и с правой стороны.
