# CappAckiMiner Windows PRO / PRO B

## Downloads

| Edition | Public file | Build line | Internal version |
| --- | --- | --- | --- |
| PRO | `CappAckiMiner-PRO.exe` | TEST4.3 PRO.13 — limited retry-settings update | `1.3.20-test.4.3pro.13` |
| PRO B | `CappAckiMiner-PRO_B.exe` | TEST.28 — active development | `1.3.20-test.28` |
| Backup converter | `CappAckiMiner-Legacy-Backup-Converter-Setup.exe` | Installed utility | `1.0.0` |
| Backup converter | `CappAckiMiner-Legacy-Backup-Converter.exe` | Portable utility | `1.0.0` |

The PRO and PRO B files are Windows installer packages. Stable public filenames are retained so existing download links continue to work. The backup converters and Android downloads are unchanged by this update.

## Retry-setting update in both editions

- ROOT RETRY INTERVAL now offers **4, 5, 10, 20 and 30 seconds**.
- The default selection is **20 seconds**. An older saved value below 4 seconds is migrated to the new default; supported existing values are retained.
- The selection remains a base interval. Existing randomized waits are preserved: the 4-second selection gives a 2–6-second range and the 20-second default gives a 10–30-second range. The menu minimum therefore does not mean a four-second minimum actual wait.
- Mining tap timing remains fixed at **1.72 seconds**. Wallet start spacing and Start All delay remain separate from retry settings.
- This update does not add escalating retry behavior for overflow responses.

PRO.13 is a specifically requested retry-configuration exception to the otherwise frozen PRO.12 line. It does not incorporate PRO B's other development changes or resume general development of PRO. Continued development remains on PRO B.

## PRO B updates included

- Includes B's newer session/result status safeguards and genuine SDK reject feedback. Red result frames and background tint reset at the verified short-epoch boundary; the latest genuine result determines the visible result color.
- Submission observations in Log help explain the application's own observed requests and responses. They are not node-wide queue length or fullness measurements. Network Health is not a queue measurement either.
- Main and Lite toolbar alignment is corrected across English, Turkish, Russian, Arabic, Chinese and Indonesian. Translated labels remain within their controls rather than overlapping the income and running panels.
- Main/Lite Start All animation remains available subject to the user's animation preference.

No claim is made that these changes increase acceptance or rewards. Network availability, acceptance rate and reward amounts cannot be guaranteed.

## Existing features retained

- PRO and PRO B keep separate application identities, executable names, installation directories and local data areas. They can be installed and launched independently.
- Main and Lite share the top two toolbar rows. Add Wallet and compact Log controls remain beside the mining controls.
- Daily NACKL follows the verified network daily epoch rather than local midnight or a rolling 24-hour period. Epoch NACKL follows the short mining epoch.
- Genuine late results remain associated with their older session, separate from a newer session.
- Blue and green accept indicators retain their short-epoch reset behavior and card background tint.
- Wallet backup, recent reward display, network health, start delay and fixed production tap timing remain available.

> Do not mine the same wallet in PRO and PRO B at the same time. Side-by-side installation is intended for controlled comparison, not duplicate wallet operation.

## Legacy backup converter

The release retains the Windows utility for owners of older self-contained wallet-backup EXE files. It converts the encrypted backup payload into the `.cappacki` format accepted by PRO and PRO B.

The legacy EXE is never executed. The utility opens it only as a data file, validates the backup envelope, then writes and verifies a new `.cappacki` file. It does not ask for the backup password or decrypt wallet data. Import the result through **Wallet Backup > Import Wallet Backup** and enter the original backup password in CappAckiMiner.

## Installation and security

- Back up wallets before installing or upgrading, and stop mining at an appropriate time before running an installer.
- The installers do not currently carry an Authenticode signature, so Windows SmartScreen may show a warning.
- Download only from this official release and verify SHA-256 before running.
- Application source code, wallet files and private mining implementation details are not included in this public repository.
- Full English installation, usage, settings, status and troubleshooting guidance is available in [HELP.md](https://github.com/cappackiminer/CappAckiMiner-PRO/blob/main/HELP.md).

## SHA-256

```text
7FDAEA90E8AB62785A1DAFD14892D2889BF1A38A330C18001C0BCA532D8ACFE3  CappAckiMiner-PRO.exe
1519BEF29CC7865714466B47394A1E5CE2FEB9AEDAB004637CA9D905DD83EE2E  CappAckiMiner-PRO_B.exe
5217A1BBD53A47D74904FF5EE2C6D888522DCC5145979B88446C75BF342B3FC9  CappAckiMiner-Legacy-Backup-Converter-Setup.exe
656C8B07796288CA53FE270C55D146C1D06AED1444C68CD86CB8804E5ECD40BF  CappAckiMiner-Legacy-Backup-Converter.exe
```

[Android PRO downloads](https://github.com/cappackiminer/CappAckiMiner-PRO/releases/tag/android-pro-2026-09-17)

GitHub's automatic Source code ZIP/TAR downloads contain only this distribution repository's documentation, not the application source code.
