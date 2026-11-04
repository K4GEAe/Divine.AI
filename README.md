# Divine — GitHub public distribution package

Version: 0.2.2-alpha.2 (Windows x64)

**UNSIGNED LOCAL TEST BUILD — NOT READY FOR PUBLIC RELEASE OR AUTOMATIC UPDATES.**

This ZIP contains redistributable documentation and one locally built unsigned Windows installer.
It deliberately contains no application source, Git history, private config, token, signing key, or update metadata.
No GitHub release has been published by the bundling script.

## Upload to a PUBLIC GitHub repository

1. Create a public repository for distribution documentation.
2. Copy the contents of repository/ and SHA256SUMS.txt to the root of the new public GitHub repository.
3. Keep its CREDITS.md alongside LICENSE and THIRD_PARTY_NOTICES.md.
4. Keep the release-assets folder outside the Git repository. It contains a large binary that exceeds GitHub regular-file limits.
5. Upload release-assets/divine-harness-0.2.2-alpha.2-win-x64-unsigned.exe as a GitHub Release asset **only for an explicitly labelled unsigned test/prerelease**.
6. Verify the SHA-256 in SHA256SUMS.txt before distributing any file.

## Install and update status

This file is unsigned and intended only for isolated manual testing. Windows SmartScreen may warn about it.
A private repository can be used for development; a public repository with public GitHub Releases can serve anonymous update downloads after a signed release is prepared.
No latest.yml, blockmap, or update feed is included. Do not point a production auto-updater at this test build.

## Path to a signed release

1. Build the intended version using the project Windows release signing workflow.
2. Verify every signed release asset, its publisher certificate identity, Authenticode signature, and timestamp.
3. Generate the matching electron-updater latest.yml and blockmap through the actual signed packaging process.
4. Publish the signed installer and generated update artifacts together on a public GitHub Release matching its version.
5. Configure GitHub Releases as the application update provider, enable updater checks only for the signed channel, and verify an actual installed update on Windows.
6. Keep signing credentials and any GitHub tokens in protected build or release configuration, never in a public repository or bundled ZIP.

## Credits and licenses

repository/LICENSE is the original upstream MIT license with its copyright retained. repository/THIRD_PARTY_NOTICES.md documents project dependencies.
Some references in the notices describe the upstream source tree, which is not included in this binary-only distribution package.
CREDITS.md contains the credits bundled with the Desktop application.
