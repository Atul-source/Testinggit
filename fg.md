# L3AFD Config  Options Documentation

See [l3afd.cfg](https://github.com/l3af-project/l3afd/blob/main/config/l3afd.cfg) for a full example configuration.


```
[DEFAULT]

[l3afd]
pid-file: ./l3afd.pid
datacenter: dummy
bpf-dir: /dev/shm
bpf-log-dir:
kernel-major-version: 4
kernel-minor-version: 15
shutdown-timeout: 1s
http-client-timeout: 10s
max-nf-restart-count: 3
max-nfs-attach-count: 10
bpf-chaining-enabled: true
bpf-delay-time: 5
swagger-api-enabled: false
# PROD | DEV
environment: PROD
....
```

### Below is the detailed documentation for each field


## [l3afd]
| FieldName     | Example       | Description     |
| ------------- | ------------- | --------------- |
|pid-file| `"l3afd.pid"`  |It contains process id of eBPF Programs |
|datacenter| `"dummy"` | Name of DataCenter|
|bpf-dir| `"/dev/shm"` | Absolute Path of eBPF Programs (where they are extracted) |
|bpf-log-dir|`""`      | Absolute Path where we store logs eBPF Programs|
|kernel-major-version|`"4"`|Major version of kernel|
|kernel-minor-version|`"15"`|Miner version of kernel (Ex 4.15)|
|shutdown-timeout|`"1s"`|It is the amount of time allowed to stop all network functions|
|http-client-timeout|`"10s"`|It is the amount of time allowed to get response headers|
|max-nf-restart-count|`"3"`|maximum number of attempts to monitor eBPF Program|
|max-nfs-attach-count|`"10"`| Todo|
|bpf-chaining-enabled|`"true"`|boolean to set bpf-chaining |
|bpf-delay-time|`"5"`|Todo|
|swagger-api-enabled|`"false"`|boolean to check swagger api enable or not|
|environment|`"PROD"`| environment  variable |


