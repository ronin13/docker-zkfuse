# docker-zkfuse

 Dockerfile for FUSE provider of Zookeeper Znode namespace.

## Image

Available at https://hub.docker.com/r/ronin/zkfuse/

### Running

1. If zookeeper is running locally at 0.0.0.0:2181,

```
mkdir -p /tmp/host-mount/volume
docker run  --name zkfuse --net=host -v /tmp/host-mount:/zkmount:shared --device /dev/fuse --cap-add SYS_ADMIN  --rm ronin/zkfuse:latest   /usr/bin/zkfuse -d  -m /zkmount/volume -z 0.0.0.0:2181
```

2. If zookeeper is remote at $hostname:$port (or a list of host:port tuple),

```
mkdir -p /tmp/host-mount/volume
docker run  --name zkfuse -v /tmp/host-mount:/zkmount:shared --device /dev/fuse --cap-add SYS_ADMIN  --rm ronin/zkfuse:latest   /usr/bin/zkfuse -d  -m /zkmount/volume -z $host:$port
```
