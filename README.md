Minimal wrapper library for general metrics writing using telegraf.

# Usage

Using this library assumes you have a socket listener input setup in your telegraf config, like so (can be udp, tcp, or unix):

```
[[inputs.socket_listener]]
  service_address = "udp://localhost:8094"
```

Creating a client and pushing metrics:

```go
client := telegraf.NewClientImpl("udp://localhost:8094")

point := &telegraf.Metric{
    Measurement: "foo_measure",
    Tags:        map[string]interface{}{
                    "tag1": "bar1", 
                    "tag2": "bar2",
                 },
    Fields:      map[string]interface{}{
                    "field1": "foo1", 
                    "field2": 2,
                 },
}

client.WritePoint(point)
```
