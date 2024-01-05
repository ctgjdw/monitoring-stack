# Monitoring Stack

## Logging

There are 2 different log collectors here

1. [Vector](https://vector.dev/) - Used by Openshift4 (current)
2. [Fluentd/bit](https://docs.fluentd.org/) - Used by Openshift4 (legacy), `fluent-bit` is the lightweight version

### Logging Benchmark

[Reference](https://medium.com/ibm-cloud/log-collectors-performance-benchmarking-8c5218a08fea). Vector has a higher throughput and efficiency, and is able to handle logs with lower latency (streaming) as compared to Fluent's bulk methodology.

### Setup

1. Create docker network. `docker network create host-net`
1. Opensearch
    - uncomment `services.opensearch.logging` in `docker-compose.yml` if using `fluent-bit/d`
    - `cd ./opensearch && docker compose up -d`
1. [Vector](./vector-logging/setup.md)
1. [Fluent-bit](./fluent-bit-logging/setup.md)

## Metrics

Metrics are exported by applications in the `prometheus` format via plugins and exporter containers/sidecars. These metrics are then crawled and ingested by the `prometheus` server.

The metrics can then be visualised using `grafana` via dashboards.

### Setup

1. [Prometheus](./prometheus-metrics-store/setup.md)
1. [Grafana](./grafana-dashboards/setup.md)