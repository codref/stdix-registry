# stdix-registry

Standards registry for [stdix](https://github.com/codref/stdix).

## Structure

```
standards/
  <language>/
    <topic>.yaml
  shared/
    <topic>.yaml
```

Each YAML file is a single standard. See the [stdix README](https://github.com/codref/stdix#registry-authoring) for the full schema.

## CI

- **PR**: validates all standards with `stdix-build validate`
- **Push to main**: builds `registry.db` and publishes it as the rolling `latest` release

## Adding a standard

Use the [/new-standard](https://github.com/codref/stdix/blob/main/.github/prompts/new-standard.prompt.md) Copilot prompt in the stdix repo, or manually:

```sh
export STDIX_REGISTRY_TOKEN=<your-github-token>
stdix push /tmp/my.standard.yaml --repo codref/stdix-registry
```

## Consuming

```sh
stdix init --registry-url https://github.com/codref/stdix-registry/releases/latest/download/registry.db
stdix sync
stdix match "my task"
```
