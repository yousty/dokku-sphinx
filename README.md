# dokku sphinx (beta)
## requirements

- dokku 0.4.x+
- docker 1.8.x

## installation

```shell
# on 0.4.x+
dokku plugin:install https://github.com/yousty/dokku-sphinx.git sphinx
```

Plugin requires a directory to write to (default `/var/lib/dokku/services/sphinx`) and a volume to read configuration from (default `/var/lib/dokku/data/storage`)

## commands

```
sphinx:create <name>            Create a sphinx service with environment variables
sphinx:destroy <name>           Delete the service and stop its container if there are no links left
sphinx:expose <name> [port]     Expose a sphinx service on custom port if provided (random port otherwise)
sphinx:info <name>              Print the connection information
sphinx:link <name> <app>        Link the sphinx service to the app
sphinx:list                     List all sphinx services
sphinx:logs <name> [-t]         Print the most recent log(s) for this service
sphinx:promote <name> <app>     Promote service <name> as SPHINX_URL in <app>
sphinx:restart <name>           Graceful shutdown and restart of the sphinx service container
sphinx:start <name>             Start a previously stopped sphinx service
sphinx:stop <name>              Stop a running sphinx service
sphinx:unexpose <name>          Unexpose a previously exposed sphinx service
sphinx:unlink <name> <app>      Unlink the sphinx service from the app
```

## usage

**Important!**
Make sure to include listen ports listed below in your sphinx.conf:
```
searchd {
  ...
  listen = 9312
  listen = 127.0.0.1:9306:mysql41
  ...
}
```

```shell
# create a sphinx service named foo
dokku sphinx:create foo

# you can also specify the image and image
# version to use for the service
# it *must* be compatible with the
# leodido/sphinxsearch image
export SPHINX_IMAGE="leodido/sphinxsearch"
export SPHINX_IMAGE_VERSION="2.2.10"

# you can also specify custom environment
# variables to start the sphinx service
# in semi-colon separated form
export SPHINX_CUSTOM_ENV="USER=alpha;HOST=beta"

# get connection information as follows
dokku sphinx:info foo

# a sphinx service can be linked to a
# container this will use native docker
# links via the docker-options plugin
# here we link it to our 'bar' app
# NOTE: this will restart your app
dokku sphinx:link foo bar
```
