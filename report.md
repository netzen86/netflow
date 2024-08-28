# Run monitoring tools with docker compose

`docker compose up -d`

# Run stress

`stress -c 2 -i 1 -m 1 --vm-bytes 800M -d 1 --hdd-bytes 100M -t 200s &`
# Run all service separate
## Install node_exporter
`https://github.com/prometheus/node_exporter/releases`

`wget url form github`

`tar xvzf node_exporter-1.7.0.linux-amd64.tar.gz` 

`./node_exporter &`

## Install Prometheus
`docker pull prom/prometheus`

`docker run --name prometheus -v $(realpath ./)/prometheus.yml:/etc/prometheus/prometheus.yml -d -e TZ=UTC -p 9090:9090 --add-host host.docker.internal:host-gateway prom/prometheus`

`/etc/prometheus/prometheus.yml`

## Install Grafana

`docker run -d -p 3000:3000 --add-host host.docker.internal:host-gateway --name=grafana grafana/grafana-oss`