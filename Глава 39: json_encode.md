Фильтр ```json_encode``` возвращает JSON представление переменной:

```twig
{{ data|json_encode() }}
```

Twig использует PHP-функцию ```json_encode```.

###### Аргументы

- ```options```: битовая маска (```{{ data|json_encode(constant('JSON_PRETTY_PRING')) }}```)
