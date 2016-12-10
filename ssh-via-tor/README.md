# ssh-via-tor
With Ports Closed: SSH where it shouldn't be possible.

This is my vm.

screenshot 1

I can't ssh to it from outside because my ISP gives me an NAT'ed IP 192.168.1.X. I could ask them to route traffic to the external IP port 22 to my NAT IP where I would then route it to my VM but that's a pain and no guarantee that they'd do it.  What can I do?

Recently I've been working on projects for making easy TOR services. For example, with my [Torify Wordpress](https://github.com/tgeek77/tor-fied-wordpress) project you can create a web server container with Wordpress installed without opening port 80, 443, or anything else. The TOR service takes care of the data transport for me. It hit me, can I do this with ssh? After a bit of Googling, it looks like I can. I created a fresh base Ubuntu container, installed openssh-server and tor. I started the service. I updated /etc/tor/torrc to include localhost port 22 as something that is should be handling. I then started tor and got my new .onion address from /var/lib/tor/hidden_service/hostname

screenshot 2

The difficulty now is, how to test it? I found two possibilities. Both required TOR to be installed on the the remote host i.e. remote from the host that we want to get into with the SOCKS proxy function enabled. SSH doesn't handle the SOCKS proxy natively and that's where 

###netcat###
Using netcat, you can use the following command to connect to your remote server with ssh:

```
ssh -o ProxyCommand='nc --proxy-type socks4 --proxy 127.0.0.1:9050 %h %p' user@host.onion
```
This is a long and inwieldly command, but it can be made into an alias easily. The downside to using this function is that it is limited to SSH only.

###Proxychains###
Proxychains is another option, but it's not as common. While netcat may be available in many different Linux distributions, Praxychains may need to be [built from source](http://proxychains.sourceforge.net/).

Add 127.0.0.1 9050 to /etc/proxychains.conf

```
$ vi /etc/proxychains.conf
```

Run ssh or any application that needs to access the TOR proxy using proxychains as a wrapper

```
$ proxychains ssh user@host.onion
```




