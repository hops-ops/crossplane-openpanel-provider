### What's changed in v0.1.0

* feat: crossplane-openpanel-provider Crossplane provider stack (by @patrickleet)

  OpenPanel provider, ProviderConfig, and ExternalSecret-sourced credentials.
  Split out of the monolithic CrossplaneStack into a per-provider XR.

  Implements [[tasks/crossplane-provider-xr-split]]

  Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

* fix: correct examples block indentation in CI workflows (by @patrickleet)

  The generated on-pr.yaml and on-push-main.yaml indented the JSON
  `{ "example": ... }` lines less than the enclosing `examples: |`
  block scalar, which terminated the scalar early and produced an
  invalid workflow file (startup_failure, 0 jobs). Re-indent the lines
  to sit inside the block scalar.

  Implements [[tasks/crossplane-provider-xr-split]]

  Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

* refactor: rename to OpenPanelProviderStack on crossplane.ops.com.ai group (by @patrickleet)

  Renamed XRD kind to OpenPanelProviderStack, API group to crossplane.ops.com.ai, and the
  repo/package to crossplane-openpanel-provider-stack. No consumers yet; pre-release.

  Implements [[tasks/crossplane-provider-xr-split]]

  Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>


