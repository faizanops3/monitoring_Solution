# setup

- Download loki config
  wget https://raw.githubusercontent.com/grafana/loki/v2.8.0/cmd/loki/loki-local-config.yaml -O loki-config.yaml

docker run -d --name loki -v $(pwd):/mnt/config -p 3100:3100 grafana/loki:2.8.0 --config.file=/mnt/config/loki-config.yaml

- loki runs on 3100

---

- Load the Grafana Dashboard ID = 16966,
- taken from here: https://grafana.com/grafana/dashboards/16966-container-log-dashboard/
