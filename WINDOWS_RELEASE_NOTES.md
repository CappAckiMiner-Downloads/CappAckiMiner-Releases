# CappAckiMiner Windows — Hunter TEST33 and Burst v1.0.2

## Current packages

| Edition | File | Version |
| --- | --- | --- |
| Hunter SmallWindow | `CappAckiMiner-Hunter-TEST33-WaitFix-SmallWindow-x64-Setup.exe` | `1.3.20-test.33` |
| Burst SmallWindow | `CappAckiMiner-Burst-v1.0.2-WaitFix-SmallWindow-x64-Setup.exe` | `1.0.2` |

These are the two maintained Windows editions. They retain separate application identities and local data areas and may be installed side by side. Do not mine the same wallet in both editions simultaneously.

## Update summary

- Reduced an unnecessary delay before an eligible new start after an older worker has actually closed.
- Improved handling of delayed HTTP response bodies and uncertain delivery results.
- Preserved late genuine results without allowing an older session to take ownership of a newer session.
- Improved the distinction between an actual SDK wait and a wallet that is ready to start.
- Retained SmallWindow resizing, wallet backup support, verified-epoch result colors and recent accept-rate history.

These changes improve local lifecycle and diagnostic behavior. They do not change network priority and do not guarantee a higher acceptance rate.

## SHA-256

```text
9A8CA4E3D64F08FB7AA420D6020C8F2993E68CEAFF4875FE38F14BC1CDEFFBD1  CappAckiMiner-Hunter-TEST33-WaitFix-SmallWindow-x64-Setup.exe
E38AECE87605850259D0A8593784E8145A79DF3E575EB979EAF2804B0A098B96  CappAckiMiner-Burst-v1.0.2-WaitFix-SmallWindow-x64-Setup.exe
```

## Installation

1. Create and verify a current wallet backup.
2. Download the desired installer from the official release.
3. Verify its SHA-256 value.
4. Stop the installed edition at an appropriate time and run the installer.
5. Confirm wallets and settings after launch before using Start All.

The installers do not currently carry an Authenticode signature. Windows SmartScreen may therefore display a warning. Verify the download URL and hash before running the file.

See [HELP.md](HELP.md) for operation, status, backup and troubleshooting guidance. Older packages and utilities remain available in the Windows archive release.
