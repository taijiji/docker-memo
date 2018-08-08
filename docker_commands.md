
# confirm container status

```
docker ps
docker ps -a
```

# run command in container machine

```
docekr exec 0ee226119e61 ls -al /usr/share/nginx/html
```

# using bash mode in container

-i (--interactive=true)
-t (--tty=true)

```
% docker exec -i -t 0ee226119e61 bash
root@0ee226119e61:/#
root@0ee226119e61:/# uname -a
Linux 0ee226119e61 4.9.27-moby #1 SMP Thu May 11 04:01:18 UTC 2017 x86_64 GNU/Linux
```


# bind volume from host machine to container
using '-v(--volume)' option.

```
docker run -P -d -v /Users/taiji/work/study/docker:/usr/share/nginx/html nginx
```

# build using docker files


# create & connect network

```
# create docker networks
docker network create net1
docker network create net2

# connect docker instances to the networks
docker network connect net1 ceos1
docker network connect net1 ceos2
docker network connect net2 ceos1
docker network connect net2 ceos2

# start the instances
docker start ceos1
docker start ceos2

# check network status

docker network ls

NETWORK ID          NAME                    DRIVER              SCOPE
6eca767cbdc2        bridge                  bridge              local
3aef68408a02        host                    host                local
bb1f27539fca        net1                    bridge              local
29333c03cd8c        net2                    bridge              local


docker inspect ceos1

[
    {
        (snippet)
        
        "NetworkSettings": {

            (snippet)

            "Networks": {
                "bridge": {

                    (snippet)

                },
                "net1": {
                    "IPAMConfig": {},
                    "Links": null,
                    "Aliases": [
                        "e1ce8ae27112"
                    ],
                    "NetworkID": "bb1f27539fca83d5073fe244636d95ccd9fa4ba7be40d02fb54112df7688862a",
                    "EndpointID": "5be33a9641f98e4d43dfd00a8d2ea9a1581316b9c0c2a9b6acf4ea34dab4a327",
                    "Gateway": "172.19.0.1",
                    "IPAddress": "172.19.0.2",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "02:42:ac:13:00:02",
                    "DriverOpts": null
                },
                "net2": {
                    "IPAMConfig": {},
                    "Links": null,
                    "Aliases": [
                        "e1ce8ae27112"
                    ],
                    "NetworkID": "29333c03cd8c102c17114ce4dc61d1a823dc9ba7d221bdf5814c3549629bc71e",
                    "EndpointID": "2d1fcc2599365257138362fc310f94fcf493893111ddb4be363abbf97431ce87",
                    "Gateway": "172.20.0.1",
                    "IPAddress": "172.20.0.2",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "02:42:ac:14:00:02",
                    "DriverOpts": null
                }
            }
        }
    }
]
```

# remove docker network

after stopping container whitch connected network

docker network rm net1 
