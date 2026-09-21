# CappAckiMiner Downloads

This is the single official public download hub for CappAckiMiner Windows and Android packages.

This distribution repository contains compiled packages and public documentation only. Wallet files, recovery phrases, private keys and application source code are not included.

## Current downloads

| Platform | Edition | Version | Download |
| --- | --- | --- | --- |
| Windows | CappAckiMiner Hunter SmallWindow | `1.3.20-test.33` | [Download Hunter TEST33](https://github.com/CappAckiMiner-Downloads/CappAckiMiner-Releases/releases/download/windows-current-2026-09-21/CappAckiMiner-Hunter-TEST33-WaitFix-SmallWindow-x64-Setup.exe) |
| Windows | CappAckiMiner Burst SmallWindow | `1.0.2` | [Download Burst v1.0.2](https://github.com/CappAckiMiner-Downloads/CappAckiMiner-Releases/releases/download/windows-current-2026-09-21/CappAckiMiner-Burst-v1.0.2-WaitFix-SmallWindow-x64-Setup.exe) |
| Android | Universal APK | `1.3.9` | [Download Android Universal](https://github.com/CappAckiMiner-Downloads/CappAckiMiner-Releases/releases/download/android-pro-2026-09-17/CappAckiMiner-pro-1.3.9-Universal.apk) |

[Current Windows release notes](https://github.com/CappAckiMiner-Downloads/CappAckiMiner-Releases/releases/tag/windows-current-2026-09-21) · [Android release notes](https://github.com/CappAckiMiner-Downloads/CappAckiMiner-Releases/releases/tag/android-pro-2026-09-17) · [All releases](https://github.com/CappAckiMiner-Downloads/CappAckiMiner-Releases/releases) · [User guide](HELP.md)

Hunter and Burst are the two maintained Windows editions. They keep separate application identities and local data areas, so they can be installed and opened independently. Never mine the same wallet in both editions at the same time.

The SmallWindow editions open at their normal desktop size and can be resized substantially smaller when needed.

## Windows tools and archive

The [Windows tools and legacy archive](https://github.com/CappAckiMiner-Downloads/CappAckiMiner-Releases/releases/tag/windows-pro-ab-2026-09-17) contains:

- CappAcki Wallet Monitor;
- the Legacy Backup Converter setup and portable executable;
- retired CappAckiMiner Windows builds retained for users who need an older package;
- the original legacy release assets migrated from the former download repository.

Archived miner builds are provided for recovery and reference. Use the current Hunter or Burst edition for new testing.

## Legacy backup converter

Older CappAckiMiner wallet backups may be self-contained `.exe` files. Current editions import encrypted `.cappacki` backups. The Legacy Backup Converter reads the old EXE strictly as data, validates its embedded encrypted backup envelope and copies that encrypted payload into the current format. It does not execute the old EXE, request the wallet password or decrypt wallet material.

Keep both the original and converted backup private. Never attach either file to a GitHub issue, chat or public cloud link.

## Verification

Current Windows SHA-256 values:

```text
9A8CA4E3D64F08FB7AA420D6020C8F2993E68CEAFF4875FE38F14BC1CDEFFBD1  CappAckiMiner-Hunter-TEST33-WaitFix-SmallWindow-x64-Setup.exe
E38AECE87605850259D0A8593784E8145A79DF3E575EB979EAF2804B0A098B96  CappAckiMiner-Burst-v1.0.2-WaitFix-SmallWindow-x64-Setup.exe
```

Android Universal SHA-256:

```text
48A951009E27E064BC72F12B3CF2E3F9C765FD3B1CDF69DBB5DF36437B551C7A  CappAckiMiner-pro-1.3.9-Universal.apk
```

PowerShell example:

```powershell
Get-FileHash .\CappAckiMiner-Hunter-TEST33-WaitFix-SmallWindow-x64-Setup.exe -Algorithm SHA256
```

The reported value must match the value published here exactly. Do not run a file whose hash differs.

## Installation and safety

- Create and verify a current wallet backup before installing or upgrading.
- Download packages only from this repository's Releases page.
- The Windows installers do not currently carry an Authenticode signature, so Windows SmartScreen may show a warning.
- Never share a recovery phrase, private key, wallet-backup file, access token or unredacted diagnostic log.
- Acceptance and rewards depend on the network, wallet authorization and SDK responses; they cannot be guaranteed.

GitHub's automatic source-code ZIP/TAR downloads contain only this distribution repository's documentation and artwork, not the application source code.
