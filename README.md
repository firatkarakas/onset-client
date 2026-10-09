<p align="center">
  <img src="assets/hero.svg" alt="Onset: self-hosted voice, text and screen sharing for Windows. The desktop strip in a call, above the top of its panel." width="100%">
</p>

<p align="center">
  <a href="https://github.com/firatkarakas/onset-client/releases/latest"><b>Download the latest release</b></a>
  &nbsp;·&nbsp;
  <a href="https://apps.microsoft.com/detail/9MVQJC12LBKD">Microsoft Store</a>
  &nbsp;·&nbsp;
  <a href="https://onsetvoice.com">Website</a>
  &nbsp;·&nbsp;
  <a href="https://github.com/firatkarakas/onset-host">Host a server</a>
  &nbsp;·&nbsp;
  <a href="#verify-your-download">Verify your download</a>
  &nbsp;·&nbsp;
  <a href="#troubleshooting">Troubleshooting</a>
</p>

# Onset for Windows

Onset is a desktop app for group voice calls, text rooms and screen sharing on a server that you or a friend runs. There is no Onset account and no hosted service: the app connects straight to an [Onset Host](https://github.com/firatkarakas/onset-host) on someone's own Windows PC. It stays out of the way as a slim strip on the edge of your screen, and your call keeps running while you work in other windows.

This repository hosts the Windows installers, release notes and update feed. Downloads are on the [Releases page](https://github.com/firatkarakas/onset-client/releases/latest). The same app is in the [Microsoft Store](https://apps.microsoft.com/detail/9MVQJC12LBKD) as **Onset Voice**. Onset is free; by downloading or installing it you agree to its [license](LICENSE.txt), and the app works as the [privacy policy](https://onsetvoice.com/privacy/) describes.


## Contents

- [Features](#features)
- [Install](#install)
- [Connect to a server](#connect-to-a-server)
- [Using the app](#using-the-app)
- [Verify your download](#verify-your-download)
- [Updates](#updates)
- [Security and privacy](#security-and-privacy)
- [Troubleshooting](#troubleshooting)
- [Uninstall](#uninstall)
- [Support](#support)
- [License](#license)

## Features

**Voice**
- Opus voice at 48 kHz from a native audio engine, with echo cancellation, noise suppression, a microphone gate and packet-loss concealment.
- **End-to-end encrypted calls** (Onset 1.0.9 with Onset Host 1.0.5 or later): voice, screen sharing and the sound of a share are encrypted on your PC and opened only by the people in the call; the server that relays them has no keys. Onset uses DAVE, the open protocol Discord published. Everyone in the call sees the same 30-digit code to compare out loud, and a lock beside the server tells you whether the call is encrypted.
- Voice travels over UDP with Onset's own encrypted protocol, GCA4 (ChaCha20-Poly1305, keys for each session, replay protection).
- A speech threshold that follows the noise in your room by default, or one you set yourself on the live level meter, and a microphone test that names the microphone it hears and says when nothing arrives from it.
- Volume and "Mute for me only" for each person, set from that person's menu, which opens from their seat in the call or their name in chat. It affects only what you hear.
- Voice activation or push-to-talk with an adjustable release delay, so the end of a word is not cut off, plus push-to-mute.
- Shortcuts that keep working while Onset is in the background, in games too: push-to-talk, push-to-mute, mute, deafen, screen sharing, and show or hide. Use any key, mouse button or combination. The game still gets the key.

**Text and files**
- Text rooms whose history is kept on the server, plus direct messages. Direct messages are text only; calls happen in voice rooms.
- Replies, edits, deletes, `@mentions`, emoji reactions, unread counts and search across messages and files, with an emoji picker in the message box.
- Display names and profile pictures (any image; Onset crops and shrinks it). Pictures in chat are shown whole, and a click opens them fitted to the screen.
- File sharing with resumable uploads (up to 512 MiB per file by default; the server owner sets the limits), downloads that pick up where they stopped if the connection drops, and inline image previews.
- A ping or nudge for someone who is online.

**Screen sharing**
- Share a window or a whole screen through the Windows picker, at 720p, 1080p or Source resolution and 30 or 60 fps. Shares use AV1 where your PC can encode it smoothly, which keeps text sharp at about a quarter of the bandwidth, and H.264 otherwise.
- Sound from the shared app is included. When you share a window, only that app's audio is captured; when you share a screen, Onset's own audio is left out so nobody hears themselves echoed back.
- Up to five people in a voice room can share at once (Onset Host 1.0.3 or later). Watch one or several, laid out as **Focus**, **Grid** or **Single**; you hear the one in focus. A share sends you nothing until you choose to watch it.
- See who is watching (Onset Host 1.0.4 or later), and the stream's frame rate, bitrate, loss and round trip.
- Full screen fills the screen, with controls that float over the picture and step aside when the mouse rests, or pop a stream out into a picture-in-picture window.

**Desktop**
- A docked strip that snaps to the top or bottom edge of the screen, or floats wherever you drop it. Grab it anywhere on its empty space; double-click there to open or close the panel.
- Your ping on the panel's tab row, and during a call the jitter-buffer depth and packet loss.
- Interface sounds: sixteen short cues for messages, pings, people joining and leaving, your microphone and headphones, and screens shared and watched, with their own volume.
- System tray (the icon moves while someone in your call is talking), start with Windows, desktop notifications and signed in-app updates.

<p align="center">
  <img src="assets/strip-panel.svg" alt="Illustration of the Onset strip with the panel open on the Chat tab. The strip shows the server button, a call pill in the middle reading 'Maya is speaking' with the call time, an unread count on its corner and the microphone and headphones buttons on it, then the settings, minimise and close buttons. The panel has Chat, Screen, Search, Profile and Settings tabs, a live line reading 'ping 18 ms, buffer 40 ms, 0.0% loss', a rooms column and a text room." width="100%">
</p>

## Install

### Requirements

- Windows 10 or Windows 11, 64-bit (x64).
- Microsoft Edge WebView2 Runtime. Windows 11 already includes it. If it is missing, the installer downloads and installs it, which needs an internet connection.
- A microphone and speakers or headphones for calls.
- An Onset Host to connect to, run by you or by someone you trust. Every 1.0 release works; several screen shares in one room need 1.0.3, seeing who is watching needs 1.0.4, and end-to-end encrypted calls need 1.0.5. See the [server repository](https://github.com/firatkarakas/onset-host).

### Steps

1. Open the [latest release](https://github.com/firatkarakas/onset-client/releases/latest) and download `Onset-<version>-x64.msi` and `SHA256SUMS`.
2. Optional, but a good idea: [check the file's hash](#verify-your-download).
3. Run the MSI. The installer is not signed with a paid code-signing certificate, so Windows SmartScreen may show **Windows protected your PC**. After you have checked the hash, choose **More info**, then **Run anyway**.
4. Start **Onset**. A small sign-in card appears in the middle of the screen.

**From the Microsoft Store.** Install [Onset Voice](https://apps.microsoft.com/detail/9MVQJC12LBKD) instead of steps 1 to 3. It is the same app, installed and updated by the Store, with no SmartScreen warning. The Store publishes a new version after Microsoft has reviewed it, so it can arrive a few days after it appears here.

## Connect to a server

<p align="center">
  <img src="assets/invite-flow.svg" alt="Three steps: 1, the owner hosts Onset Host; 2, the owner clicks Copy invite in the control panel, which gives an address such as 203.0.113.42:8080 followed by a hash sign and the server's SHA-256 fingerprint; 3, you paste the invite into the app's Server address field, the app reports that 203.0.113.42:8080 answered, and it checks and remembers the fingerprint." width="100%">
</p>

1. **Get an invite from the server owner.** It looks like `203.0.113.42:8080#` followed by 64 hexadecimal characters. That long part is the SHA-256 fingerprint of the server's certificate. If the server only allows invited people to register, also ask for the **invite token**.
2. **Paste the invite into Server address.** The card checks the server before you type a password. When it answers, you see a line such as `203.0.113.42:8080 answered`.
3. **Create an account or sign in.** For a new account, choose **Register a new account**, pick a username (at least 2 characters) and a password (at least 8), and paste the invite token into the **Bootstrap token** field. Then choose **Create the account**. Accounts belong to one server, so you register separately on each server you join.
4. After you connect, the card turns into the strip. Your session is remembered, so you do not have to type your password again next time.

**Without an invite.** You can also type just `host:port`, for example `192.168.1.20:8080`. The app then trusts the certificate it sees when you first press **Connect** and pins it (trust on first use); merely typing an address never pins anything. To confirm you reached the right server, compare the **Identity** shown under the address with the fingerprint in the owner's control panel.

**Setting up your own server?** The first account on a new server becomes its **owner**. Register it with the **First owner setup token** from the control panel, entered in the **Bootstrap token** field. The [server README](https://github.com/firatkarakas/onset-host#first-start) walks through it.

## Using the app

**The strip.** From left to right: the grip, the server button with a connection dot (hover it for the server's address), the call pill in the middle, then **Settings**, minimise and close. Drag the grip, or any empty part of the strip, to move it; double-click the empty part to open or close the panel. The call pill shows, in this order of priority, *Deafened*, *Muted*, who is speaking, or the room name, along with the call time and a level meter, and carries the microphone and headphones buttons; click the name to open the panel. A red number on its corner counts unread messages. When you are not in a call, it becomes **Join voice**, which opens the panel so you can pick a room; your own shortcuts still mute and deafen. When someone pings you, their name appears next to the server button for a few seconds. Your ping is on the panel's tab row.

**The panel** has five tabs:

| Tab | What it is for |
| --- | --- |
| **Chat** | Rooms, direct messages, the conversation and the message box. In a voice room, the people in the call: someone sharing has a **Live** badge, and pointing at their seat offers **Watch**. Right-click a seat for the person's menu. |
| **Screen** | Every share in your voice room: watch one or several in the **Focus**, **Grid** or **Single** layout, with the stream's figures, who is watching, picture-in-picture and full screen. Your own share starts here. |
| **Search** | Search messages and files. |
| **Profile** | Display name, avatar, password, theme and sign-out. |
| **Settings** | Everything about this PC, one page at a time: **Voice**, **Screen share**, **Shortcuts**, **Notifications**, **Window** and **About** (see below). |

**Settings** lists its pages on the left and shows one at a time:

- **Voice**: microphone and speakers with their volumes, the **Microphone test** with the speech threshold (sound below it is not sent), the input mode and processing. With **Automatic speech threshold** on (the default) Onset sets the threshold from the noise in your room, just above its quietest moments, and shows it on the live level meter while the microphone is in use; turn it off to drag the marker yourself, just under where your voice lands. The test names the microphone it listens to and says so if nothing arrives from it; during a call it shows your microphone in the call instead. The input mode is **Voice activity** or **Push to talk** (with its key and release delay); processing is echo cancellation, noise suppression and automatic gain.
- **Screen share**: the quality and frame rate a new share starts from, whether a share carries the whole machine's sound, and how loud other people's shares play.
- **Shortcuts**: the keys that work everywhere (below).
- **Notifications**: desktop notifications, interface sounds and their volume, and what a new message does: open the panel, or show a preview line on the strip.
- **Window**: keeping the strip above other windows, closing the panel when it is left alone, the close button, starting with Windows, and **Quit Onset**.
- **About**: updates and the installed version, anonymous performance data (from 1.0.9: its switch and the last report sent), call diagnostics, the event log, and live reception counters for the call.

**Where things are.** Share your screen from the panel's **Screen** tab, or with your sharing shortcut. To leave a call, use the red **Leave** button under the call in the panel, or right-click the voice room in the room list. The server button opens your saved servers, with **Disconnect** and, for people with the right role, **Administration**. Beside the server you are on, a lock says whether anyone else can listen: closed and green when your call (or, outside a call, the server's calls) is end-to-end encrypted, open and red when it is not; point at it for the reason. In a voice room, the line above **Leave** shows the call's 30-digit code. **Sign out** is in **Profile**, **Quit Onset** is in **Settings → Window** and in the tray menu, and **New room** is at the bottom of the room list. The close button on the strip puts Onset in the tray and keeps your call running; click the tray icon to bring the window back. Turn off **Settings → Window → Close button keeps Onset in the tray** if you would rather it, and Alt+F4, quit Onset.

**Keyboard.** Calls are controlled only by the shortcuts you choose (below); Onset has no fixed keys of its own. The one key the window answers to is `Esc`, which closes the topmost layer: a menu, an image, the side column, then the panel.

**Shortcuts in the background.** **Settings → Shortcuts** binds push-to-talk, push-to-mute, mute, deafen, start or stop sharing, and show or hide Onset. They work in any app, including full-screen games, and while Onset is minimised or in the tray. None is bound until you choose a key.

- Click the action's key, then press the key, mouse button (middle or side) or combination you want. Let go to finish, or press `Esc` to cancel. The cross clears it.
- Onset reads only the keys you bind. It never sees anything else you type, and it does not take the key away from the game.
- A shortcut still works while you hold other keys, so push-to-talk keeps working while you run. A modifier bound on its own keeps its side: **Right Ctrl** is not **Left Ctrl**.
- One key does one thing. Binding a key that another action uses moves it.

The push-to-talk key also appears in **Settings → Voice**, under the input mode, when push-to-talk is chosen.

## How it connects

<p align="center">
  <img src="assets/architecture.svg" alt="Diagram: each desktop client talks to your Onset server on one UDP port, 8080 by default, which carries HTTPS and WSS control over QUIC with a pinned self-signed identity, GCA4 encrypted voice, and WebRTC screen sharing with DTLS-SRTP. The server stores data in SQLite on the same PC. No third-party servers are involved." width="100%">
</p>

- Everything goes to **one UDP port** on the server, the one in the invite (8080 by default).
- **Control** (sign-in, chat, files) always uses HTTPS and secure WebSockets (WSS), carried over QUIC, and the certificate must match the pinned fingerprint.
- **Voice** uses the GCA4 protocol. The server relays each speaker separately, which is how you can set each person's volume on your side.
- **Screen sharing** uses WebRTC through the server's forwarding unit (SFU), encrypted with DTLS-SRTP.

The app also connects to servers running Onset Host 1.0.1 or earlier, which use TCP 8080, UDP 9000 and UDP 9001.

## Verify your download

Each release includes a `SHA256SUMS` file. In PowerShell, from the folder you downloaded to:

```powershell
$file = 'Onset-1.0.9-x64.msi'   # the file you downloaded
$expected = (Select-String -Path .\SHA256SUMS -Pattern ([regex]::Escape($file) + '$')).Line.Split(' ')[0]
$actual = (Get-FileHash ".\$file" -Algorithm SHA256).Hash
if ($actual -eq $expected) { 'OK: the hash matches' } else { 'MISMATCH: do not install this file' }
```

Or run `Get-FileHash .\Onset-1.0.9-x64.msi -Algorithm SHA256` and compare the result with the matching line in `SHA256SUMS` yourself (upper and lower case do not matter).

The hash confirms that your download matches the published file. It does not replace a code-signing certificate, which this project does not have. In-app updates are checked separately against the update signing key built into the app (see below).

## Updates

- The app checks for a new version shortly after it starts and every few hours while it stays open, using this repository's `latest.json`. When one is available, a banner shows the version and a **Restart** button; during a call the banner waits until the call ends. You can also check from **Settings → About → Check now**. Each package is verified against the updater signature built into the app before it is installed. Packages that fail the check are not installed.
- If a server needs a newer Onset than yours, the sign-in card says so and offers the update right there.
- The Microsoft Store edition is updated by the Store; its own updater is off.

## Security and privacy

- **No Onset accounts or relays.** The app talks to the servers you add and to GitHub when it checks for updates. From 1.0.9 it also sends the developers anonymous performance data unless you turn it off (below). Nothing you say, write or share goes anywhere but your servers.
- **Anonymous performance data** (Onset 1.0.9 and later). Every five minutes the app sends a short report: call and screen-share quality, CPU and memory use, startup time, where it crashed if it did, why a connection failed, and, once per installation, coarse hardware facts (makers and ranges, never model names). It never includes messages, file names, user or display names, server addresses, device names, audio or video, and the IP address it comes from is not kept. Reports carry no identifier of any kind: the collector adds each one to the day's totals and keeps nothing else, so what is stored is anonymous. Onset says so the first time it runs and sends nothing before; **Settings → About** shows the last report exactly as it went and turns it off. Earlier versions send the developers nothing. Details are in the [privacy policy](https://onsetvoice.com/privacy/).
- **Server identity.** Every server has its own long-lived certificate. The app pins its fingerprint from the invite, or on first contact. If a server ever presents a different identity, the app refuses to connect and shows both the remembered and the presented fingerprints. It connects only if you explicitly choose **Trust the new identity**, which you should do only after confirming the new fingerprint with the server owner.
- **End-to-end encrypted calls** (Onset 1.0.9 and later, on Onset Host 1.0.5 and later). Voice, screen sharing and share audio are encrypted with keys only the people in the call hold (DAVE: MLS key exchange, AES-GCM frames). The server relays the key exchange but never has a key. It does decide who is in a call, so Onset gives the keys only to people it shows in the room, and warns you if anyone else holds them. Compare the call's 30-digit code with the others: if it matches, only the people shown in the room can listen. Encryption hides what is said and shown, not who is in a call, when, or who is speaking. A room is not end-to-end encrypted while someone in it uses an older Onset, or if the server's owner turned encrypted calls off; the lock beside the server and the line in the voice room say so.
- **Encryption in transit.** Everything else is protected between you and the server: control traffic with TLS (HTTPS/WSS over QUIC), voice with GCA4 (ChaCha20-Poly1305) and screen sharing with DTLS-SRTP. Messages and files are not end-to-end encrypted: the server stores them, so whoever runs it can technically read them. Only join servers run by people you trust.
- **Your sign-in** is stored on your PC, protected with Windows DPAPI for your Windows user account. Passwords are stored on the server only as bcrypt hashes.
- **Call diagnostics.** While you are in a call, the app sends audio and screen-share statistics (packet counts, buffer depth, loss, device names, app version) to *the server you are connected to*, not to the developers. Audio, video, message text and file names are never included. Turn this off in **Settings → About → Call diagnostics**; the server owner can also switch it off for the whole server.

## Troubleshooting

<details>
<summary><b>Windows SmartScreen says "Windows protected your PC"</b></summary>

The installer is not Authenticode-signed, because the project does not buy a code-signing certificate, and new releases have no SmartScreen reputation yet. [Verify the hash](#verify-your-download), then choose **More info → Run anyway**. Your browser may also warn that the file is not commonly downloaded. Choose **Keep**.
</details>

<details>
<summary><b>"This server's identity changed"</b></summary>

The server presented a different certificate from the one the app remembered. Either the owner reinstalled or reset the server without restoring its identity, or something between you and the server is impersonating it. Ask the owner to read out the **Server identity (SHA-256)** from their control panel. Choose **Trust the new identity** only if it matches the **Presented** fingerprint. If you used an invite and see *"This server's identity does not match the invite"*, ask the owner for a fresh invite.
</details>

<details>
<summary><b>"No answer from …"</b></summary>

- Check the address and port. The owner's control panel shows the exact **Client address** and **Invite**.
- Make sure the server is running (its panel shows **Server online**).
- On a local network, the server PC's Windows network profile must be **Private** for its firewall rule to allow you in.
- Over the internet, the owner's router must forward the server's UDP port (see the [server README](https://github.com/firatkarakas/onset-host#ports-and-firewall)).
</details>

<details>
<summary><b>"answered over TCP only" or "This server needs UDP port …"</b></summary>

The server answered on its TCP port, but its UDP port, which the app uses for everything, did not. Ask the owner to forward the port for **UDP**, not only TCP. If the server works from other networks, the network you are on may block UDP, as some workplace and public networks do.
</details>

<details>
<summary><b>Chat works but there is no voice, or screen shares do not load</b></summary>

On servers running Onset Host 1.0.1 or earlier, chat uses TCP while voice and screen sharing use their own UDP ports (9000 and 9001 by default); check that those are forwarded. On current servers everything uses one UDP port, so if chat works, ask the owner to check that the server is in **Internet** mode for people outside their network.
</details>

<details>
<summary><b>Registration is refused</b></summary>

*"Registration is closed; ask the server owner for an invite token"* means the server needs an invite token, or does not accept new accounts at all. Paste the token from the owner into **Bootstrap token**. For the very first account on a new server, use the **First owner setup token** from the control panel.
</details>

<details>
<summary><b>A shortcut does not work in a game</b></summary>

- Check that the action has a key in **Settings → Shortcuts**. Nothing is bound until you choose a key.
- Push-to-talk works only while the input mode is push-to-talk (**Settings → Voice**).
- If the game runs as administrator, try running Onset as administrator too.
</details>

## Uninstall

Open **Settings → Apps → Installed apps**, find **Onset** (or **Onset Voice** for the Microsoft Store edition) and choose **Uninstall**. The installer's edition keeps settings, your remembered servers and your saved sign-in in your Windows profile under `%APPDATA%\com.onset.desktop` and `%LOCALAPPDATA%\com.onset.desktop`; delete those folders if you want to remove them as well. The Store edition keeps them inside its package, and Windows removes them with it. Messages and files are stored on the servers, not on your PC.

## Support

Email **support@onsetvoice.com**, or report a bug on the [issue tracker](https://github.com/firatkarakas/onset-client/issues). Please include your Onset version (**Settings → About**, "Installed version") and, if you can, the event log from **Settings → About → Export log**. The log holds connection, voice and update events, no message content and no audio.

Questions about a particular server, such as your account, a ban or what happens to your data there, go to the person who runs it. The developer cannot see or change anything on someone else's server.

## Related

- **[Onset Host](https://github.com/firatkarakas/onset-host)**: the Windows installer for hosting your own server, with its local control panel.
- **[Releases](https://github.com/firatkarakas/onset-client/releases)**: every version, with release notes and checksums.

## License

This version of Onset is freeware: free to use, and you may share unmodified copies of the official installer as long as you charge nothing for them. The license applies to the version it ships with. Later versions may be offered under different terms, and the names and logo are not licensed. © Fırat Karakaş. All rights reserved. The full terms, including the warranty disclaimer, are in [LICENSE.txt](LICENSE.txt).

Onset is built on open-source components. Their licenses and full license texts are in `THIRD-PARTY-NOTICES.md`, which is installed next to the program and attached to every release.

This repository contains release files only. The source code is not published here.

Onset is an independent project and is not affiliated with, endorsed by or sponsored by Discord, TeamSpeak, Mumble, Microsoft, Cloudflare or GitHub. Discord is a trademark of Discord Inc.; Microsoft, Windows, Microsoft Store, Microsoft Edge and WebView2 are trademarks of the Microsoft group of companies; other names are trademarks of their owners.
