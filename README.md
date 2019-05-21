# Practicing Consul

> This is an intro to Consul

For this purpose we will create the servers in digitalocean

> For us to implement some of the security mechanisms at a later point, we need to name all of our machines within a single domain. This is so that we can leverage a wildcard SSL certificate in the future.

*ip is example only*
```
+-----------------------+------------+-------------------------+
|       Hostname        | IP Address |          Role           |
+-----------------------+------------+-------------------------+
| server1.edmamerto.com |  192.0.2.1 | bootstrap consul server |
| server2.edmamerto.com |  192.0.2.2 | consul server           |
| server3.edmamerto.com |  192.0.2.3 | consul server           |
| agent1.edmamerto.com  | 192.0.2.50 | consul client           |
+-----------------------+------------+-------------------------+
```
download screen
```
$ apt-get update
$ apt-get install unzip screen
```
Start a screen session
```
$ screen
```
download consul
```
$ cd /usr/local/bin
$ wget https://dl.bintray.com/mitchellh/consul/0.3.0_linux_amd64.zip
$ unzip *.zip
$ rm *.zip
```
Start the bootstrap server `server1`
> this will make this server the cluster leader
```
$ consul agent -server -bootstrap -data-dir /tmp/consul
```
Start other servers `server2` and `server3`

```
$ consul agent -server -data-dir /tmp/consul
```
join all the servers... in `server1`, exit out of your session
```
CTRL-A C
```
*to switch sessions* 
```
CTRL-A N
```
join `server2` and `server3` from `server1`
```
$ consul join 192.0.2.2 192.0.2.3
```
check
```
$ consul members
```
Remove `server1` in bootstrap mode (servers are supposed to operate as equals and make decisions by quorum).

switch back to session
```
CTRL-A N
``` 
Stop service
```
CTRL-C
```
 Restart service without bootstrap
```
$ consul agent -server -data-dir /tmp/consul
```
Switch back to open terminal
```
CTRL-A N
```
Rejoin the cluster  with one of the two servers
```
$ consul join 192.0.2.2
```
