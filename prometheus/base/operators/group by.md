Группирует значения

```PromQL
>>> group by (job) (process_cpu_seconds_total)
```

| Название                            | Метрика |
| ----------------------------------- | ------- |
| {job="prometheus"}                  | 1       |
| {job="website-constructor-backend"} | 1       |
