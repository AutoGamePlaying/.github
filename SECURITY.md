# Security policy

## Reporting a vulnerability

**Do not open a public issue** for security problems, such as a leaked secret, an authentication bypass in the local web panel, or a way to tamper with logs or results without detection. Use GitHub's private vulnerability reporting instead: in the repository, go to Security, then Report a vulnerability.

Please include:
- the affected repository and version (commit);
- steps to reproduce;
- the possible impact.

## Security conventions in the design

- Secrets live only in user-level configuration or environment variables. Configuration files only name the source, and logs, the UI and results always redact secret values.
- The local web panel listens on localhost only. It requires an access token and a session cookie, and checks `Origin` on every non-GET request.
- Run logs and the provider-config journal are hash chains. Results and scoreboards are Ed25519-signed and can be checked with `agp results verify`.
- In-game mods only read game state. Simulated input is off by default and must be enabled explicitly.
