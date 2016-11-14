Consul
======

Consul setup

### Install

Follow instructions at [consul](https://www.consul.io/intro/getting-started/install.html) to install for your platform.
for Mac:
```bash
brew install consul
```

### Start

```bash
# To start the consul cluster
cd infra/consul
consul agent -data-dir=data/test
consul agent -config-file=server1.json -ui
consul agent -config-file=server2.json
consul agent -config-file=server3.json
consul agent -config-file=client1.json
```


### Access
Server 1 : http://localhost:9500/ui