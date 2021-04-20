---
description: >-
  If you are able to compromise the node-passwd you can use this to spin up your
  own agent and access a K3 deployment.
---

# Connecting a K3 agent

## Create and connect an agent

Set environmental variables:

```
$ K3s_URL=https://server:6443
K3S_TOKEN=<node-token>
```

{% hint style="info" %}
 Super-powers are granted randomly so please submit an issue if you're not happy with yours.
{% endhint %}

Create an agent:

```bash
curl -sfL https://get.k3s.io | K3S_URL=${k3s_url} K3S_TOKEN=${k3s_token} sh - 
```

Install a specific agent version

```bash
curl -sfL https://get.k3s.io | INSTALL_K3S_VERSION=vX.Y.Z-rc1 sh -
```



