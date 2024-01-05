# Grafana Dashboards

Grafana can be used to query datastores (e.g. Prometheus) and visualise the data in dashboards.

This setup has the following provisioned:

1. Basic Auth
```
GF_SECURITY_ADMIN_USER: admin
GF_SECURITY_ADMIN_PASSWORD: password
```
1. Datasource - configured in `./setup/datasources/prometheus.yml`
1. Dashboards - configured in `./setup/dashboards/default.yml` and stored `./dashboards`

# Setup

1. Configure settings above and in `docker-compose.yml`
1. `docker compose up -d` to run