# CappAckiMiner Windows PRO / PRO B

## Downloads

| Edition | Public file | Build line | Internal version |
| --- | --- | --- | --- |
| PRO | `CappAckiMiner-PRO.exe` | TEST4.3 PRO.11 — frozen | `1.3.20-test.4.3pro.11` |
| PRO B | `CappAckiMiner-PRO_B.exe` | TEST.22 — active development | `1.3.20-test.22` |
| Backup converter | `CappAckiMiner-Legacy-Backup-Converter-Setup.exe` | Installed utility | `1.0.0` |
| Backup converter | `CappAckiMiner-Legacy-Backup-Converter.exe` | Portable utility | `1.0.0` |

The PRO and PRO B files are Windows installer packages. The converter is available as both an installer and a portable executable. Stable public filenames are retained so existing download links continue to work.

PRO is now frozen at PRO.11. Further development and testing will continue on PRO B. This publication uses the existing installer packages without rebuilding or modifying them.

## Changes in this update

- Main Mode distributes the monitor and income panels across the available toolbar space.
- Main wallet cards give reward amounts more room and use smaller timestamps for the three recent rewards.
- Blue and green accept indicators use a more visible 12% wallet-card background tint while retaining their existing epoch reset behavior.
- Manual-stop status is clearer, daily-epoch monitor reporting is more consistent, and dense wallet views reduce decorative animation.
- PRO and PRO B now use separate application identities, executable names, installation directories and local data areas. They can be installed and launched independently.
- A compatible legacy profile can be migrated once on first run; the editions then maintain independent local data.
- Verified epoch handoff no longer allows an inactive older session owner to unnecessarily block the next epoch start.
- A real late SDK result stays associated with its older session and cannot take control of a newer mining session.
- Current-session and late-session accept indicators stay isolated and reset on the verified epoch boundary.
- Existing wallet backup, Main/Lite views, network health, daily/epoch accounting and fixed production timing remain available.

> Do not mine the same wallet in PRO and PRO B at the same time. Side-by-side installation is intended for controlled comparison, not duplicate wallet operation.

This update improves lifecycle stability; it does not guarantee an acceptance rate, reward amount or uninterrupted network availability.

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
DE47B23A2AE2C4E3BA1748103BB57AF54A4948C239345D5CC85752EEDA8AB663  CappAckiMiner-PRO.exe
0B600EA70829B9BC31DF8F16F749FC754260E821971E437412EE282167A8E1B2  CappAckiMiner-PRO_B.exe
5217A1BBD53A47D74904FF5EE2C6D888522DCC5145979B88446C75BF342B3FC9  CappAckiMiner-Legacy-Backup-Converter-Setup.exe
656C8B07796288CA53FE270C55D146C1D06AED1444C68CD86CB8804E5ECD40BF  CappAckiMiner-Legacy-Backup-Converter.exe
```

[Android PRO downloads](https://github.com/cappackiminer/CappAckiMiner-PRO/releases/tag/android-pro-2026-09-17)

GitHub's automatic Source code ZIP/TAR downloads contain only this distribution repository's documentation, not the application source code.
