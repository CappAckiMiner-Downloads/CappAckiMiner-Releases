# CappAckiMiner PRO

Official binary downloads for **CappAckiMiner PRO on Windows and Android**.

> Application source code and private mining implementation details are not published in this distribution repository.

## Downloads

| Platform | Edition | Version | Download |
| --- | --- | --- | --- |
| Windows | PRO | `1.3.20-test.4.3pro.11` | [Download CappAckiMiner-PRO.exe](https://github.com/cappackiminer/CappAckiMiner-PRO/releases/download/windows-pro-ab-2026-09-17/CappAckiMiner-PRO.exe) |
| Windows | PRO B | `1.3.20-test.22` | [Download CappAckiMiner-PRO_B.exe](https://github.com/cappackiminer/CappAckiMiner-PRO/releases/download/windows-pro-ab-2026-09-17/CappAckiMiner-PRO_B.exe) |
| Windows utility | Legacy backup converter setup | `1.0.0` | [Download converter setup](https://github.com/cappackiminer/CappAckiMiner-PRO/releases/download/windows-pro-ab-2026-09-17/CappAckiMiner-Legacy-Backup-Converter-Setup.exe) |
| Windows utility | Legacy backup converter portable | `1.0.0` | [Download portable converter](https://github.com/cappackiminer/CappAckiMiner-PRO/releases/download/windows-pro-ab-2026-09-17/CappAckiMiner-Legacy-Backup-Converter.exe) |
| Android | Universal 1.3.5 | ARM64 and ARMv7 | [Download Universal APK](https://github.com/cappackiminer/CappAckiMiner-PRO/releases/download/android-pro-2026-09-17/CappAckiMiner-pro-1.3.5-Universal.apk) |
| Android | ARM64 1.3.4 | ARM64 only | [Download ARM64 APK](https://github.com/cappackiminer/CappAckiMiner-PRO/releases/download/android-pro-2026-09-17/CappAckiMiner-pro-ARM64.apk) |

[Windows release notes](https://github.com/cappackiminer/CappAckiMiner-PRO/releases/tag/windows-pro-ab-2026-09-17) · [Android release notes](https://github.com/cappackiminer/CappAckiMiner-PRO/releases/tag/android-pro-2026-09-17) · [All releases](https://github.com/cappackiminer/CappAckiMiner-PRO/releases) · [Complete help guide](HELP.md)

## Windows editions

**PRO** is the TEST4.3 PRO-derived Single Engine line, now frozen at **PRO.11**. Further development and testing will continue on **PRO B**, currently **TEST.22**. Both published builds include the verified-epoch handoff and late-result isolation work.

The two editions now use separate application identities, executable names, installation directories and local data areas, so they can be installed and opened independently. A compatible legacy profile may be copied once on first run and then each edition keeps its own data.

Do **not** start mining the same wallet in both editions at the same time. Side-by-side installation is intended for controlled comparison, not duplicate operation of one wallet.

The PRO and PRO B Windows downloads are installer packages published under stable filenames so existing links continue to work. The applications and converter do not currently carry an Authenticode digital signature; Windows may therefore show a SmartScreen warning.

## Converting legacy wallet-backup EXE files

Older CappAckiMiner wallet backups were distributed as self-contained `.exe` files. Current PRO and PRO B releases import encrypted `.cappacki` backup files. Use the **Legacy Backup Converter** above to convert an old backup without launching it.

1. Install and open the converter, or download the portable converter.
2. Select the old wallet-backup `.exe` file.
3. Save the converted file with the `.cappacki` extension.
4. In PRO or PRO B, open **Wallet Backup > Import Wallet Backup** and select that file.
5. Enter the original backup password when requested.

The converter reads the legacy EXE strictly as data, validates its embedded encrypted backup envelope and copies that encrypted payload into the current format. It does not execute the old EXE, request the wallet password, decrypt private material or modify the original file. Keep both the old and converted backups private.

## What changed in this Windows update

- Published PRO.11 and PRO B TEST.22 under the existing download filenames.
- Main Mode distributes the monitor and income panels across the available toolbar space.
- Main wallet cards give reward amounts more room and use smaller timestamps for the three recent rewards.
- Blue and green accept indicators now apply a more visible 12% background tint to their wallet cards.
- The updates also include clearer manual-stop status, daily-epoch monitor consistency and reduced decorative animation in dense wallet views.
- PRO and PRO B can be installed and launched independently.
- A confirmed new mining epoch can retire obsolete local ownership left by an older completed session, preventing it from unnecessarily blocking the next start.
- A real late SDK result remains attributable to the older session without taking control of the newer session.
- Current-session and late-session accept indicators are kept separate and reset at the verified epoch boundary.
- Existing wallet backup, daily/epoch counters, network-health display, Main/Lite views and fixed production timing remain available.

This release improves lifecycle stability. It does not guarantee an acceptance rate, reward amount or uninterrupted network availability.

## Windows verification

```text
DE47B23A2AE2C4E3BA1748103BB57AF54A4948C239345D5CC85752EEDA8AB663  CappAckiMiner-PRO.exe
0B600EA70829B9BC31DF8F16F749FC754260E821971E437412EE282167A8E1B2  CappAckiMiner-PRO_B.exe
5217A1BBD53A47D74904FF5EE2C6D888522DCC5145979B88446C75BF342B3FC9  CappAckiMiner-Legacy-Backup-Converter-Setup.exe
656C8B07796288CA53FE270C55D146C1D06AED1444C68CD86CB8804E5ECD40BF  CappAckiMiner-Legacy-Backup-Converter.exe
```

PowerShell example:

```powershell
Get-FileHash .\CappAckiMiner-PRO.exe -Algorithm SHA256
Get-FileHash .\CappAckiMiner-PRO_B.exe -Algorithm SHA256
Get-FileHash .\CappAckiMiner-Legacy-Backup-Converter-Setup.exe -Algorithm SHA256
Get-FileHash .\CappAckiMiner-Legacy-Backup-Converter.exe -Algorithm SHA256
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
