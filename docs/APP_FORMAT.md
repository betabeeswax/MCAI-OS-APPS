# MCAI-OS App Package Format (draft 1)

This document defines the first metadata/package contract for MCAI-OS apps. It is a draft: the firmware and desktop app runtimes do not yet load third-party packages.

## Package layout

A published app should use this layout:

```
my-app/
  manifest.json
  README.md
  icon.png
  cardputer/       # optional Cardputer ADV implementation
  desktop/         # optional desktop implementation
  assets/          # optional data, images and sounds
  tests/           # optional automated tests
```

Keep each app in its own folder or release asset. Do not put credentials, API keys, private user data or device secrets in an app package.

## Manifest

Every app must include `manifest.json`. Validate it against [the JSON Schema](../schema/app-manifest.schema.json).

Required fields:
- `schemaVersion`: manifest schema version (currently `1`).
- `id`: stable lowercase ID using letters, numbers and hyphens.
- `name`: display name.
- `version`: semantic version.
- `description`: short explanation.
- `publisher`: maintainer or organization.
- `targets`: one or more supported targets.
- `status`: `planned`, `experimental`, `available` or `deprecated`.

Optional `permissions` are capabilities requested by the app. The OS must ask the user before granting sensitive capabilities. A manifest declaration is a request, not automatic permission.

## Target identifiers

- `cardputer-adv`
- `desktop`

Only list a target when the package actually contains a working implementation for it.

## Permissions

Use the smallest possible set:
- `storage.read`
- `storage.write`
- `network`
- `bluetooth`
- `audio.input`
- `audio.output`
- `camera`
- `microphone`
- `ir`
- `notifications`

Unsupported permissions must be rejected by the runtime, not silently granted.

## Packaging and installation

The planned distribution format is a ZIP archive containing the app folder. A future App Store/client will read the manifest, verify package integrity, check target compatibility and request permissions before installation.

Until package signature verification and a sandboxed runtime exist, only install apps from sources you trust. Do not treat a ZIP or manifest as safe merely because it appears in this repository.

## Compatibility and status

- `planned`: roadmap entry only; no installable app.
- `experimental`: code exists but is incomplete or not fully tested.
- `available`: working implementation exists for the listed target(s), with build/test instructions.
- `deprecated`: no longer recommended.

A successful desktop build does not prove Cardputer hardware compatibility. Hardware claims must include the exact board revision and a physical test procedure.
