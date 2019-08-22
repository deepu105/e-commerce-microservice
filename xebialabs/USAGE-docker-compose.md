## Find the apps here:
* XL Deploy: http://localhost:4516
  * username: admin
  * password: admin
* XL Release: http://localhost:5516
  * username: admin
  * password: admin
* Jenkins: http://localhost:8080
  * username: admin
  * password: admin


Copy `xebialabs/config.yaml` to `$HOME/.xebialabs` or make sure your `$HOME/.xebialabs/config.yaml` contains:

```plain
xl-deploy:
  authmethod: http
  password: admin
  url: http://localhost:4516/
  username: admin
xl-release:
  authmethod: http
  password: admin
  url: http://localhost:5516/
  username: admin
```

If you want to run multiple `docker-compose` instances, you need to give them each unique names.

 Use `docker network list` to see what networks you currently have defined.

```plain
 docker network list
 NETWORK ID          NAME                DRIVER              SCOPE
 abcdef012345        bridge              bridge              local
 6789abcdef01        host                host                local
 23456789abcd        none                null                local
 ef0123456789        normal              bridge              local
 abcdef012345        xebialabs_default   bridge              local
```

> Here you can see that the `xebialabs` network is already defined.

To use a different network, either use the `--project-name` option or set the `COMPOSE_PROJECT_NAME` environment variable:

```plain
docker-compose --project-name xebialabs up

# or

export COMPOSE_PROJECT_NAME=xebialabs
docker-compose up
```

> **Note:** If you don't do this, all your containers will run under the `xebialabs` network with `xebialabs` prefix.
>
> If you only intend to run one container set at a time and run `docker-compose down` in between, you don't have to worry about this.