```HTTP
http://localhost:9090/api/v1/query_range?query=rate(process_resident_memory_bytes[5m])&start=1708832800&end=1708832845&step=60
```

^e8914d

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
