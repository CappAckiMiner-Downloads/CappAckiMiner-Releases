# CappAckiMiner PRO — User Guide and Help

This guide covers safe installation, basic operation, visible settings, on-screen statuses and troubleshooting for the Windows PRO and PRO B editions. Proprietary mining algorithms, internal scheduling, SDK call ordering and submission implementation are intentionally not included in this public documentation.

## Contents

- [Choosing an edition](#choosing-an-edition)
- [Before installation](#before-installation)
- [Installing on Windows](#installing-on-windows)
- [First launch and wallets](#first-launch-and-wallets)
- [Starting and stopping mining](#starting-and-stopping-mining)
- [Dashboard counters](#dashboard-counters)
- [Wallet-card statuses](#wallet-card-statuses)
- [Accept indicators](#accept-indicators)
- [Settings](#settings)
- [Wallet backups](#wallet-backups)
- [Updating and using both editions](#updating-and-using-both-editions)
- [Troubleshooting](#troubleshooting)
- [Sharing logs safely](#sharing-logs-safely)
- [Verifying downloads](#verifying-downloads)

## Choosing an edition

| Edition | Purpose | Internal version |
| --- | --- | --- |
| **PRO** | Established Windows edition | `1.3.20-test.4.3pro.13` |
| **PRO B** | Single Engine edition for continued development and testing | `1.3.20-test.28` |

PRO.13 is the established Windows edition. PRO B TEST.28 includes status-display improvements and multilingual toolbar corrections. The two editions keep their separate identities and existing wallet data areas.

Both editions use the Single Engine architecture. They have separate application identities, installation directories, executable names and local data areas, so they can be installed and opened independently on the same computer.

> **Important:** Do not mine the same wallet in PRO and PRO B at the same time. That is not a valid A/B comparison and may create conflicting sessions for the wallet.

## Before installation

1. Create a current backup of all wallets.
2. Confirm that the backup file is accessible and stored in a safe location.
3. Compare the downloaded installer's SHA-256 value with the value published in this repository.
4. If mining is active, stop it in a controlled manner at an appropriate time before upgrading.
5. Download installers only from the official release page in this repository.

The Windows installers are not currently signed with Authenticode. Windows SmartScreen may therefore display an “unrecognized app” warning. Do not continue until you have verified the filename, download address and SHA-256 value.

## Installing on Windows

1. Download the installer for the edition you want.
2. Verify its SHA-256 value.
3. Run the installer and complete the displayed steps.
4. Open the application from the Start menu or the created shortcut.
5. Allow the first-launch process to finish before closing the application.

PRO and PRO B no longer install over each other. Each edition has its own application name and local data area.

## First launch and wallets

If a compatible legacy CappAckiMiner profile is found, the application may copy that profile into its own data area once during first launch. After migration, PRO and PRO B keep their data independently. Adding or removing a wallet in one edition is not expected to change the other edition automatically.

After first launch:

- Confirm that the wallet count is correct.
- Verify that wallet names and addresses match the intended accounts.
- Import missing wallets from a trusted backup.
- Confirm that a backup exists before deleting any wallet.
- Never run the same wallet in both editions simultaneously.

To add a wallet, use the **+ wallet** button beside the red Stop All button in the second top row. Main and Lite now share these two top rows, so the control stays in the same place when switching views. For an existing backup, use **Wallet Backup > Import Wallet Backup**.

## Starting and stopping mining

### Start All

Start All begins the bulk-start process for wallets that are ready. Wallets that are not ready yet may join the queue when their required checks complete. The selected bulk-start delay also applies at verified new-epoch starts for wallets managed by Start All.

### Start on an individual wallet card

The Start button on a wallet card targets only that wallet. It does not use the additional bulk-start delay, but network, epoch and safety checks still apply.

### Stop and Stop All

- Stop on a wallet card records a stop request for that wallet.
- Stop All stops active wallets and cancels pending bulk starts.
- A genuine SDK result from an older session may arrive after Stop. Such a result does not restart mining.

Pressing a control repeatedly does not make the operation complete faster. Wait for the card status to change.

## Dashboard counters

### Total NACKL

Displays the combined visible balance read from the application's wallets. A delayed network response may cause the previous value to remain visible briefly.

### Daily NACKL

Shows the sum of observed positive balance increases within the verified network daily epoch. It is not a rolling 24-hour counter and is not tied to local midnight. It resets when a verified new daily epoch is observed.

### Epoch NACKL

Accumulates observed reward increases during the current short mining epoch and resets on a verified new short epoch. Where available, the three-dot menu shows recent epoch history.

### CPU and TPS

CPU represents application workload. TPS is an informational view of observed network transaction activity. High TPS or low CPU usage does not by itself guarantee an accept.

### Network Health

Network Health is an auxiliary indicator built from external network observations. Its red-to-yellow-to-green background provides a quick visual summary.

- **No data:** No valid observation has been received yet.
- **Stale data:** The most recent observation is no longer current.
- The displayed percentage is not a guarantee of mining success.
- It is not a node message-queue length or fullness measurement. PRO B's submission observations in Log describe only this application's observed sessions and responses, not the entire network queue.

## Wallet-card statuses

Statuses are intentionally short. It is normal for a wallet card to pass through several states during one lifecycle.

| Status | General meaning |
| --- | --- |
| `READY` | The wallet is ready to receive a start request. |
| `QUEUE` | A local start or network operation is queued. |
| `MINING` | An active mining session is running. |
| `WAIT` | The application is waiting for the current SDK or network stage. |
| `RESULT` | A result is being processed or verified. |
| `CHECK` | The result or epoch state is being checked again. |
| `CLOSE` | The previous session is completing a safe close stage. |
| `EPOCH` | The wallet is waiting for a verified new epoch. |
| `REC` / `RESTORE` | The application is attempting to recover the wallet's working state safely. |
| `Insufficient time` | There is not enough time remaining in the current epoch to start a new safe session. |

Seeing `BC 70` does not, by itself, prove that a local session completed successfully. The final state must also account for SDK and network results.

### Why does “Insufficient time” appear?

A new mining session is not started when too little time remains for it to complete safely in the current epoch. This protection does not forcibly interrupt a session that is already active. A completed session's result or close status should not be replaced merely because the remaining epoch time is low.

## Accept indicators

Wallet-card border colors show the session context in which a genuine SDK result was observed:

- **Green:** An accept was observed for the current session in the verified current epoch.
- **Blue:** A genuine accept from an earlier session arrived late.
- **Alternating blue and green:** The card has both a late older-session accept indicator and a current-session accept indicator.
- **Red in PRO B:** A genuine SDK reject was observed. When accept and reject results arrive in the same observed epoch, the latest genuine result determines the card's result color. A network error alone is not a reject.

These visual indicators reset on a verified new short epoch. A border is informational only: it does not start or stop mining and does not replace reward accounting.

The green number on a wallet card is the accept counter, while the red number is the reject counter. Hover over a number to display its label.

## Settings

### Wallet start spacing

Adds spacing between bulk wallet-start requests so that many wallets do not create a simultaneous load spike. A lower value does not necessarily produce better results.

### Start All delay

Controls how long wallets managed by Start All wait after a verified epoch start. Starting a wallet directly from its card skips this additional bulk delay.

### Main and Lite views

Main provides larger cards and a more detailed layout. Lite uses a denser layout so that more wallets can be monitored on one screen. Both views now share Lite's top two rows, including the Add Wallet button and the compact log button. The controls remain visible at desktop widths from 1280 to 1920 pixels. Changing the view does not change the mining engine.

Main cards show the three most recent reward amounts beside their arrival times. The timestamps use a more readable 8–9 px size, while full reward amounts retain priority even in narrow cards. Lite wallet rows are unchanged by this adjustment.

### Language and animations

The language option changes interface text. PRO B's shared Main/Lite toolbar has been checked in English, Turkish, Russian, Arabic, Chinese and Indonesian to keep translated controls from overlapping. The general animation option affects only supported visual effects and does not change mining results.

## Wallet backups

A verified wallet backup is the most important safety measure before updates or testing.

- Store backups only in a trusted offline or encrypted location.
- Never make a cloud share link publicly accessible.
- Never attach a wallet backup to a GitHub issue, Telegram group or support message.
- After importing, verify wallet names and the total wallet count.
- Do not close the application until the import has completed.
- Test the new backup before deleting an older known-good backup.

The Wallet Backup option opens the supported backup and import workflow. If you use a separate backup utility, confirm that its file is compatible with the installed edition.

### Converting an older wallet-backup EXE

Older CappAckiMiner backups may be self-contained `.exe` files, while current PRO editions use the `.cappacki` format. Download the **CappAckiMiner Legacy Backup Converter** from the Windows release page:

- Use the setup package for Desktop and Start Menu shortcuts.
- Use the portable package if you prefer a single executable with no installation.

Open the converter, select the old backup EXE and choose a destination for the new `.cappacki` file. Then open **Wallet Backup > Import Wallet Backup** in PRO or PRO B and enter the original backup password.

The converter never starts the old EXE. It reads and validates only the embedded encrypted backup payload, does not decrypt wallet material and leaves the original file unchanged. Do not upload either backup file to GitHub, Telegram, chat or a public cloud link.

## Updating and using both editions

1. Stop mining at an appropriate time.
2. Create and verify a current wallet backup.
3. Verify the new installer's SHA-256 value.
4. Run the installer for the relevant edition.
5. After launch, check wallets and settings.
6. Observe a small number of wallets first, then use bulk start.

PRO and PRO B may be open at the same time, but one wallet must run in only one edition. For comparisons, use separate wallet groups or test the same wallet sequentially under comparable network conditions.

Uninstalling one edition does not uninstall the other. If an uninstaller offers to remove local application data, do not approve that option without a verified backup.

## Troubleshooting

### Start All is disabled or a wallet does not start

- Confirm that at least one wallet is ready.
- Check whether the card reports `Insufficient time`.
- Check the wallet's AUTO state and whether a Stop request is pending.
- Check Network Health for a no-data or stale-data warning.
- Try Start on one individual wallet card first.
- Allow the current check to finish instead of repeatedly reopening the application.

### A wallet remains in WAIT, RESULT, CHECK or CLOSE

These states do not always indicate a freeze. The application may be waiting for a delayed network/SDK result or a safe close of an older session.

- Check Network Health and the internet connection.
- Confirm that the same wallet is not active in the other edition.
- Observe at least one epoch transition.
- If the problem repeats, export a log and share only the relevant time range after removing sensitive information.

In current builds, a verified new epoch can retire inactive local ownership left by an older session so that it does not unnecessarily block the next start. A genuine late result may still be attributed to the older session, but it cannot take control of a newer session.

### Accept is low or reject is high

Acceptance is not controlled by the interface alone. Network load, endpoint responses, SDK results, wallet authorization and epoch conditions may all affect it.

- Do not run the same wallet in two applications simultaneously.
- If Network Health is poor or stale, do not judge performance from a single epoch.
- Observe several complete epochs under controlled settings instead of constantly changing values.
- Do not confuse accept/reject counters with reward balance changes.

### Network Health shows “No data” or “Stale data”

- Check the internet connection.
- Check whether a firewall or DNS policy blocks access to the network-observation service.
- Wait for the next update; the indicator is shared by the application, not queried separately for every wallet.
- Missing data does not automatically mean that the network is healthy or unhealthy.

### Balance or Daily/Epoch NACKL updates late

Network reads may arrive late or out of order. Counters are designed to include only verified observations in the appropriate order. Repeatedly restarting the application does not make the network update faster.

### Windows blocks the application

- Confirm that the file came from the official release page.
- Verify its SHA-256 value.
- If the hash does not match, do not run the file; download it again.
- On a managed device, follow your system administrator's policy.

### PRO and PRO B do not open independently

Current installers give PRO and PRO B separate application identities, executable names and local data locations. Close any older build, reinstall both current packages and use the exact application names shown in the Start menu.

## Sharing logs safely

Diagnostic logs are useful, but always inspect them before sharing.

Never share:

- private keys or recovery phrases,
- wallet-backup files,
- secret authorization data contained in connection or deep links,
- unnecessary personal path and system information,
- access tokens, cookies or API keys.

Where possible, share only a few minutes before and after the problem. Keep the original log privately and redact sensitive fields from the copy that will be shared.

## Verifying downloads

Current Windows installer hashes:

```text
7FDAEA90E8AB62785A1DAFD14892D2889BF1A38A330C18001C0BCA532D8ACFE3  CappAckiMiner-PRO.exe
D58242C7DD29002F3941A006780397FA05C9653C410483CB291A848E70E2FA93  CappAckiMiner-PRO_B.exe
```

PowerShell:

```powershell
Get-FileHash .\CappAckiMiner-PRO.exe -Algorithm SHA256
Get-FileHash .\CappAckiMiner-PRO_B.exe -Algorithm SHA256
```

The reported hash must match the value on this page exactly. Do not run the file if even one character differs.

## Information to include in a support request

The following information helps diagnose a problem without exposing wallet secrets:

- whether you use PRO or PRO B,
- the complete internal version shown in About or Log,
- your Windows version,
- the local time and epoch in which the problem occurred,
- the number and level range of affected wallets,
- the status displayed on the card,
- the relevant redacted log section,
- a screenshot that contains no private information, where possible.

A private key, recovery phrase or wallet-backup file is never required for support.

## Limitations

CappAckiMiner is a network client. It cannot guarantee network availability, SDK outcomes, acceptance rate or reward amount. Health indicators, counters and statuses are diagnostic and monitoring tools; they do not alter the final on-chain result.

This guide covers supported use without publishing private implementation details.
