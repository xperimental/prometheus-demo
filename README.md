# Prometheus demo environment

This repository contains a small `docker-compose` environment for demoing prometheus with a few active exporters.

## Components

| Port | Component                                                                | Description                             |
|-----:|:-------------------------------------------------------------------------|:----------------------------------------|
| 3000 | [PromDash](https://github.com/prometheus/promdash)                       | Graphing dashboard                      |
| 8080 | [goecho](https://hub.docker.com/r/xperimental/goecho/)                   | Example service                         |
| 9090 | [Prometheus](https://github.com/prometheus/prometheus)                   | Metrics database                        |
| 9091 | [Pushgateway](https://github.com/prometheus/pushgateway)                 | Gateway for batch jobs                  |
| 9093 | [Alertmanager](https://github.com/prometheus/alertmanager)               | Aggregation and notification for alerts |
| 9100 | [Node exporter](https://github.com/prometheus/node_exporter)             | Hardware metrics                        |
| 9104 | [Container exporter](https://github.com/docker-infra/container_exporter) | Docker container metrics                |

## Usage

```bash
# Pull all images
docker-compose pull
# Setup promdash database
docker-compose run promdash ./bin/rake db:migrate
# Run environment (blocking)
docker-compose up
```

After starting you will have to configure PromDash to point to the prometheus server. Keep in mind that it needs the IP
of the host the docker containers are running on to access prometheus (`localhost` will only work on linux).
