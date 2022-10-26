# Python: La guía sencilla

## Introducción
Esta guía está inspirada en Python Tips, un libro escrito por Yasoob Ullah Khalid. El objetivo de esta guía es ofrecer de forma clara, en español y con ejemplos prácticos, diversos tópicos de Python que pueden ser de utilidad para usuarios novatos, intermedios e incluso avanzados. También puede servir como una hoja de acceso rápido. Este no es un tutorial para aprender a programar, sino una referencia rápida, con la finalidad reunir mucha información que se encuentra dispersa en internet.

## Requisitos
Para esta guía estoy utilizando python3. Específicamente la versión Python 3.7.

# Resumen

## `*args` y `**kwargs`
`*args` y `**kwargs` se utilizan generalmente como parámetros de una función en algunos contextos explicados a continuación. Es importante destacar que no importa realmente el nombre que se le de a estos parámetros, sino que los caracteres realmente relevantes son `*` y `**`, así, podríamos renombrarlos como `*parameters_1` o bien `**random_name`. Sin embargo, por convención se utiliza `*args` y `**kwargs`.

### Uso de `*args`
`*args` permite pasar una cantidad arbitraria de argumentos a una función, y disponer de ellos sin un nombre en específico. El acceso a este valor se trata como si fuera una lista.
```python
def the_beatles_band(favourite_beatle: str, *args):
    print(f'This is my favourite Beatle: {favourite_beatle}')
    for another_beatle in args:
        print(f'This is another Beatle: {another_beatle}')

the_beatles_band('George Harrison', 'Paul McCartney', 'Ringo Starr', 'John Lennon')

> This is my favourite Beatle: George Harrison
> This is another Beatle: Paul McCartney
> This is another Beatle: Ringo Starr
> This is another Beatle: John Lennon
```
### Uso de `**kwargs`
A diferencia de `*args`, `**kwargs` también permite pasar una cantidad arbitraria de argumentos a una función, pero asociado esta vez a una llave, lo que permite poder referenciarlo directamente.
```python
def get_hero_superpower(**kwargs) -> str:
    for key, value in kwargs.items():
        print(f'{key}: {value}')
    print(f'{kwargs.get('name')} superpower is: {kwargs.get('superpower')}')
    return kwargs.get('superpower')

get_hero_superpower(
    {
        'name': 'Batman',
        'age': 26,
        'city': 'Gotham City',
        'superpower': 'Money'
    }
)

> name: Batman
> age: 26
> city: Gotham City
> superpower: Money
> Batman superpower is: Money
```