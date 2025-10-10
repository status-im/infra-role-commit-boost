# Description

This role provisions a [commit-boost](https://github.com/Commit-Boost/commit-boost-client) installation that can act as a payload builder for ETH2 nodes.

# Introduction

The role will:

* Start a node by defining a [Docker Compose](https://docs.docker.com/compose/compose-application-model/)
* Setup Consul service with checks

# Ports

The service exposes these ports:

* `18550` API port(`commit_boost_cont_port`)

* `10000` metrics port(`commit_boost_cont_metrics_port`)


# Installation

Add to your `requirements.yml` file:

```yaml
- name: infra-role-commit-boost
  src: git+git@github.com:status-im/infra-role-commit-boost.git
  scm: git
```

# Configuration

The crucial settings are:

```yaml
commit_boost_network: 'holesky'
commit_boost_relays:
  - id:  'titan'
    url: 'https://0xaa58208899c6105603b74396734a6263cc7d947f444f396a90f7b7d3e65d102aec7e5e5291b27e08d02c50a050825c2f@holesky.titanrelay.xyz'
```

# Management

## Service

Manged by `docker-compose`:

```sh
docker-compose start
docker-compose stop
docker-compose restart
```

You can view logs with `docker`:

```sh
docker logs commit-boost
```

# Links

- https://commit-boost.github.io/commit-boost-client/
- https://ethstaker.cc/mev-relay-list
