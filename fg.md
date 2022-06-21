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


| FieldName     | Example       | Description     |
| ------------- | ------------- | --------------- |
|pid-file| l3afd.pid  | file used for stroing process id's|



