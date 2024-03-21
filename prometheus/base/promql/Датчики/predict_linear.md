Показывает, какое значение датчика будет через N времени, исходя из текущих тенденций

```PromQL
>>> predict_linear(node_filesystem_free_bytes{job="node"}[1h], 4 * 3600)
```
