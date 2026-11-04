# Divine security information

Divine is a local AI coding agent that can read and change files, execute commands, install plugins and interact with applications or network services. Treat untrusted files, model content and third-party plugin code as potentially unsafe.

## Existing controls

The main Electron renderer disables Node integration and enables context isolation and sandboxing. Browser guest views have separate restrictions, and the local Web API performs authentication and request-host checks. Default tool permissions limit filesystem writes to the workspace and ask before broader operations. Native Computer Use checks application access through an approval flow. Signed updater configurations pin the source and publisher.

## Known limits

Installed third-party plugins run inside the Host Node process and can have access beyond a tool's workspace sandbox. The managed Windows credential document uses user-scoped DPAPI, while macOS and Linux retain owner-only YAML. Processes running under the same Windows user can still request DPAPI decryption, and project or environment-provided secrets are outside the managed file. Session storage is not encrypted at rest, and recoverable recycle and backup do not erase sensitive data. Local original crash diagnostics can contain raw private information; the separate support export is sanitized before optional sharing. Exposing the Web server beyond loopback requires appropriate TLS or a trusted HTTPS reverse proxy and careful network configuration. An unsigned test installer is not a signed production release. Signing keys and signing runners need operational access isolation before processing untrusted contributions.

## Vulnerability reports

The independent distributor has not yet supplied a verified private vulnerability reporting address or staffed security response channel. Check the current trusted distribution repository for its official private reporting instructions. Avoid posting sensitive reproduction details, secrets or personal information in public issues; if only a public channel exists, first request a private route using a nonsensitive summary. No response deadline, certification or complete external audit is claimed.

Read [PRIVACY.md](PRIVACY.md) and [SUPPORT.md](SUPPORT.md) for related limitations.
