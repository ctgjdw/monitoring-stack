# Prometheus

Metrics are exported by applications in the `prometheus` format via plugins and exporter containers/sidecars. These metrics are then crawled and ingested by the `prometheus` server.

Prometheus has a web ui at [http://localhost:9090](http://localhost:9090).

## Setup

1. Configure `prometheus.yml` with the targets to scrape
1. `docker compose up -d` to run

## Exporters

The various exporters are configured:

Default (included with the app, no installation required):

1. `Prometheus`

1. `Grafana`

Installed:

1. `node-exporter`: via a docker container in `docker-compose.yml`

1. `opensearch`: via a plugin in the `opensearch` container