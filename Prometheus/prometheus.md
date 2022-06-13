# Getting Started with Prometheus
## Introduction
- Written in GO
- Time series database + Web Server + Engine
- Data is collected regularly
- Good balance between In-memory storage and disk storage
- Data structur: key / timestamp / value
- Double delta is possible to limit storage usage: data is written only if changed.

## Installation de prometheus
### Docker installation
```
docker run -d --name prometheus -v $PWD/etc/:/etc/prometheus/ -v $PWD/data/:/prometheus/ -p 9090:9090 quay.io/prometheus/prometheus:v2.33.5
```
### Debian installation
```bash
sudo apt-get install prometheus
```

## Configuration 
```
$ cat /etc/prometheus/prometheus.yml
# Sample config for Prometheus.

global:
  scrape_interval:     15s # Set the scrape interval to every 15 seconds. Default is every 1 minute.
  evaluation_interval: 15s # Evaluate rules every 15 seconds. The default is every 1 minute.
  # scrape_timeout is set to the global default (10s).

  # Attach these labels to any time series or alerts when communicating with
  # external systems (federation, remote storage, Alertmanager).
  external_labels:
      monitor: 'example'

# Alertmanager configuration
alerting:
  alertmanagers:
  - static_configs:
    - targets: ['localhost:9093']

# Load rules once and periodically evaluate them according to the global 'evaluation_interval'.
rule_files:
  # - "first_rules.yml"
  # - "second_rules.yml"

# A scrape configuration containing exactly one endpoint to scrape:
# Here it's Prometheus itself.
scrape_configs:
  # The job name is added as a label `job=<job_name>` to any timeseries scraped from this config.
  - job_name: 'prometheus'

    # Override the global default and scrape targets from this job every 5 seconds.
    scrape_interval: 5s
    scrape_timeout: 5s

    # metrics_path defaults to '/metrics'
    # scheme defaults to 'http'.

    static_configs:
      - targets: ['localhost:9090']

  - job_name: node
    # If prometheus-node-exporter is installed, grab stats about the local
    # machine by default.
    static_configs:
      - targets: ['localhost:9100']

```

<br>


## Reload de configuration

```
curl -X POST http://localhost:9090/-/reload
```

<br>

