# CappAckiMiner Downloads

This is the single official public download hub for CappAckiMiner Windows and Android packages.

This distribution repository contains compiled packages and public documentation only. Wallet files, recovery phrases, private keys and application source code are not included.

## Current downloads

| Platform | Edition | Version | Download |
| --- | --- | --- | --- |
| Windows | CappAckiMiner Hunter SmallWindow | `1.3.20-test.33` | [Download Hunter TEST33](https://github.com/CappAckiMiner-Downloads/CappAckiMiner-Releases/releases/download/windows-current-2026-09-21/CappAckiMiner-Hunter-TEST33-WaitFix-SmallWindow-x64-Setup.exe) |
| Windows | CappAckiMiner Burst SmallWindow | `1.0.2` | [Download Burst v1.0.2](https://github.com/CappAckiMiner-Downloads/CappAckiMiner-Releases/releases/download/windows-current-2026-09-21/CappAckiMiner-Burst-v1.0.2-WaitFix-SmallWindow-x64-Setup.exe) |
| Windows | CappAckiMiner PRO | Legacy | [Download PRO](https://github.com/CappAckiMiner-Downloads/CappAckiMiner-Releases/releases/download/windows-current-2026-09-21/CappAckiMiner-PRO.exe) |
| Windows | CappAckiMiner PRO B | Legacy | [Download PRO B](https://github.com/CappAckiMiner-Downloads/CappAckiMiner-Releases/releases/download/windows-current-2026-09-21/CappAckiMiner-PRO_B.exe) |
| Android | Universal APK | `1.3.9` | [Download Android Universal](https://github.com/CappAckiMiner-Downloads/CappAckiMiner-Releases/releases/download/windows-current-2026-09-21/CappAckiMiner-pro-1.3.9-Universal.apk) |
| Windows utility | Legacy Backup Converter setup | `1.0.0` | [Download converter setup](https://github.com/CappAckiMiner-Downloads/CappAckiMiner-Releases/releases/download/windows-current-2026-09-21/CappAckiMiner-Legacy-Backup-Converter-Setup.exe) |
| Windows utility | Legacy Backup Converter portable | `1.0.0` | [Download portable converter](https://github.com/CappAckiMiner-Downloads/CappAckiMiner-Releases/releases/download/windows-current-2026-09-21/CappAckiMiner-Legacy-Backup-Converter.exe) |

[All downloads on one page](https://github.com/CappAckiMiner-Downloads/CappAckiMiner-Releases/releases/tag/windows-current-2026-09-21) · [User guide](HELP.md)

Hunter and Burst are the two maintained Windows editions. They keep separate application identities and local data areas, so they can be installed and opened independently. Never mine the same wallet in both editions at the same time.

The SmallWindow editions open at their normal desktop size and can be resized substantially smaller when needed. PRO and PRO B are retained as legacy Windows applications; Hunter and Burst are the maintained editions.

## Verification

Current Windows SHA-256 values:

```text
9A8CA4E3D64F08FB7AA420D6020C8F2993E68CEAFF4875FE38F14BC1CDEFFBD1  CappAckiMiner-Hunter-TEST33-WaitFix-SmallWindow-x64-Setup.exe
E38AECE87605850259D0A8593784E8145A79DF3E575EB979EAF2804B0A098B96  CappAckiMiner-Burst-v1.0.2-WaitFix-SmallWindow-x64-Setup.exe
7FDAEA90E8AB62785A1DAFD14892D2889BF1A38A330C18001C0BCA532D8ACFE3  CappAckiMiner-PRO.exe
D58242C7DD29002F3941A006780397FA05C9653C410483CB291A848E70E2FA93  CappAckiMiner-PRO_B.exe
5217A1BBD53A47D74904FF5EE2C6D888522DCC5145979B88446C75BF342B3FC9  CappAckiMiner-Legacy-Backup-Converter-Setup.exe
656C8B07796288CA53FE270C55D146C1D06AED1444C68CD86CB8804E5ECD40BF  CappAckiMiner-Legacy-Backup-Converter.exe
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
