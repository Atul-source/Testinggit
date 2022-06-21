# L3AFD Config  Options Documentation

See [l3afd.cfg](https://github.com/l3af-project/l3afd/config/l3afd.cfg) for a full example configuration.


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

| Key                 | Type                                           | Example                                                        | Description                                                                                                                      |
|---------------------|------------------------------------------------|----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
| name                | string                                         | ratelimiting                                                   | Name of the eBPF Program                                                                                                         |
| seq_id              | number                                         | `1`                                                            | Position of the eBPF program in the chain. Count starts at 1.                                                                    |
| artifact            | string                                         | `"l3af_ratelimiting.tar.gz"`                                   | Userspace eBPF program binary and kernel eBPF byte code in tar.gz format                                                         |
| map_name            | string                                         | `"/sys/fs/bpf/ep1_next_prog_array"`                            | Chaining program map in the file system with path. This should match the eBPF program code.                                      |
| cmd_start           | string                                         | `"ratelimiting"`                                               | The command used to start the eBPF program. Usually the userspace eBPF program binary name.                                      |
| cmd_stop            | string                                         |                                                                | The command used stop the eBPF program                                                                                           |
| cmd_status          | string                                         |                                                                | The command used to get the status of the eBPF program                                                                           |
| version             | string                                         | `"latest"`                                                     | The version of the eBPF Program                                                                                                  |
| user_program_daemon | boolean                                        | `true` or `false`                                              | Whether the userspace eBPF program continues running after the eBPF program is started                                           |
| admin_status        | string                                         | `"enabled"` or `"disabled"`                                    | This represents the program status. `"enabled"` means to be started if not running.  `"disabled"` means to be stopped if running |
| prog_type           | string                                         | `"xdp"` or `"tc"`                                              | Type of eBPF program. Currently only XDP and TC network programs are supported.                                                  |
| cfg_version         | number                                         | `1`                                                            | Payload version number                                                                                                           |
| start_args          | map                                            | `{"collector_ip": "10.10.10.2", "verbose":"2"}`                | Argument list passed while starting the eBPF Program                                                                             |
| stop_args           | map                                            |                                                                | Argument list passed while stopping the eBPF Program                                                                             |
| status_args         | map                                            |                                                                | Argument list passed while checking the running status of the eBPF Program                                                       |
| map_args            | map                                            | `{"rl_config_map": "2", "rl_ports_map":"80,443"}`              | eBPF map to be updated with the value passed in the config                                                                       |
| monitor_maps        | array of [monitor_maps](#monitor_maps) objects | `[{"name":"cl_drop_count_map","key":0,"aggregator":"scalar"}]` | The eBPF maps to monitor for metrics and how to aggregate metrics information at each interval metrics are sampled               |

Note: `name`, `version`, the Linux distribution name, and `artifact` are
combined with the configured KF repo URL into the path that is used to download
the artifact containing the eBPF program. For example, if
`name="ratelimiting"`, `version="latest"`, and
`artifact="l3af_ratelimiting.tar.gz"` and L3AFD is running on Ubuntu 20.04.3
LTS (Focal Fossa), then we would look for the artifact at:

`http://{kf repo configured in l3afd.cfg}/ratelimiting/latest/focal/l3af_ratelimiting.tar.gz`

## monitor_maps

|Key|Type|Example|Description|
|--- |--- |--- |--- |
|name|string|`"rl_drop_count_map"`|The name of the map where metrics are stored|
|key|number|0|The index in the map specified by `name` where metrics are stored|
|aggregator|string|scalar|The type of metrics aggregation to use for the configured metric sampling interval. Supported values are `"scalar"`, `"max-rate"`, and `"avg"`.|
