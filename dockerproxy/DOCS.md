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

### `ssl`

Controls the protocol used by Home Assistant's Open Web UI button. Set this to `true` if the add-on is exposed through HTTPS on the same host and port mapping Home Assistant knows about.

Home Assistant add-on metadata does not support a configurable hostname override for the Open Web UI button. If you expose dockerproxy through a separate hostname, such as `https://docker.example.com/`, bookmark that URL or maintain a local fork that sets `webui` to that fixed external URL.

## Endpoints

- Web UI: `/ui`
- Health check: `/health`

The add-on exposes container port `8080` on host port `8080` by default.
