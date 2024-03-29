
## repr vs str

- repr нужен для удобного просмотра разработчиками
- str нужен для удобного просмотра пользователями

## classmethod

- classmethod часто используется как альтернативный конструктор

## format

Очень мощная вещь, позволяющая управлять выводом, как пример `datetime`

```python
>>> format(now, '%H:%M:%S')
'18:49:05'
```

Для этого нужно реализовать метод класса

```python
def __format__(self, fmt_spec=''):
```

## Методы `__eq__` и `__hash__`

Почему они должны реализовываться вместе ?

Потому что если два **объекта равны** то их **хеши** тоже должны быть **равны**


## Закрытые и защищенные атрибуты

- Если у атрибута два начальных прочерка он сохранится как `_ClassName__attribute` (это называется декорирование имен)


## `__slots__`
Позволяет сэкономить память при использовании объекта, помещая атрибуты не в **отдельный словарь** а внутрь самого объекта (в скрытый массиве ссылок экземпляра)

При этом
- **Нельзя** создать новые атрибуты
- `__slots__` должен присутсвовать до создания экземпляра (логично)
- Экземпляр класса теряет атрибут `__dict__` 

```python
>>> class Pixel:
	__slots__ = ('x', 'y') 

>>> p = Pixel() 
>>> p.__dict__
AttributeError: 'Pixel' object has no attribute '__dict__'

>>> p.x = 10
>>> p.y = 20

>>> p.color = 'red'
AttributeError: 'Pixel' object has no attribute 'color'
```


#### Прикол с дочерними классами

	Дочерние классы, от классов в которых есть __slots__ наследуют его не 
	польностью

**Важно**
- В дочерних классах доступен метод `__dict__`
- Можно добавить новые атрибуты (и они будут добавлены в `__dict__`)
- Атрибуты, которые объявлены в `__slots__` экзепляра будут добавлены в **скрытый массив ссылок**, а не в `__dict__`

```python
>>> class OpenPixel(Pixel):
		pass

>>> op = OpenPixel()
>>> op.__dict__
{}
>>> op.x = 8
>>> op.__dict__
{}
>>> op.x
8
>>> op.color = 'green'
>>> op.__dict__
{'color': 'green'}
```

#### Как избежать такого поведения

	Необходимо довать в дочерний класс __slots__

- Если необходимо вовсе ограничить добавление новых атрибутов то в качестве `__slots__` нужно указать **пустой** кортеж (базовые останутся)
- Если нужно добавить ещё атрибутов то добавить их в `__slots__ = ('color',)`

#### Зачем это

	Позволяет экономить память


## offtopic
	bool – подкласс int


#### Утиная типизация
	Пытаться выполнить действие и ловить исключения

#### Гусиная типизация
	Сравнивать тип с ABC посредством isinstance

#### Плюсы и минусы

	Утиная типизация обладает большей гибкостью, а явная проверка типов дает 
	более предсказуемый результат

	Для библиотек лучше утиная типизация
 