# docker-gelf-stack


DRIVER              VOLUME NAME
local               elasticsearch_storage
local               grafana_storage

NAME                     DRIVER              SCOPE 
monitoring-network-001   overlay             swarm
monitoring-network-002   overlay             swarm
services-network-001     overlay             swarm
services-network-002     overlay             swarm
services-network-003     overlay             swarm
ui-network-001           overlay             swarm
ui-network-002           overlay             swarm


## grafana
$ docker run \
  -d \
  -p 3000:3000 \
  --name=grafana \
  -e "GF_SERVER_ROOT_URL=http://grafana.server.name" \
  -e "GF_SECURITY_ADMIN_PASSWORD=secret" \
  grafana/grafana



Setting	Default value
GF_PATHS_CONFIG	/etc/grafana/grafana.ini
GF_PATHS_DATA	/var/lib/grafana
GF_PATHS_HOME	/usr/share/grafana
GF_PATHS_LOGS	/var/log/grafana
GF_PATHS_PLUGINS	/var/lib/grafana/plugins
GF_PATHS_PROVISIONING	/etc/grafana/provisioning


custom build

docker build -t grafana:latest-with-plugins \
  --build-arg "GRAFANA_VERSION=latest" \
  --build-arg "GF_INSTALL_PLUGINS=grafana-clock-panel,grafana-simple-json-datasource" .


Version	User	User ID
< 5.1	grafana	104
>= 5.1	grafana	472<Paste>
