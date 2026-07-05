# dockerproxy add-on documentation

## Configuration

dockerproxy reads the Home Assistant add-on options directly from:

```text
/data/options.json
```

The container image defaults to:

```text
--config-file /data/options.json --cache-dir /data/cache
```

Cache data is stored in `/data/cache`, which is persistent add-on storage.

The upstream dockerproxy image runs as UID/GID `65532:65532`. Home Assistant supplies `/data` as an add-on runtime mount, so this repository builds a minimal wrapper image from `ghcr.io/dthompso99/dockerproxy:main` and switches the runtime user to UID/GID `0:0`. No dockerproxy source is vendored or rebuilt.

The published dockerproxy image currently advertises `linux/amd64`, so this add-on is marked for `amd64`.

## Options

### `hosts`

List of upstream registries to proxy.

```yaml
hosts:
  - name: dockerhub
    url: https://registry-1.docker.io
```

Optional authenticated host:

```yaml
hosts:
  - name: private
    url: https://registry.example.com
    username: my-user
    token: my-token
```

### `ttl`

Cache time-to-live in seconds. The default is `31557600`, approximately one year.

### `log_level`

dockerproxy log level. The default is `1`.

## Endpoints

- Web UI: `/ui`
- Health check: `/health`

The add-on exposes container port `8080` on host port `8080` by default.
