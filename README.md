# docker-zkfuse
[![](https://images.microbadger.com/badges/version/ronin/docker-zkfuse.svg)](https://microbadger.com/images/ronin/docker-zkfuse "Get your own version badge on microbadger.com")
[![](https://images.microbadger.com/badges/image/ronin/docker-zkfuse.svg)](https://microbadger.com/images/ronin/docker-zkfuse "Get your own image badge on microbadger.com")
![docker](http://dockeri.co/image/ronin/zkfuse)

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
