Значение по умолчанию. Можно указать напрямую, или указать `вызываемый` объект

```
def contact_default():
    return {"email": "to1@example.com"}

contact_info = JSONField(
	"ContactInfo",
	 default=contact_default
)
```

**НО** `lambda` функции нельзя присвоить `default`

Для указания `default` для `ForeignKey` требуется указать значение **поля** на которое оно ссылается (`pk`)
