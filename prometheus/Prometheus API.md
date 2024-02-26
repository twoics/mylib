
	Prometheus может принимать запросы по API и отдавать результат в виде json


## Query

```HTTP
http://localhost:9090/api/v1/query?query=process_resident_memory_bytes
```

```json
{
  "status": "success",
  "data": {
    "resultType": "vector",
    "result": [
      {
        "metric": {
          "__name__": "process_resident_memory_bytes",
          "instance": "localhost:9090",
          "job": "prometheus"
        },
        "value": [
          1708833835.047,
          "93036544"
        ]
      },
      {
        "metric": {
          "__name__": "process_resident_memory_bytes",
          "instance": "server:8000",
          "job": "website-constructor-backend"
        },
        "value": [
          1708833835.047,
          "110047232"
        ]
      }
    ]
  }
}
```


## QueryRange

	То же самое, только позволяет посылать запросы на период времени

```HTTP
http://localhost:9090/api/v1/query_range?query=rate(process_resident_memory_bytes[5m])&start=1708832800&end=1708832845&step=60
```

```json
{
  "status": "success",
  "data": {
    "resultType": "matrix",
    "result": [
      {
        "metric": {
          "instance": "localhost:9090",
          "job": "prometheus"
        },
        "values": [
          [
            1708832800,
            "919996.7999775438"
          ],
          [
            1708832860,
            "609729.1228070175"
          ],
          [
            1708832920,
            "307930.80750310526"
          ],
        ]
      },
      {
        "metric": {
          "instance": "server:8000",
          "job": "website-constructor-backend"
        },
        "values": [
          [
            1708832800,
            "2315102.3157894732"
          ],
          [
            1708832860,
            "2697668.7157894736"
          ],
          [
            1708832920,
            "3081657.936842105"
          ],
        ]
      }
    ]
  }
}
```
