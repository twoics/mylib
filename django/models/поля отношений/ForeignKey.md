Отношение типа `один ко многим`

Представим ситуацию:

Таблица ***Person***	
```
| pk | name |
| -- | ---- |
| 1  | Чел  |
| 2  | Пчел |
```

Таблица ***Phone***
```
| pk | phone_name    | person_pk |
| -- | ------------- | --------- |
| 1  | Iphone 12     | 1         |
| 2  | Iphone 11     | 1         |
| 3  | Xiaomi Note 7 | 2         |
```

В данном случае, `person_pk` будет внешним ключом

В **Django** это будет записываться так
 ```
class Person(models.Model):
	name = models.CharField()

class Phone(models.Model):
	phone_name = models.CharField()
	person = models.ForeignKey(to='Person')
```

**На естественном языке можно сказать**

	Что у одного пользователя может быть несколько телефонов



### Рекурсивная связь
Для создания рекурсивного отношения, с "самим собой" можно использовать

```
models.ForeignKey('self')
```

### Индекс
Индекс для `ForeignKey` создается автоматически

### Опции
- `on_delete`
