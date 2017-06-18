
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