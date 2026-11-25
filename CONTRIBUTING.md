# Contributing

This is the default contributing guide for AutoGamePlaying repositories. If a repository has its own `CONTRIBUTING.md`, that one takes precedence.

## Ground rules

- **Do not commit game files, extracted game data or walkthrough text**, nor tables copied from them. Test data must be self-made.
- **Do not commit secrets, tokens, LAN addresses, account names, machine names or absolute local paths.** Configuration only names where a secret comes from (an environment variable or a file path).
- **Tests must not call real model APIs or connect to a game machine.** Use local fake servers (for example wiremock), fake game modules and temporary directories.
- **Use Conventional Commits**, for example `feat(llm): …`, `fix(runner): …`, `docs: …`.

## Checks

Run the repository's checks before committing; everything must pass:

| Repository | Checks |
| --- | --- |
| `agp` | `scripts/check.sh` (`cargo fmt --check`, `cargo clippy -D warnings`, `cargo test`); changes touching Windows code also need `scripts/build-windows.sh` |
| `Final-Fantasy-Pixel-Remaster` | `npm run check` |
| `Final-Fantasy-Resonance-Agent` | `npm run check` and `scripts/check-rust.sh` |

## Code style

- Error messages are for people: say which step failed and why.
- Do not swallow errors and do not guess. Report data that cannot be read; never substitute defaults for it.
- Code comments are in English. User-facing messages and model-facing tool descriptions are currently written in Chinese.

## Design changes

Before changing the architecture, a protocol, the log or result format, or competition rules, open an issue that explains the motivation and impact, and agree on it before writing code.
