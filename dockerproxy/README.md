# dockerproxy Home Assistant add-on

dockerproxy is a lightweight multi-host Docker registry cache/proxy.

Lets be honest here, the odds of this as an addon (or app) to HA, is usefull to anyone, is slim to none!  I needed a stable host that was not part of my cluster to manage my cache, and homeassistant had the capacity.

This add-on runs the published dockerproxy image:

```text
ghcr.io/dthompso99/dockerproxy:main
```

It does not vendor the Rust source and does not rebuild the image. Home Assistant passes the add-on options to the container at `/data/options.json`, and dockerproxy stores its cache under `/data/cache`.

## Access

- Proxy and API port: `8080`
- Web UI: `http://<home-assistant-host>:8080/ui`
- Health endpoint: `http://<home-assistant-host>:8080/health`

## Default options

```yaml
hosts:
  - name: dockerhub
    url: https://registry-1.docker.io
ttl: 31557600
log_level: 1
ssl: false
```

Each host may also include `username` and `token` when the upstream registry requires authentication. The `token` field is marked as a password field in the Home Assistant add-on schema.

Set `ssl: true` if Home Assistant should open the add-on web UI with `https` instead of `http`.

See [DOCS.md](DOCS.md) for configuration details.
