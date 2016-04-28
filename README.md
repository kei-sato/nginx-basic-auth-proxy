# build

```
docker build -t nginx-basic-auth-proxy .
```

# run

```
# pseudo back end server (whatever you want)
docker run --name nginx -d nginx

# launch basic auth proxy with user and password
docker run --name nginx-basic-auth-proxy -d -p 80:80 --link nginx:backend -e USER=user1 -e PASS=pass1 nginx-basic-auth-proxy

# open in browser
open http://$(docker-machine ip)/
```

# specify backend host and port

```
docker run --name nginx -d nginx
docker run --name nginx-basic-auth-proxy -d -p 80:80 --link nginx:nginx -e BACKEND=nginx:80 -e USER=user1 -e PASS=pass1 nginx-basic-auth-proxy
```

# default values

```
BACKEND=backend:80
USER=supersecure
USER=itsnot
```
