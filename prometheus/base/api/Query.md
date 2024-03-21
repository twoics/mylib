
```HTTP
http://localhost:9090/api/v1/query?query=process_resident_memory_bytes
```

### Response
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
