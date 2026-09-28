# CappAckiMiner — User Guide and Help

This guide documents the earlier Hunter and Burst interfaces. The current Windows applications are CappAckiMiner ALL Personal 1.0.9 (mining app) and CappAckiMiner Eye 1.0.46 (read-only monitor). The controls and limits below may not match ALL, and this is not an operating guide for Eye. For current downloads and hashes, use README.md or the all-downloads release page.

## Contents

- [Choosing an edition](#choosing-an-edition)
- [Before installation](#before-installation)
- [Installing and updating](#installing-and-updating)
- [Wallets and backups](#wallets-and-backups)
- [Starting and stopping](#starting-and-stopping)
- [Dashboard information](#dashboard-information)
- [Wallet-card statuses](#wallet-card-statuses)
- [Accept and reject indicators](#accept-and-reject-indicators)
- [Main and Lite views](#main-and-lite-views)
- [Troubleshooting](#troubleshooting)
- [Sharing logs safely](#sharing-logs-safely)
- [Verifying downloads](#verifying-downloads)

## Choosing an edition

| Historical edition documented here | Version | General role |
| --- | --- | --- |
| **Hunter SmallWindow** | `1.3.20-test.33` | Queued delivery and diagnostic test edition |
| **Burst SmallWindow** | `1.0.2` | Fixed-policy alternative edition |

Both editions use separate application identities, installation locations and local data areas. They can be installed and opened independently.

> Never mine the same wallet in both editions at the same time. Side-by-side installation is for controlled comparison with separate wallet groups or sequential tests.

## Before installation

1. Create a current backup of every wallet.
2. Confirm that the backup is accessible and stored safely.
3. Download only from this repository's official Releases page.
4. Compare the file's SHA-256 with the published value.
5. Stop the edition being upgraded at an appropriate time before running its installer.

The Windows installers do not currently carry an Authenticode signature. Windows SmartScreen may show an “unrecognized app” warning. Continue only after verifying the filename, repository URL and SHA-256 value.

## Installing and updating

1. Download the desired current installer.
2. Verify its SHA-256 value.
3. Run the installer and complete the displayed steps.
4. Start the application from the Start menu or shortcut.
5. Allow first-launch checks to finish.
6. Confirm wallet names, count and settings before starting all wallets.

Installing one edition does not uninstall the other. If an uninstaller offers to remove local application data, do not approve that option without a verified backup.

## Wallets and backups

Use the **+ wallet** button in the upper controls to add a wallet. To restore existing data, use **Wallet Backup > Import Wallet Backup** and choose a trusted `.cappacki` file.

Backup rules:

- Store backups in a trusted offline or encrypted location.
- Never make a backup share link public.
- Never attach a wallet backup to an issue, chat or support message.
- Verify wallet names and the total wallet count after an import.
- Test a new backup before deleting an older known-good copy.

### Legacy backup EXE files

The current release includes the installable **Legacy Backup Converter** package. A portable converter executable is not listed on this release page. It converts compatible self-contained backup EXE files to `.cappacki` without executing the old EXE or decrypting wallet material.

1. Open the converter.
2. Select the old wallet-backup EXE.
3. Save the converted `.cappacki` file.
4. Import that file through **Wallet Backup**.
5. Enter the original backup password when requested by the miner.

## Starting and stopping

### Start All

Start All begins the bulk-start process for eligible wallets. Wallets still completing required checks may join later. A configured bulk-start delay may apply at a verified new epoch.

### Individual Start

The Start control on a wallet card targets only that wallet. It skips the additional bulk delay, while network, epoch, ownership and safety checks still apply.

### Stop and Stop All

- Stop requests a controlled stop for one wallet.
- Stop All stops active wallets and cancels pending bulk starts.
- Repeated clicks do not make an SDK worker close faster.
- A genuine result from an older session may arrive after Stop; it does not restart mining.

## Dashboard information

### Total NACKL

The combined visible balance read for the application's wallets. A delayed network response may leave the previous value visible briefly.

### Daily NACKL

The sum of observed positive balance changes in the verified network daily epoch. It is not a rolling 24-hour total and is not tied to local midnight. It resets at a verified daily-epoch change.

### Epoch NACKL

Observed reward increases for the current short mining epoch. It resets at a verified short-epoch change. Where available, the three-dot menu shows recent completed-epoch history.

### Accept Rate

Shows the percentage of the 48 displayed wallet slots that received a genuine SDK accept for the verified current epoch. A late accept from an older epoch is credited to its recorded epoch history rather than the current rate.

### CPU, TPS and Network Health

- CPU is the application's current processor use.
- TPS is an informational view of observed network activity.
- Network Health is an auxiliary external observation.

None of these values guarantees an accept or reward. Network Health is not the node's complete message-queue length.

## Wallet-card statuses

| Status | General meaning |
| --- | --- |
| `READY` | The wallet can receive a start request. |
| `QUEUE` | A local start or delivery operation is queued. |
| `MINING` | An active mining session is running. |
| `SDK WAIT` / `WAIT` | The application is waiting for SDK or network readiness. |
| `RESULT` | A result is being processed or verified. |
| `CHECK` | Result or epoch state is being checked again. |
| `CLOSE` | An older session is completing a safe close stage. |
| `EPOCH` | The wallet is waiting for a verified new epoch. |
| `REC` / `RESTORE` | The application is restoring working state. |
| `Insufficient time` | Too little time remains to begin a new safe session. |

`WAIT`, `RESULT`, `CHECK` and `CLOSE` do not automatically mean the application is frozen. A genuinely submitted session may need to retain ownership while waiting for delayed proof or result information.

The Hunter and Burst editions documented in this legacy guide distinguish work that never began a network write from work whose delivery is uncertain. Only the former can be retired safely at a newer verified epoch. A timeout is not proof that a submitted network request was never delivered.

## Accept and reject indicators

Card colors are created only from genuine SDK result callbacks:

- **Green:** accept observed for the current session in the verified current epoch.
- **Blue:** accept from an older session arrived during the current epoch.
- **Alternating blue and green:** both an older-session accept and a current-session accept were observed for that wallet.
- **Red:** genuine SDK reject; a network error alone is not a reject.

The latest genuine accept or reject determines the visible result when both occur. Result colors reset at the next verified short epoch. They do not start or stop mining or replace reward accounting.

## Main and Lite views

Main provides larger wallet cards and more detail. Lite is denser. Switching views does not change the mining engine.

The Hunter and Burst editions documented here retain their normal desktop opening size and support the SmallWindow minimums for manual resizing. Some dense content may need scrolling at very small dimensions.

The language setting changes interface text. The animation setting affects supported decorative effects only and does not change mining results.

## Troubleshooting

### A wallet does not start

- Confirm that the wallet is enabled for automatic operation.
- Check for `Insufficient time`.
- Check whether a Stop request or older SDK worker is still active.
- Check for `SDK WAIT`, network no-data or stale-data warnings.
- Try one individual wallet Start before repeating Start All.
- Do not repeatedly restart the application while a check is in progress.

### A wallet stays in WAIT, RESULT, CHECK or CLOSE

- Confirm the same wallet is not running in the other edition.
- Observe at least one complete epoch transition.
- Check the internet connection and Network Health state.
- Export a log if the same wallet repeats the behavior across epochs.

The current lifecycle fixes remove waits known to be unnecessary, while preserving genuinely sent or delivery-uncertain work so late valid results are not discarded. This means not every CLOSE or WAIT should disappear immediately.

### Acceptance is low

Acceptance depends on network load, endpoint responses, wallet authorization, SDK results and epoch timing. A lower retry value does not guarantee better results and may increase queue errors.

Compare complete epochs with the same wallet group and settings. Do not change several settings during the same comparison and do not run one wallet in both editions.

### Network Health shows No data or Stale data

- Check internet, DNS and firewall access.
- Wait for the next observation.
- Do not treat missing health data as proof that the network is healthy or unhealthy.

### Windows blocks the installer

Verify the official release URL and SHA-256. If one character differs, do not run the file; download it again.

## Sharing logs safely

Inspect every log before sharing it. Redact:

- recovery phrases and private keys;
- wallet-backup files and backup paths;
- authorization tokens, signatures, cookies and API keys;
- wallet/account identifiers that are not needed;
- personal Windows paths and unrelated system details.

Share only the short time range around the problem. No support request requires a recovery phrase, private key or wallet-backup file.

## Verifying downloads

Current Windows executable hashes are listed in README.md and on the all-downloads release page. Compare the full SHA-256 before running either current Windows file:

PowerShell:
Get-FileHash .\CappAckiMiner-Eye-v1.0.46.exe -Algorithm SHA256
Get-FileHash .\CappAckiMiner-ALL-v1.0.9-windows.exe -Algorithm SHA256

If any character differs from the published value, do not run the file; download it again from the official release page.
## Limitations

CappAckiMiner is a network client. It cannot guarantee network availability, message priority, SDK outcomes, acceptance rate or reward amount. Dashboard values and statuses are diagnostic aids; they do not alter the final network result.
