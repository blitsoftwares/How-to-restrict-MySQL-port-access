# How-to-restrict-MySQL-port-access

On some Linux distributions, port 3306 is open after you install MySQL. This article describes two methods for restricting or blocking access to port 3306 on an unmanaged server.

## Configure firewall rules
You can use iptables to create firewall rules that restrict access to port 3306. The advantage of this method is that you can selectively grant or deny access to port 3306 based on IP addresses or other criteria.

For example, to block external access to port 3306 completely, type the following command:

```
$ iptables -A INPUT -p tcp --dport 3306 -j DROP
```

Similarly, to grant access to a specific IP address and block all others, type the following commands. Replace xxx.xxx.xxx.xxx with the IP address for which you want to grant access:

```
$ iptables -A INPUT -p tcp --dport 3306 -s xxx.xxx.xxx.xxx -j ACCEPT
$ iptables -A INPUT -p tcp --dport 3306 -j DROP
```
