# MCAI-OS Apps

The official app catalogue and app-package repository for [MCAI-OS](https://github.com/betabeeswax/MCAI-OS), the M5Stack Cardputer ADV and companion desktop environment.

## What's here

- `catalogue.json` — the shared 108-entry roadmap copied from the main MCAI-OS repository.
- `schema/app-manifest.schema.json` — JSON Schema for app metadata.
- `docs/APP_FORMAT.md` — package layout, targets, permissions and publishing rules.
- `apps/tap-counter/app.json` — the first installable Cardputer ADV app package.

## Important status note

The catalogue is a roadmap, not a claim that every app is available. Entries remain `planned` until working app code, target support and tests are published. This repository now includes the first installable `mcai-app-v1` Cardputer package (Tap Counter). The Cardputer firmware downloads it over HTTPS, verifies SHA-256, stores it on microSD and runs it through a restricted declarative runtime. The catalogue currently marks 12 native Cardputer apps as built-in, Tap Counter as experimental/installable, and the remaining roadmap entries as planned. The Notes app supports separate editable text files on microSD. Status labels are intentionally conservative: a planned app is not presented as installable.

## Targets

- `cardputer-adv` — native app for the M5Stack Cardputer ADV.
- `desktop` — companion desktop environment.
- `both` — package supports both targets.

## Contributing

Read [the app format](docs/APP_FORMAT.md) before submitting an app. Do not claim hardware support without testing on the named Cardputer ADV hardware. Apps must request only the permissions they actually need.

## Related project

- [MCAI-OS firmware and system](https://github.com/betabeeswax/MCAI-OS)
- [Easy Flasher](https://betabeeswax.github.io/MCAI-OS/)
- [Firmware releases](https://github.com/betabeeswax/MCAI-OS/releases)
