Так же не стоит создавать `total` метки

```text
some_metric{label="foo"} 7
some_metric{label="bar"} 13
some_metric{label="total"} 20
```

или

```
some_metric{label="foo"} 7
some_metric{label="bar"} 13
some_metric{} 20
```


#### Кратко про то, почему не надо 
Такая операция должна выполняться в `PromQL` задача метрик - хранить значение, не стоит предварительно их агрегировать 
