# Find PID of a Container

Get the container ID:

```
$ docker ps
```

Get the PID of the process:

{% code title="" %}
```bash
docker inspect --format '{{.State.Pid}}' <container PID>
```
{% endcode %}



