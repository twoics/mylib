Возвращают первые **k** метрик с начала или последние **k** метрик с конца

```PromQL
>>> topk(1, process_cpu_seconds_total)
```

| Название                                                                             | Метрика |
| ------------------------------------------------------------------------------------ | ------- |
| process_cpu_seconds_total{instance="server:8000", job="website-constructor-backend"} | 7.43    |
