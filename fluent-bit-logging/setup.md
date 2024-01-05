# Setup

The Fluent-bit log collector server is configured with `/fluent-bit/etc/fluent-bit.conf`. This config file contains:

1. input - collection sources, e.g. docker
1. parser - parses raw data to structured data
1. filter - transformations like filtering, appending, etc.
1. output - export destinations, e.g. elastic

## Deploy

This example takes in a docker source (docker daemon will forward the logs, see `docker-compose.yml`), and forwards the raw logs with some docker metadata to `opensearch` with a logstash index. This is configured in `fluent-bit.conf`

1. Edit `fluent-bit.conf`
1. `docker compose up -d` to bring up the server

## Analyse in Opensearch Dashboards >= 2.11.1

1. Create an index pattern
    1. `Dashboards Management` > `Index Patterns` > `Create`
    1. Define pattern: `logstash*`, for example
1. Go to `Observability` > `Logs` > `Explorer`
    1. Select datasource > `logstash*`
    1. Configure timeframe and `Refresh`
