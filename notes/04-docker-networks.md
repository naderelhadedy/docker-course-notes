# Docker Networks

## Network Types

![Course screenshot](../images/20261117214539.png)

![Course screenshot](../images/20261117214558.png)

### Default Bridge Network
- Containers use the default bridge network by default, where they can communicate only by IP address because there is no DNS.

![Course screenshot](../images/20261117214310.png)

### Custom Bridge Network
- `Network`: docker network create mynetwork | docker ...... --network mynetwork (attach network)
	- With this network attached, containers can communicate by hostname, IP address, or container name because DNS is provisioned.

![Course screenshot](../images/20261117214006.png)

### Overlay Network
- Communication between multiple containers on different nodes/servers.

![Course screenshot](../images/20261117214750.png)
