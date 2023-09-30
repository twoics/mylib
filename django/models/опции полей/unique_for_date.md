Требует указания названия поля типа `DateField` или `DateTimeField` чтобы требовать уникальной пары:
(текущее поле + указанное поле типа `date`)

Пример:
```
some_date = DateField()
title = CharField(
	unique_for_date='some_date'
)
```

При создании объекта, с уже существующей парой (`some_date` и `title` выкинет исключение). 
При этом ограничения на `some_date` и `title` по отдельности **не накладываются**

Так же есть `unique_for_month` и `unique_for_year`
