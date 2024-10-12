# setup

- Load the Grafana Dashboard ID = 193,
- taken from here: https://grafana.com/grafana/dashboards/193-docker-monitoring/

- Docker logs Dashboard ?? - https://grafana.com/grafana/dashboards/17921-docker-logs/ = 17921

---

### Simulating Alert-test

```sh
curl -X POST -d @prom-alert.json http://localhost:2000/alertmanager
```

---

For production, since you only need to access **Grafana**, you can limit the open ports to just the necessary services and close the rest. Here's the breakdown of the ports in your Docker Compose file:

### Required Open Port

- **Grafana**:
  - **Port 3000** should remain open so you can access Grafana at `http://<EC2-IP>:3000`.

### Ports You Can Close

If you don’t need to access other services (Prometheus, Loki, cAdvisor, etc.) from outside the instance, you can close the following ports:

- **Prometheus**: Port 9090
- **Alertmanager**: Port 9093
- **cAdvisor**: Port 8080
- **Loki**: Port 3100
- **Prometheus-MSTeams**: Port 2000

### Security Group Recommendation

For production, ensure the following:

- **Open port 3000** (Grafana) to only your IP or a limited set of trusted IPs.
- **Close all other ports** unless you need to access them from outside.

This approach will improve security by limiting external access to just Grafana.
