# MCAI-OS Apps

The official app catalogue and app-package repository for [MCAI-OS](https://github.com/betabeeswax/MCAI-OS), the M5Stack Cardputer ADV and companion desktop environment.

## What's here

- `catalogue.json` — the shared 109-entry roadmap copied from the main MCAI-OS repository.
- `schema/app-manifest.schema.json` — JSON Schema for app metadata.
- `docs/APP_FORMAT.md` — package layout, targets, permissions and publishing rules.
- `apps/tap-counter/app.json` — Tap Counter.
- `apps/score-counter/app.json` — Score Counter.
- `apps/rep-counter/app.json` — Rep Counter.

## Important status note

The catalogue is a roadmap, not a claim that every app is available. Entries remain `planned` until working app code, target support and tests are published. This repository now includes three installable `mcai-app-v1` Cardputer packages: Tap Counter, Score Counter and Rep Counter. The Cardputer firmware downloads it over HTTPS, verifies SHA-256, stores it on microSD and runs it through a restricted declarative runtime. The catalogue currently includes 14 native Cardputer apps marked built-in, three installable counter packages, and the remaining roadmap entries. Snake is already included as a built-in game. The Notes app supports separate editable text files on microSD. Status labels are intentionally conservative: a planned app is not presented as installable.

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
