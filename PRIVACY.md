# Divine privacy information

This describes the current DivineHarness source snapshot, not a future hosted service. Divine is independently branded from DeepSeek Harness and is not affiliated with DeepSeek AI. The distributor has not provided a verified dedicated privacy contact or website policy URL. This description is not a substitute for legal review before public distribution.

## Local data

Session files can contain user prompts, model responses, excerpts from files, file paths, tool arguments, terminal output, and conversation history. They are stored locally under the configured harness and workspace locations. The Session persistence backend provides backup and recoverable recycle operations: a recycled Session is moved out of the active listing, with its backup retained separately. Neither operation permanently erases data, and no automatic retention or permanent deletion schedule is established. Session files are not an encrypted vault.

On Windows, the managed local credential document uses user-scoped DPAPI encryption and migrates legacy plaintext documents after validation. This protects the managed file against casual plaintext access by a different OS user; an agent or other process running as the same Windows account may still request decryption. On macOS and Linux, the file-backed provider uses owner-only YAML without OS keychain encryption. Project, harness-home, and launch-environment credential fallbacks remain outside that managed encryption, and existing backups or file-system snapshots may retain older plaintext. Do not assume every application file is encrypted at rest.

Local original crash reports may include unredacted error messages, plugin stderr, and recent renderer console output. They are not automatically uploaded. The Desktop recovery UI offers a preview of a separately generated sanitized support copy. Only explicitly exporting that copy creates a file to share; it intentionally excludes raw errors, stacks, credentials, Session IDs, paths, URLs, plugin stderr, renderer console, and operation history. The original local diagnostic remains private. Other logs and manual attachments may still contain sensitive information.

## Necessary and optional external requests

When you choose an AI model provider, model requests may send prompts, conversation context, tool results, or attachment content to that provider. Optional plugins, web tools and integrations may communicate with other services. Each provider's terms and privacy practices apply independently.

Desktop usage analytics are OFF by default. The distributor must explicitly set DIVINE_PRODUCT_TELEMETRY_ENDPOINT to its own trusted HTTPS collector (or a loopback endpoint for local tests). Without a configured destination, the exporter is inactive. When a destination exists, users can opt in or turn collection off in Settings → General. The Web-only interface does not submit Desktop analytics.

If enabled, event types, timestamps, approved categorical and numeric action attributes, application version, and detailed OS/hardware information such as OS build, CPU model and RAM total may be sent. The Divine analytics Host only forwards declared event fields, excluding account/device IDs, session/message IDs, file inputs, free-form text, model names and plugin names. The collector is still able to observe network-level metadata, such as the connecting IP address. Disabling the setting stops new event intake, but queued events might complete on shutdown.

The separate feedback-triggered Session telemetry is also OFF without explicit consent. Feedback alone never authorizes uploading history. An administrator must configure DIVINE_SESSION_TELEMETRY_ENDPOINT and the FEEDBACK_ONLY collection mode, then the user must explicitly enable the conversation-sharing setting in Settings → General. A subsequent feedback action may export the existing Session event history prefix, which can include conversation and tool context even after field-level redaction. Do not enable this for sensitive projects without reviewing the destination and distributor's notice.

The default Divine base configuration also disables the DeepSeek-specific Session-log contribution included in official model API requests. A custom profile or third-party plugin can change behavior; users should review additional settings and code before enabling them.

## Limits and control

There is no universal retention period, encrypted Session vault, automated cloud deletion, or verified data-subject request channel implemented here. The optional analytics controls do not stop data sent to model providers or tools you deliberately invoke. For guidance, see [SECURITY.md](SECURITY.md) and [SUPPORT.md](SUPPORT.md).
