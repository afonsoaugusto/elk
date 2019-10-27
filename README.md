# ELK Stack in Swarm Mode

This repository uses the new Docker Compose v3 format to create an ELK stack using swarm mode.

## Prerequisites:

1. Docker Engine 17.06.0+
2. Docker Compose 1.14+
3. Set the following on nodes that will be running Elasticsearch:
    1. `sysctl -w vm.max_map_count=262144`
    2. `echo 'vm.max_map_count=262144' >> /etc/sysctl.conf` (to persist reboots)

## Usage

1. Clone this repository
2. On a machine that is communicating with the swarm cluster:
    1. `docker stack deploy -c $(pwd)/docker-compose.yml elk`

## notes

```sh
docker run -d -p 9000:9000 --name portainer --restart always -v /var/run/docker.sock:/var/run/docker.sock portainer/portainer


sudo docker swarm init --advertise-addr 192.168.100.8
docker stack deploy --prune -c $(pwd)/docker-compose.yml elk

docker stack services elk
docker stack rm elk

docker service ls
docker service ps --no-trunc

```

## References

https://github.com/ahromis/swarm-elk
