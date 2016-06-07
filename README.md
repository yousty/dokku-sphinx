# dokku sphinx (beta)
## requirements

- dokku 0.4.x+
- docker 1.8.x

## installation

```shell
# on 0.4.x+
dokku plugin:install https://github.com/yousty/dokku-sphinx.git sphinx
```

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
