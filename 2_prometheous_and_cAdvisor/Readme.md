# setup

- Load the Grafana Dashboard ID = 193,
- taken from here: https://grafana.com/grafana/dashboards/193-docker-monitoring/

- Docker logs Dashboard ?? - https://grafana.com/grafana/dashboards/17921-docker-logs/ = 17921

---

## Send Docker Containers Logs to Loki

1. We will first need to install a docker driver to send logs to Loki

   ```sh
   sudo docker plugin install grafana/loki-docker-driver:latest --alias loki --grant-all-permissions
   ```

2. update /etc/docker/daemon.json file and add below content

   ```json
   {
     "debug": true,
     "log-driver": "loki",
     "log-opts": {
       "loki-url": "http://localhost:3100/loki/api/v1/push",
       "loki-batch-size": "400"
     }
   }
   ```

3. Restart all the containres

   `systemctl restart docker`

---

## Docker plugin for Grafana

What it will do?

it will bring the the docker logs to grafana

### List all the docker plugins

```sh
sudo docker plugin ls
```
