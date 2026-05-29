# crossplane-openpanel-provider-stack

Installs hops-ops/provider-openpanel and optionally composes its Secret-backed ProviderConfig.

## Why This XR?

Without a dedicated provider XR, provider lifecycle changes are coupled to
the Crossplane core install. With this XR, the provider package, runtime
resources, and ProviderConfig can be reconciled independently.

## The Journey

### Stage 1: Getting Started

Apply the minimal example in `examples/openpanelproviderstacks/minimal.yaml` after
the target cluster already has Crossplane core installed.

### Stage 2: Growing

Override `spec.runtimeConfig` when the provider controller needs different
requests or limits, and set `spec.nodePool.enabled: true` to land provider
runtimes on the CrossplaneStack NodePool. Use `spec.scheduling` only for
custom node selector or toleration overrides.

### Stage 3: Enterprise Scale

Pin provider package versions with `spec.package.version` and keep provider
credentials in a stack-owned Secret or ExternalSecret.

### Stage 4: Import Existing

Existing target-cluster ProviderConfigs can be left in place by omitting
`spec.secretName` where ProviderConfig rendering is optional.

Set `spec.secretName` to compose a ProviderConfig that reads credentials
from a target-cluster Secret. Omit it when another stack owns the
ProviderConfig lifecycle.

## Status

- `status.provider.ready`: readiness of the composed provider package Object.

## Composed Resources

- `Object` wrapping `DeploymentRuntimeConfig` for provider runtime settings.
- `Object` wrapping the target `Provider` package.

## Development

```sh
make render:all
make validate:all
make test
```

## License

Apache-2.0
