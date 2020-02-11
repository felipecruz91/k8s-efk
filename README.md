# k8s-efk
Elasticsearch + Fluentd + Kibana in K8s

## Deploy ElasticSearch

Create a namespace for the installation target.

```shell
$ kubectl create namespace logging
```

## Generate Log Events
Run this container to start generating random log events.

```shell
$ kubectl run random-logger --image=chentex/random-logger --generator=run-pod/v1
```

The log events will look something like this.
```shell
...
2019-03-27T11:06:25+0000 INFO takes the value and converts it to string.
2019-03-27T11:06:29+0000 DEBUG first loop completed.
2019-03-27T11:06:31+0000 ERROR something happened in this execution.
2019-03-27T11:06:46+0000 WARN variable not in use.
...
```

Inspect the actual log events now being generated with this log command.

```shell
$ kubectl logs pod/random-logger
```

Don't be alarmed by the messages, these are just samples.

