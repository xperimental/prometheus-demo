# Prometheus demo environment

This repository contains a small `docker-compose` environment for demoing prometheus with a few active exporters.

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

## Exposed ports

| Port | Component          |
|-----:|:-------------------|
| 3000 | PromDash           |
| 9090 | Prometheus         |
| 9091 | Pushgateway        |
| 9093 | Alertmanager       |
| 9100 | Node exporter      |
| 9104 | Container exporter |
