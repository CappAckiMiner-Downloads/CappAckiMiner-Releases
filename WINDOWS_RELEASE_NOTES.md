# CappAckiMiner Windows PRO / PRO B

## Downloads

| Edition | Public file | Build line | Internal version |
| --- | --- | --- | --- |
| PRO | `CappAckiMiner-PRO.exe` | TEST4.3 PRO.12 — visual update, frozen mining line | `1.3.20-test.4.3pro.12` |
| PRO B | `CappAckiMiner-PRO_B.exe` | TEST.23 — active development | `1.3.20-test.23` |
| Backup converter | `CappAckiMiner-Legacy-Backup-Converter-Setup.exe` | Installed utility | `1.0.0` |
| Backup converter | `CappAckiMiner-Legacy-Backup-Converter.exe` | Portable utility | `1.0.0` |

The PRO and PRO B files are Windows installer packages. The converter is available as both an installer and a portable executable. Stable public filenames are retained so existing download links continue to work.

PRO.12 is an explicitly requested visual-only update to the frozen PRO.11 mining line. This release rebuilds both installers with the shared interface improvements below, without changing either edition's mining behavior. Continued development and mining tests remain on PRO B.

## Changes in this update

- Main Mode shares Lite's top two rows instead of using a separate toolbar layout.
- Add Wallet stays visible beside the mining controls at desktop widths from 1280 to 1920 pixels; the compact log control also remains available.
- The three recent-reward timestamps in Main cards are enlarged to a readable 8–9 px. Full reward amounts retain priority, including in narrow cards.
- Mining behavior, counters, reward accounting, start controls and timing are unchanged by these presentation changes.

## Existing features retained

- Blue and green accept indicators use a 12% wallet-card background tint with their existing epoch reset behavior.
- Manual-stop status, daily-epoch monitor reporting and reduced decorative animation in dense wallet views remain available.
- PRO and PRO B retain separate application identities, executable names, installation directories and local data areas. They can be installed and launched independently.
- A compatible legacy profile can be migrated once on first run; the editions then maintain independent local data.
- Existing verified-epoch handoff prevents inactive older-session ownership from unnecessarily blocking the next epoch start.
- A real late SDK result stays associated with its older session and cannot take control of a newer mining session.
- Current-session and late-session accept indicators stay isolated and reset on the verified epoch boundary.
- Existing wallet backup, Main/Lite views, network health, daily/epoch accounting and fixed production timing remain available.

> Do not mine the same wallet in PRO and PRO B at the same time. Side-by-side installation is intended for controlled comparison, not duplicate wallet operation.

This is a visual update, not a new mining optimization. It makes no claim of improved acceptance or rewards and does not guarantee an acceptance rate, reward amount or uninterrupted network availability.

## Legacy backup converter

The release also includes a small Windows utility for owners of older self-contained wallet-backup EXE files. It converts the encrypted backup payload into the `.cappacki` format accepted by PRO and PRO B.

The legacy EXE is never executed. The utility opens it only as a data file, validates the CappAckiMiner backup marker, payload length and encrypted envelope, then writes and verifies a new `.cappacki` file. It does not ask for the backup password or decrypt wallet data. Import the result through **Wallet Backup > Import Wallet Backup** and enter the original backup password in CappAckiMiner.

## Installation and security

- Back up wallets before installing or upgrading.
- The installers do not currently carry an Authenticode signature, so Windows SmartScreen may show a warning.
- Download only from this official release and verify SHA-256 before running.
- Application source code, wallet files and private mining implementation details are not included in this public repository.
- Full English installation, usage, status and troubleshooting guidance is available in [HELP.md](https://github.com/cappackiminer/CappAckiMiner-PRO/blob/main/HELP.md).

## SHA-256

```text
AB0194A1D5F939E7D44D814FBAE78F4DDF0B26386A553259F3BB204630184DBA  CappAckiMiner-PRO.exe
D819B423C0E5D28A33D141F7AA32F97C5EC4695BD50E746DC7F30F45D00FDCBD  CappAckiMiner-PRO_B.exe
5217A1BBD53A47D74904FF5EE2C6D888522DCC5145979B88446C75BF342B3FC9  CappAckiMiner-Legacy-Backup-Converter-Setup.exe
656C8B07796288CA53FE270C55D146C1D06AED1444C68CD86CB8804E5ECD40BF  CappAckiMiner-Legacy-Backup-Converter.exe
```

[Android PRO downloads](https://github.com/cappackiminer/CappAckiMiner-PRO/releases/tag/android-pro-2026-09-17)

GitHub's automatic Source code ZIP/TAR downloads contain only this distribution repository's documentation, not the application source code.
