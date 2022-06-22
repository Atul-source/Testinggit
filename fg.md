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
|max-nf-restart-count|`"3"`|Maximum number of attempts to monitor eBPF Program|
|max-nfs-attach-count|`"10"`| Todo|
|bpf-chaining-enabled|`"true"`|Boolean to set bpf-chaining |
|bpf-delay-time|`"5"`|Todo|
|swagger-api-enabled|`"false"`|Boolean to check swagger api enable or not|
|environment|`"PROD"`| Environment  variable |

## [kf-repo]
| FieldName     | Example       | Description     |
| ------------- | ------------- | --------------- |
|url| `"http://localhost:8000/"`|Default Repository to Download eBPF Programs|

## [web]
| FieldName     | Example       | Description     |
| ------------- | ------------- | --------------- |
|metrics-addr|`"0.0.0.0:8898"`|Prometheus endpoint for pull/scrape the metrics|
|kf-poll-interval|`"30s"`|Periodic Interval to scrape metrics using Prometheus|
|n-metric-samples|`"20"`|Number of Metric Samples|

## [admind]
| FieldName     | Example       | Description     |
| ------------- | ------------- | --------------- |
|host|`""`|Hostname of admin|
|username|`""`|Username of admin|
|api-key|`""`|Api key of admin|
|groud-id|`"0"`|Group id of admin|
|api-enabled|`"true"`|Boolean to check api enabled or not|

## [xdp-root-program]
| FieldName     | Example       | Description     |
| ------------- | ------------- | --------------- |
|name|`"xdp_root"`|Name of xdp_root program|
|artifact|`"xdp-root.tar.gz"`|Archive of xdp_root program|
|ingress-map-name|`"root_array"`|Ingress map name of xdp_root program|
|command|`"xdp_root"`|Command to run xdp_root program|
|version|`"1.01"`|Version of xdp_root program|
|is-user-program|`"false"`|Boolean to check xdp_root is kernel space or user space program|

## [tc-root-program]
| FieldName     | Example       | Description     |
| ------------- | ------------- | --------------- |
|name|`"tc_root"`|Name of tc_root program|
|artifact|`"l3af_tc_root.tar.gz"`|Archive of tc_root program|
|ingress-map-name|`"tc_ingress_root_array"`|Ingress map name of tc_root program|
|egress-map-name|`"tc_egress_root_array"`|Egress map name of tc_root program|
|command|`"tc_root"`|Command to run tc_root program|
|version|`"1.0"`|Version of tc_root program|
|is-user-program|`"false"`|Boolean to check tc_root is kernel space or user space program|

## [ebpf-chain-debug]
| FieldName     | Example       | Description     |
| ------------- | ------------- | --------------- |
|addr|`"0.0.0.0:8899"`|Address of ebpf chain debuging|
|enabled|`"true"`|Boolean to check ebpf-chain-debuging is enabled or not|

## [l3af-configs]
| FieldName     | Example       | Description     |
| ------------- | ------------- | --------------- |
|restapi-addr|`"localhost:53000"`| Address of l3af-configs rest api |

# [l3af-config-store]
| FieldName     | Example       | Description     |
| ------------- | ------------- | --------------- |
|filename|`"/etc/l3afd/l3af-config.json"`|Absolute path of persistent config file|

# [mtls]
| FieldName     | Example       | Description     |
| ------------- | ------------- | --------------- |
|enabled| `"true"` | Boolean to check mtls enabled or not|
|min-tls-version|`""`| Minimum tls version allowed|
|cert-dir|`"/etc/l3af/certs"`|Absolute path of ca certificates |
|server-crt-filename|`"server.crt"`|Server's ca certificate filename|
|server-key-filename|`"server.key"`|Server's key filename|
|cert-expiry-warning-days|`"30"`|How many days before expiry you want warning|





