# MCAI-OS App Package Format

This document defines the first installable Cardputer package format: **mcai-app-v1**.

## Package structure

Each app is a standalone UTF-8 JSON file published at a stable HTTPS URL. The catalogue entry supplies the URL, exact byte length and SHA-256 digest. The Cardputer downloads the file, checks the digest, validates the package identity and target, then saves it to the microSD card.

Example:

```json
{
  "format": "mcai-app-v1",
  "id": "tap-counter",
  "name": "Tap Counter",
  "version": "1.0.0",
  "target": "cardputer-adv",
  "ui": {
    "title": "Tap Counter",
    "subtitle": "Press ENTER to count",
    "initial": 0,
    "increment": 1
  }
}
```

## Supported runtime API (v1)

The first Cardputer runtime is intentionally declarative: packages contain data, not native machine code or scripts. The current API supports:
- A title and short instruction line.
- An integer value with a bounded initial value.
- A bounded increment action triggered by Enter.
- Backspace to return to the App Store.

The runtime validates the format, app ID, target, required fields and numeric limits. Unknown formats and targets are rejected. Apps cannot directly access hardware, files, network, memory or other apps.

## Catalogue entry

An installable entry must use `status: "available"` and include:

- `package.format`: `mcai-app-v1`
- `package.url`: HTTPS URL to the raw JSON package
- `package.sha256`: lowercase SHA-256 of the exact package bytes
- `package.sizeBytes`: exact package size

Do not set an app to `available` until its package exists, its hash matches and its supported target has passed tests. Planned entries must not show an Install action.

## Install and launch

1. Fetch the catalogue over HTTPS.
2. Require a supported package format, HTTPS URL and 64-character SHA-256.
3. Download with a strict size limit.
4. Verify SHA-256 before parsing or writing.
5. Validate package ID and target against the selected catalogue entry.
6. Save to `/sdcard/MCAI-OS/apps/<id>.json`.
7. Parse and validate again when launching.

The current Cardputer runtime stores packages on microSD and only executes the built-in declarative operations listed above. It does not run downloaded native binaries.

## Security and compatibility

- HTTPS certificate validation is required.
- A checksum detects corruption or an unexpected file; it is not a publisher signature.
- Only publish packages from the official MCAI-OS-APPS repository.
- Never include credentials, API keys or private user data.
- Hardware-specific functionality requires physical testing on the named Cardputer ADV revision.
