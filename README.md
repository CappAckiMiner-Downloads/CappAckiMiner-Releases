# CappAckiMiner PRO

Official binary downloads for **CappAckiMiner PRO on Windows and Android**.

> Application source code and private mining implementation details are not published in this distribution repository.

## Downloads

| Platform | Edition | Version | Download |
| --- | --- | --- | --- |
| Windows | PRO | `1.3.20-test.4.3pro.13` | [Download CappAckiMiner-PRO.exe](https://github.com/cappackiminer/CappAckiMiner-PRO/releases/download/windows-pro-ab-2026-09-17/CappAckiMiner-PRO.exe) |
| Windows | PRO B | `1.3.20-test.28` | [Download CappAckiMiner-PRO_B.exe](https://github.com/cappackiminer/CappAckiMiner-PRO/releases/download/windows-pro-ab-2026-09-17/CappAckiMiner-PRO_B.exe) |
| Windows utility | Wallet Monitor | `1.0.8` | [Download Wallet Monitor setup](https://github.com/CappAckiMiner-Downloads/CappAckiMiner-PRO/releases/download/windows-pro-ab-2026-09-17/CappAcki-Wallet-Monitor-v1.0.8-Setup.exe) |
| Windows utility | Legacy backup converter setup | `1.0.0` | [Download converter setup](https://github.com/cappackiminer/CappAckiMiner-PRO/releases/download/windows-pro-ab-2026-09-17/CappAckiMiner-Legacy-Backup-Converter-Setup.exe) |
| Windows utility | Legacy backup converter portable | `1.0.0` | [Download portable converter](https://github.com/cappackiminer/CappAckiMiner-PRO/releases/download/windows-pro-ab-2026-09-17/CappAckiMiner-Legacy-Backup-Converter.exe) |
| Android | Universal 1.3.9 | ARM64 and ARMv7 | [Download Universal APK](https://github.com/CappAckiMiner-Downloads/CappAckiMiner-PRO/releases/download/android-pro-2026-09-17/CappAckiMiner-pro-1.3.9-Universal.apk) |

[Windows release notes](https://github.com/cappackiminer/CappAckiMiner-PRO/releases/tag/windows-pro-ab-2026-09-17) · [Android release notes](https://github.com/CappAckiMiner-Downloads/CappAckiMiner-PRO/releases/tag/android-pro-2026-09-17) · [All releases](https://github.com/cappackiminer/CappAckiMiner-PRO/releases) · [Complete help guide](HELP.md)

## Windows editions

**PRO** is the established Windows edition. **PRO B** is the edition receiving continued development. Current versions are **PRO.13** and **TEST.28** respectively. Both editions retain their separate identities and existing wallet data areas.

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

- Published PRO.13 and PRO B TEST.28 under the existing download filenames.
- PRO B includes status-display improvements and six-language Main/Lite toolbar alignment fixes.

### Existing features retained

- Blue and green accept indicators include a 12% wallet-card background tint and reset at the verified epoch boundary.
- Manual-stop status, daily-epoch monitor consistency and reduced decorative animation in dense wallet views remain available.
- PRO and PRO B can be installed and launched independently.
- Existing verified-epoch handoff and late-result isolation keep older-session results separate from a newer session.
- Wallet backup, daily/epoch counters, network-health display and Main/Lite views remain available.

Acceptance rate, reward amount and uninterrupted network availability cannot be guaranteed.

## Windows verification

```text
7FDAEA90E8AB62785A1DAFD14892D2889BF1A38A330C18001C0BCA532D8ACFE3  CappAckiMiner-PRO.exe
D58242C7DD29002F3941A006780397FA05C9653C410483CB291A848E70E2FA93  CappAckiMiner-PRO_B.exe
6CDFFC68D6E7E528FF4B313A886931CB24877F8CC1FF8726BD7116E9958A652C  CappAcki-Wallet-Monitor-v1.0.8-Setup.exe
5217A1BBD53A47D74904FF5EE2C6D888522DCC5145979B88446C75BF342B3FC9  CappAckiMiner-Legacy-Backup-Converter-Setup.exe
656C8B07796288CA53FE270C55D146C1D06AED1444C68CD86CB8804E5ECD40BF  CappAckiMiner-Legacy-Backup-Converter.exe
```

PowerShell example:

```powershell
Get-FileHash .\CappAckiMiner-PRO.exe -Algorithm SHA256
Get-FileHash .\CappAckiMiner-PRO_B.exe -Algorithm SHA256
Get-FileHash .\CappAcki-Wallet-Monitor-v1.0.8-Setup.exe -Algorithm SHA256
Get-FileHash .\CappAckiMiner-Legacy-Backup-Converter-Setup.exe -Algorithm SHA256
Get-FileHash .\CappAckiMiner-Legacy-Backup-Converter.exe -Algorithm SHA256
```

## Android packages

The Universal APK is the only Android download offered. It is version **1.3.9**, supports both ARM64 and ARMv7, and uses application ID `com.cappackiminer.rootretrysingle.android7`. Minimum Android API level: **24**.

Avoid unnecessary downgrades or uninstalling an existing installation without first creating and safely checking a wallet backup.

## Safety and privacy

- Keep wallet backups, recovery material and private keys offline and private.
- Never publish a wallet-backup file, private key or unredacted diagnostic log in a GitHub issue or chat.
- Verify the SHA-256 hash after downloading.
- Mining acceptance and rewards depend on the network, wallet authorization, SDK responses and current network conditions; they cannot be guaranteed.

For installation, first-run, status explanations, backup guidance and troubleshooting, see the [complete help guide](HELP.md).

GitHub's automatic “Source code” ZIP/TAR files contain only this distribution repository's documentation, not the application's source code.
