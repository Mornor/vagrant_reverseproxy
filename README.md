required on host:

virtualbox, vagrant



h1. setup and run vagrant 
*  Change network configuration in Vagrantfile to reflect your network setup (e.g. change public IP of virtual machine)

to start vagrant machine run 

```
vagrant up
```

then connect 

```
vagrant ssh
```

start nginx reverse proxy in fg mode


```
cd nginx_reverseproxy/
docker-compose up
```


in a second terminal on vagrant box start some demo webservers. use different hostnames or the same hostname multiple times:

```
docker run \
    --expose 80 \
    --net nginxreverseproxy_default \
    -e VIRTUAL_HOST=myhostname \
    -d nginxdemos/hello
```

from any machine in your local network

```
curl -H "Host: myhostname" 192.168.2.100
```