# Install HAProxy

> sudo add-apt-repository ppa:vbernat/haproxy-1.8
> sudo apt-get update
> sudo apt-get install haproxy

## Editing the configuration

Now edit haproxy default configuration file /etc/haproxy/haproxy.cfg and start configuration.

> sudo vi /etc/haproxy/haproxy.cfg

## Adding HAProxy Listener:

Now tell HAProxy to where to listen for new connections. As per below configuration HAProxy will list on port 80 of 192.168.1.12 ip address.

`frontend Local_Server bind 192.168.1.12:80 mode http default_backend My_Web_Servers`

## Add Backend Web Servers:

As per above configuration haproxy is now listening on port 80. Now define the backend web servers where HAProxy send the request.

`backend nodes mode http balance roundrobin option forwardfor http-request set-header X-Forwarded-Port %[dst_port] http-request add-header X-Forwarded-Proto https if { ssl_fc } option httpchk HEAD / HTTP/1.1rnHost:localhost server web1.example.com 192.168.1.101:80 server web2.example.com 192.168.1.102:80 server web3.example.com 192.168.1.103:80`
