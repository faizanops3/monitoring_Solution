# setup

- Load the Grafana Dashboard ID = 193,
- taken from here: https://grafana.com/grafana/dashboards/193-docker-monitoring/

- Docker logs Dashboard ?? - https://grafana.com/grafana/dashboards/17921-docker-logs/ = 17921

---

### Simulating Alertss

```sh
curl -X POST -d @prom-alert.json http://localhost:2000/alertmanager
```
