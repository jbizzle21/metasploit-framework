# Namespaceing

## Interact with Linux namespace

There's a intro here for linux network namespaces: [https://blog.scottlowe.org/2013/09/04/introducing-linux-network-namespaces/](https://blog.scottlowe.org/2013/09/04/introducing-linux-network-namespaces/)

List namespaces:

```
$ lsns
        NS TYPE   NPROCS   PID USER             COMMAND
4026531835 cgroup    152     1 root             /sbin/init
4026532985 mnt         1  2721 root             /metrics-server

```

Interact with the specific namespace of a process \(2721 is the process\):

{% code title="Enter namespace of process 2721:" %}
```bash
nsenter -t 2721 -n

```
{% endcode %}

Once in the namespace the output from commands will reflect the namespace you are in:

```bash
#For example - the following is from 2721 process
ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
3: eth0@if7: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1450 qdisc noqueue state UP mode DEFAULT group default 
    link/ether 0a:96:18:52:ac:4a brd ff:ff:ff:ff:ff:ff link-netnsid 0

```

Show the current namespace:

```bash
ip netns identify $$
```

List the Container netns interface \(note that these correspond to the number of vethX interfaces\)

```bash
ls /var/run/netns/
cni-1970b555-202d-8eb9-cc41-9ad4f76c7804  cni-51a47907-fa07-4d24-f634-a86a4431eb15  cni-88a7e790-1b3a-2c03-2e63-139c8251d151  cni-b6af33bb-09a9-7abe-6f55-525111b41e6d  cni-d74f809d-7e79-e51b-a201-2ab00543581f
cni-25edcf89-8446-0c1d-8d1d-fe5265a91235  cni-646825bc-7304-535f-5896-cf036f0ac40d  cni-8ac3596b-0c94-f3e2-8496-f83314c0e7e2  cni-bf49ee11-f990-e200-84c7-bf0d41e66f0f  cni-f38ca55b-1e90-2880-2589-85f175adf57a
cni-2a761332-4805-6957-9c17-4da78d597c80  cni-6628d700-40c1-e5ea-8979-e982cc2ca16b  cni-984ac2ec-1411-4418-6cd0-908d5f2c6bee  cni-c90b1a05-e126-b1a5-b299-8f5ea8fc0640  cni-f78238aa-e811-e4d0-44bd-dd242074fe87

```

Or use:

```bash
ip netns list
```

