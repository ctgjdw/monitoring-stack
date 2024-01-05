# Setup

The Vector log collector server is configured with `/etc/vector/vector.yaml`. This config file contains:

1. sources - collection sources, e.g. docker daemon
2. transforms - transformers, e.g. parsing, custom code (VRL)
3. sinks - export destinations, e.g. elastic

## Deploy

This example takes in a docker source (filters only to opensearch container), parses the raw string line into an object and inserts into the final response (flat). Lastly, it forwards to `opensearch`. This is configured in `vector.yaml`

1. Edit `vector.yaml`
1. `docker compose up -d` to bring up the server

## Analyse in Opensearch Dashboards >= 2.11.1

1. Create an index pattern
    1. `Dashboards Management` > `Index Patterns` > `Create`
    1. Define pattern: `vector*`, for example
1. Go to `Observability` > `Logs` > `Explorer`
    1. Select datasource > `vector*`
    1. Configure timeframe and `Refresh`
