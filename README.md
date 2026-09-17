# CappAckiMiner PRO

Official binary downloads for **CappAckiMiner PRO on Windows and Android**.

> Application source code and private mining implementation details are not published in this distribution repository.

## Downloads

| Platform | Edition | Version | Download |
| --- | --- | --- | --- |
| Windows | PRO | `1.3.20-test.4.3pro.9` | [Download CappAckiMiner-PRO.exe](https://github.com/cappackiminer/CappAckiMiner-PRO/releases/download/windows-pro-ab-2026-09-17/CappAckiMiner-PRO.exe) |
| Windows | PRO B | `1.3.20-test.20` | [Download CappAckiMiner-PRO_B.exe](https://github.com/cappackiminer/CappAckiMiner-PRO/releases/download/windows-pro-ab-2026-09-17/CappAckiMiner-PRO_B.exe) |
| Android | Universal 1.3.5 | ARM64 and ARMv7 | [Download Universal APK](https://github.com/cappackiminer/CappAckiMiner-PRO/releases/download/android-pro-2026-09-17/CappAckiMiner-pro-1.3.5-Universal.apk) |
| Android | ARM64 1.3.4 | ARM64 only | [Download ARM64 APK](https://github.com/cappackiminer/CappAckiMiner-PRO/releases/download/android-pro-2026-09-17/CappAckiMiner-pro-ARM64.apk) |

[Windows release notes](https://github.com/cappackiminer/CappAckiMiner-PRO/releases/tag/windows-pro-ab-2026-09-17) · [Android release notes](https://github.com/cappackiminer/CappAckiMiner-PRO/releases/tag/android-pro-2026-09-17) · [All releases](https://github.com/cappackiminer/CappAckiMiner-PRO/releases) · [Complete help guide](HELP.md)

## Windows editions

**PRO** is the TEST4.3 PRO-derived Single Engine line. **PRO B** is the newer Single Engine comparison line. Both builds include the current verified-epoch handoff and late-result isolation work.

The two editions now use separate application identities, executable names, installation directories and local data areas, so they can be installed and opened independently. A compatible legacy profile may be copied once on first run and then each edition keeps its own data.

Do **not** start mining the same wallet in both editions at the same time. Side-by-side installation is intended for controlled comparison, not duplicate operation of one wallet.

Both Windows downloads are installer packages published under stable filenames so existing links continue to work. They do not currently carry an Authenticode digital signature; Windows may therefore show a SmartScreen warning.

## What changed in this Windows update

- PRO and PRO B can be installed and launched independently.
- A confirmed new mining epoch can retire obsolete local ownership left by an older completed session, preventing it from unnecessarily blocking the next start.
- A real late SDK result remains attributable to the older session without taking control of the newer session.
- Current-session and late-session accept indicators are kept separate and reset at the verified epoch boundary.
- Existing wallet backup, daily/epoch counters, network-health display, Main/Lite views and fixed production timing remain available.

This release improves lifecycle stability. It does not guarantee an acceptance rate, reward amount or uninterrupted network availability.

## Windows verification

```text
BFBB03A27100243604FA84D075E8453F0B86513275EE8EF4282A6FC9B4A3A4C1  CappAckiMiner-PRO.exe
6824257881D08B8E8ACFC49139C5E3CCCCB9A185DC05F4620524C5AF104D058C  CappAckiMiner-PRO_B.exe
```

PowerShell example:

```powershell
Get-FileHash .\CappAckiMiner-PRO.exe -Algorithm SHA256
Get-FileHash .\CappAckiMiner-PRO_B.exe -Algorithm SHA256
```

## Android packages

The Universal APK is version **1.3.5** and supports ARM64 and ARMv7. The ARM64-only APK is the earlier version **1.3.4**. Both use the same Android application ID. Minimum Android API level: **24**.

Avoid unnecessary downgrades or uninstalling an existing installation without first creating and safely checking a wallet backup.

## Safety and privacy

- Keep wallet backups, recovery material and private keys offline and private.
- Never publish a wallet-backup file, private key or unredacted diagnostic log in a GitHub issue or chat.
- Verify the SHA-256 hash after downloading.
- Mining acceptance and rewards depend on the network, wallet authorization, SDK responses and current network conditions; they cannot be guaranteed.

For installation, first-run, status explanations, backup guidance and troubleshooting, see the [complete help guide](HELP.md).

GitHub's automatic “Source code” ZIP/TAR files contain only this distribution repository's documentation, not the application's source code.
