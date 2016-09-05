# New Relic plugin for Redis in Docker

This repository wraps the [newrelic_redis_plugin](https://github.com/kenjij/newrelic_redis_plugin) in a simple to use Docker image.

## Run

    $ docker run --env REDIS_URL=redis://host:port \
        --env NEWRELIC_LICENSE_KEY=<your New Relic license key> \
        sspinc/newrelic-redis

You can also specify the following environment variables:

* `REDIS_INSTANCE_NAME`: Name of the Redis instance that is being monitored. It defaults to the id of the container that runs the New Relic Redis agent.
* `REDIS_DB`: The Redis database number to monitor. Defaults to `db0`.

If you want to supply your own `newrelic_plugin.yml` you can mount it to the container:

    $ docker run --env REDIS_URL=redis://host:port \
        --env NEWRELIC_LICENSE_KEY=<your New Relic license key> \
        -v /path/to/your/newrelic_plugin.yml:/etc/newrelic_redis_plugin/newrelic_plugin.yml \
        sspinc/newrelic-redis

## Development

You can build it the image with

    $ make build
