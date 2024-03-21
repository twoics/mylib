Создание просто счетчика
```python
REQUESTS = Counter('hello_worlds_total',
'Hello Worlds requested.')

...
if something:
	REQUESTS.inc()
```


## Важно
Счетчики можно увеличивать не только **на 1** но и на любое **неотрицательное число**
```python
REQUESTS.inc(22)
```
