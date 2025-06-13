---
description: For instructions on how to configure Fadah for multiple servers.
---

# Multi Server

### Pre-Requisites

You must first have an [external database setup](database.md). You must also have a Redis server. (Or a server that uses the Redis protocol)\
This should be running the latest version.

### Configuration

Find the configuration section at the bottom of the config.yml file and configure it as follows.

The configuration (and database) MUST be identical for all connected servers.

{% code title="plugins/Fadah/config.yml" %}
```yaml
broker:
  enabled: true
  type: REDIS
  host: your-redis-server-ip
  port: your-redis-server-port
  password: your-redis-server-password
  channel: fadah:cache
```
{% endcode %}

Once you have completed the configuration on all of your servers, fully restart your servers and you will now be connected!

### Redis Server Hosting

Refer to this amazing guide by William!\
[https://william278.net/docs/website/redis-hosts](https://william278.net/docs/website/redis-hosts)
