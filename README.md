# About this Repository
This repository contains custom builds of Telegraf for usage with Nvidia Cuda.

# Supported tags and respective Dockerfile links
- [1.18](https://github.com/darki73/cudagraf/blob/main/cudagraf/1.18/Dockerfile)
- [1.21](https://github.com/darki73/cudagraf/blob/main/cudagraf/1.21/Dockerfile)
- [latest](https://github.com/darki73/cudagraf/blob/main/cudagraf/1.21/Dockerfile)

# Using this image
## Exposed Ports
- 8125 StatsD
- 8092 UDP
- 8094 TCP

## Using the default configuration
The default configuration requires a running InfluxDB instance as an output plugin. Ensure that InfluxDB is running on port 8086 before starting the Telegraf container.

Minimal example to start an InfluxDB container:
```shell
$ docker run -d --name influxdb -p 8086:8086 influxdb
```

Starting Telegraf using the default config, which connects to InfluxDB at http://localhost:8086/:
```shell
$ docker run --runtime=nvidia --net=container:influxdb telegraf
```

For installation process of Nvidia Drivers on your machine, please refer to [this link](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html).

## Example of Grafana Dashboard
![Grafana Dashboard Example](https://github.com/darki73/cudagraf/blob/main/images/grafana.png?raw=true)