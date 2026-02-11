# GlassDeck User Guide

This guide covers everything you need to know to set up and use GlassDeck — from first launch to advanced features like plugins, voice commands, and hardware controllers.

---

## Table of Contents

1. [Installation](#installation)
2. [First-Time Setup](#first-time-setup)
3. [Pairing Your Phone](#pairing-your-phone)
4. [Creating Your First Profile](#creating-your-first-profile)
5. [Working with Buttons](#working-with-buttons)
6. [Actions Reference](#actions-reference)
7. [Multi-Action Sequences](#multi-action-sequences)
8. [Toggle Buttons](#toggle-buttons)
9. [Button Folders](#button-folders)
10. [Canvas Backgrounds](#canvas-backgrounds)
11. [Profiles & Pages](#profiles--pages)
12. [Integrations](#integrations)
13. [Plugins & Marketplace](#plugins--marketplace)
14. [Hardware Input](#hardware-input)
15. [Voice Commands](#voice-commands)
16. [Cloud Sync & Sharing](#cloud-sync--sharing)
17. [Collaborative Editing](#collaborative-editing)
18. [Mobile App](#mobile-app)
19. [Settings](#settings)
20. [Updating GlassDeck](#updating-glassdeck)
21. [Troubleshooting](#troubleshooting)

---

## Installation

### Desktop App (Windows)

1. Download the latest installer from the [Releases](https://github.com/DreamGlyphStudios/GlassDeck-Releases/releases) page
2. Run the MSI or NSIS installer and follow the prompts
3. Launch GlassDeck from the Start menu or desktop shortcut

The desktop app is free.

### Mobile App (Android)

Available on the Google Play Store (coming soon). Search for **GlassDeck** by DreamGlyph Studios.

### Mobile App (iOS)

Available on the Apple App Store (coming soon). Search for **GlassDeck** by DreamGlyph Studios.

---

## First-Time Setup

When you first launch the desktop app:

1. **Windows Firewall** — The app will ask to configure a firewall rule so your phone can connect. Click **Configure** to allow it (requires administrator approval). You can also do this later from **Settings > Network**.

2. **Server starts automatically** — The WebSocket server launches on port 8765 by default. You'll see a green status indicator in the bottom bar when it's running.

3. **Create a profile** — Click **New Profile** to create your first button layout. Choose a name, grid size (columns and rows), and how many pages you want.

---

## Pairing Your Phone

Both devices must be on the **same WiFi network**.

### Automatic Discovery (mDNS)

1. Open the mobile app — it will automatically search for your desktop
2. If found, your desktop appears in the server list
3. Tap it to connect

### QR Code Pairing

1. On the desktop app, go to the **Devices** tab
2. A QR code is displayed on screen
3. On the mobile app, tap **Scan QR Code**
4. Point your phone's camera at the QR code
5. The phone pairs and receives your button configuration automatically

### Manual Connection

If mDNS isn't working (common with some routers or VLANs):

1. Find your desktop's IP address (open a command prompt and type `ipconfig`)
2. On the mobile app, tap **Manual Connect**
3. Enter the IP address and port (default: 8765)

---

## Creating Your First Profile

1. Go to the **Profiles** page on the desktop app
2. Click **New Profile**
3. Enter a name (e.g., "Streaming", "Productivity", "Music")
4. Set the grid size — columns and rows determine how many buttons fit on screen
5. Set the page count — multiple pages let you organize more buttons
6. Click **Create**

The new profile opens in the deck editor where you can start adding buttons.

---

## Working with Buttons

### Adding a Button

1. Click any empty cell in the grid
2. The button editor panel opens on the right
3. Configure the button:
   - **Label** — The text shown on the button (optional)
   - **Label Size** — Font size in pixels
   - **Label Color** — Pick a color for the label text
   - **Label Position** — Top, center, or bottom of the button
   - **Icon** — Choose from the built-in library (1500+ icons), upload a custom image, or use an animated GIF
   - **Background Color** — The button's fill color
4. Add one or more **actions** (see [Actions Reference](#actions-reference))
5. Changes save automatically and push to connected phones in real time

### Editing a Button

Click any existing button to select it and open the editor panel.

### Moving Buttons

Drag and drop buttons to rearrange them. Dropping a button on an occupied cell swaps the two buttons.

### Custom Icons

- **Icon Library** — Browse 1500+ built-in icons by name
- **Image Upload** — Upload any PNG, JPG, or GIF. An image cropper lets you resize and position the image before applying it.
- **Animated GIFs** — Uploaded GIFs retain their animation on both desktop and mobile

### Deleting a Button

Select the button and click the **Delete** button (trash icon) in the editor panel.

---

## Actions Reference

Actions are what happen when you press a button. Each button can have one or more actions.

### System Actions (always available)

| Action | What It Does |
|---|---|
| **Keystroke** | Presses individual keys (e.g., Enter, Escape, F5) |
| **Hotkey** | Presses a key combination (e.g., Ctrl+C, Alt+Tab, Ctrl+Shift+T) |
| **Text Input** | Types a text string, optionally pressing Enter at the end |
| **App Launch** | Opens an application (with optional command-line arguments) |
| **System Command** | Runs a shell command |
| **Open URL** | Opens a web link in your default browser |
| **Media Keys** | Play/Pause, Next Track, Previous Track, Volume Up/Down/Mute |
| **Soundboard** | Plays an audio file with adjustable volume |
| **Counter** | Increments, decrements, or resets a named counter (value shows on button) |
| **Timer** | Starts/stops a stopwatch or countdown timer (elapsed time shows on button) |
| **HTTP Request** | Sends a custom HTTP request (GET, POST, etc.) with headers and body |
| **Clipboard** | Copies text to the clipboard |
| **System Power** | Lock screen, sleep, shutdown, or restart |
| **Switch Profile** | Changes the active profile or navigates to a specific page |
| **Navigate Page** | Goes to the next, previous, or a specific page in the current profile |
| **Open Folder** | Opens a folder in File Explorer |
| **Delay** | Waits a specified number of milliseconds (used in multi-action sequences) |

### Integration Actions

These appear in the action picker only when the corresponding integration is enabled. See [Integrations](#integrations) for setup instructions.

| Integration | Available Actions |
|---|---|
| **OBS Studio** | Switch scene, toggle source visibility, start/stop stream, start/stop recording |
| **Twitch** | Send chat message, create clip, run ad, add stream marker |
| **YouTube** | Send chat message, start/stop stream, set stream title |
| **Spotify** | Play/pause, next track, previous track, set volume |
| **Elgato Key Light** | Toggle on/off, set brightness, set color temperature |
| **Discord** | Toggle mute, toggle deafen |
| **vMix** | Switch input, control streaming/recording, adjust audio |
| **Streamlabs** | Switch scene, toggle source, start/stop stream |
| **XSplit** | Switch scene, toggle source, start/stop stream/recording |
| **Wirecast** | Switch shot, trigger transition, toggle stream/recording |
| **Lightstream** | Switch scene, start/stop stream |
| **OneStream** | Control stream, manage destinations |
| **Restream** | Control stream, manage channels, update title |
| **Philips Hue** | Toggle light, set brightness, set color, activate scene |
| **Home Assistant** | Toggle entity, call service, set state, trigger automation |

---

## Multi-Action Sequences

A single button can execute multiple actions in order.

1. Select a button and open the editor
2. Click **Add Action** multiple times to add several actions
3. **Drag and drop** actions to reorder them
4. Set a **Delay** between actions if needed (e.g., wait 500ms between a keystroke and a text input)
5. Click the expand/collapse arrow on each action to edit its settings
6. Use the **Insert** button between actions to add a step in the middle

Example: A "Go Live" button could:
1. Switch OBS to the "Live" scene
2. Wait 1 second
3. Send a Twitch chat message: "We're live!"
4. Set Elgato Key Light to full brightness

---

## Toggle Buttons

Toggle buttons have two states, each with its own set of actions.

1. Select a button and enable **Toggle** in the editor
2. Configure **State 1 Actions** (what happens on the first press)
3. Configure **State 2 Actions** (what happens on the second press)
4. The button alternates between states on each press

Example: A mute/unmute button:
- State 1: Send `Ctrl+M` to mute, change icon to muted microphone
- State 2: Send `Ctrl+M` to unmute, change icon to active microphone

---

## Button Folders

Organize buttons into folders for hierarchical navigation.

1. Create a button and set it as a **Folder** in the editor
2. Click the folder button to navigate into it — you'll see an empty grid
3. Add buttons inside the folder just like the main grid
4. A **Back** button automatically appears to return to the parent level

Folders work on both desktop and mobile.

---

## Canvas Backgrounds

Set a single image that spans the entire button grid, appearing behind all buttons.

1. Go to the profile settings (gear icon in the deck editor)
2. Click **Canvas Background**
3. Upload an image (PNG, JPG)
4. The image stretches across the full grid area
5. Set button backgrounds to transparent or semi-transparent to let the canvas show through

Canvas backgrounds sync to connected mobile devices.

---

## Profiles & Pages

### Multiple Profiles

Create separate profiles for different workflows:
- **Streaming** — OBS scene switches, Twitch chat, Spotify controls
- **Productivity** — App launchers, hotkeys, text snippets
- **Gaming** — Game-specific macros and keybinds
- **Smart Home** — Hue lights, Home Assistant automations

Switch between profiles using the profile switcher on the desktop or a **Switch Profile** button action.

### Pages

Each profile can have multiple pages. Navigate between them by:
- Swiping left/right on the mobile app
- Using **Navigate Page** button actions
- Clicking page indicators on the desktop

### Auto-Switching

GlassDeck can automatically switch profiles based on which application is in the foreground:

1. Edit a profile and go to **Auto-Switch**
2. Add application names (e.g., `obs64.exe`, `spotify.exe`)
3. When that application is the active window, GlassDeck switches to this profile automatically

### Import & Export

- **Export**: Right-click a profile and select **Export** to save it as an `.scprofile` file
- **Import**: Click **Import Profile** and select an `.scprofile` file

---

## Integrations

Integrations connect GlassDeck to external software and hardware. Go to the **Integrations** page on the desktop app to configure them.

### OBS Studio

Controls OBS Studio via its WebSocket protocol (v5).

1. In OBS, go to **Tools > WebSocket Server Settings**
2. Enable the WebSocket server and note the port (default: 4455)
3. Set a password if desired
4. In GlassDeck, go to **Integrations > OBS Studio**
5. Enter the host (`localhost`), port, and password
6. Click **Connect**

You can now add OBS actions to your buttons: switch scenes, toggle sources, start/stop streaming and recording.

### Twitch

Controls Twitch via the Helix API with OAuth authentication.

1. Go to **Integrations > Twitch**
2. Click **Authorize with Twitch**
3. Log in and grant permissions in the browser window
4. GlassDeck stores the token securely

Actions: send chat messages, create clips, run ads, add stream markers.

### YouTube

Controls YouTube Live via the Data API v3 with Google OAuth.

1. Go to **Integrations > YouTube**
2. Click **Authorize with Google**
3. Log in and grant permissions
4. GlassDeck stores the token securely

Actions: send live chat messages, start/stop stream, update stream title.

### Spotify

Controls Spotify via the Web API with OAuth PKCE.

1. Go to **Integrations > Spotify**
2. Click **Connect to Spotify**
3. Log in and grant permissions
4. Requires Spotify Premium for playback control

Actions: play/pause, next/previous track, set volume.

### Elgato Key Light

Controls Elgato Key Lights over your local network.

1. Go to **Integrations > Elgato Key Light**
2. Enter the light's IP address (find it in the Elgato Control Center app)
3. The default port is 9123

Actions: toggle on/off, set brightness (0-100%), set color temperature.

### Discord

Controls Discord mute/deafen via global keyboard shortcuts.

1. In Discord, go to **Settings > Keybinds**
2. Set keybinds for Toggle Mute and Toggle Deafen
3. In GlassDeck, go to **Integrations > Discord**
4. Enter the same keybinds

GlassDeck sends the keyboard shortcuts when you press the button.

### Philips Hue

Controls Philips Hue lights via the local bridge.

1. Go to **Integrations > Philips Hue**
2. GlassDeck discovers your Hue Bridge on the network
3. Press the **physical button on your Hue Bridge** when prompted to pair
4. Your lights and scenes appear in the integration panel

Actions: toggle light, set brightness, set color, activate scene.

### Home Assistant

Controls Home Assistant devices via the REST API.

1. Go to **Integrations > Home Assistant**
2. Enter your Home Assistant URL (e.g., `http://192.168.1.100:8123`)
3. Enter a Long-Lived Access Token (create one in Home Assistant under Profile > Security)
4. Browse your entities and services in the integration panel

Actions: toggle entity, call service, set state, trigger automation.

### Other Integrations

**vMix**, **Streamlabs**, **XSplit**, **Wirecast**, **Lightstream**, **OneStream**, and **Restream** all follow a similar pattern — enable the integration, enter connection details (host, port, or API key), and their actions become available in the button editor.

---

## Plugins & Marketplace

### Installing Plugins

1. Go to the **Plugins** page on the desktop app
2. Click the **Browse** tab to open the marketplace
3. Browse available plugins, profile templates, and icon packs
4. Click **Install** on any item you want
5. Installed plugins appear in the **Installed** tab

### Using Plugin Actions

Once a plugin is installed and enabled:
1. Edit a button and click **Add Action**
2. Plugin actions appear in the action picker under the plugin's name
3. Configure any plugin-specific settings (API keys, URLs, etc.)

### Plugin Permissions

Plugins declare what they need access to (network, keyboard, commands). When you install a plugin that requires permissions, GlassDeck shows a prompt explaining what the plugin wants to do. You can grant or deny each permission.

### Profile Templates

Pre-built button layouts created by the community:
1. Browse templates in the marketplace
2. Click **Install** to add the template as a new profile
3. Customize it to your needs

### Custom Icon Packs

Themed icon bundles from the marketplace:
1. Browse icon packs in the marketplace
2. Click **Install** to download
3. Installed icons appear in the icon picker when editing buttons

### Creating Plugins

See the [Development Guide](DEVELOPMENT.md) for instructions on creating declarative (JSON) and script (JavaScript) plugins.

---

## Hardware Input

GlassDeck supports physical input devices in addition to the mobile app.

### MIDI Controllers

Map MIDI buttons, knobs, and faders to GlassDeck buttons.

1. Go to **Settings > Hardware > MIDI**
2. Select your MIDI device from the dropdown
3. Click **Learn** next to a button mapping
4. Press a key/knob on your MIDI controller
5. The mapping is saved and auto-reconnects when the device is plugged in

### USB HID Devices

Connect macro pads, button panels, and other USB HID devices.

1. Go to **Settings > Hardware > USB HID**
2. Select your device
3. Use learn mode to map physical buttons to GlassDeck buttons

### Serial Devices

Connect Arduino, ESP32, and other serial devices.

1. Go to **Settings > Hardware > Serial**
2. Select the COM port and baud rate
3. Map serial messages to button actions

### Network Hardware

ESP32 or Raspberry Pi devices can connect as WebSocket clients using the same protocol as the mobile app.

---

## Voice Commands

Control GlassDeck hands-free with offline speech recognition.

1. Go to **Settings > Voice Commands**
2. Download a language model (~50MB, one-time download)
3. Select your microphone
4. Click **Enable Voice Commands**
5. Add keyword mappings:
   - **Keyword**: The word or phrase to listen for (e.g., "go live")
   - **Button**: The button action to trigger when the keyword is recognized

Voice recognition runs entirely offline using the Vosk engine — no audio is sent to the cloud.

---

## Cloud Sync & Sharing

### Cloud Sync (GitHub)

Back up your profiles to a GitHub repository and sync them across multiple computers.

1. Go to **Settings > Cloud Sync**
2. Enter a GitHub Personal Access Token with repo access
3. Enter the repository name (e.g., `username/glassdeck-profiles`)
4. Click **Push** to upload your profiles
5. On another computer, click **Pull** to download them

### Community Sharing

Share your profiles with the community or install profiles others have shared.

1. Go to the **Plugins** page > **Community** tab
2. Browse shared profiles
3. Click **Install** to add a community profile
4. To share your own, click **Submit** on one of your profiles

---

## Collaborative Editing

Edit button layouts in real time with another GlassDeck user on a different computer.

1. Go to the **Deck Editor** and click **Collaborate**
2. Share the session code with your collaborator
3. They enter the code on their GlassDeck to join
4. Both users can edit buttons simultaneously
5. Per-button locking prevents edit conflicts — you can see which buttons the other person is editing
6. Changes sync in real time via peer-to-peer WebRTC (with WebSocket relay as fallback)

---

## Mobile App

### Home Screen

When you open the mobile app, it automatically searches for your desktop. Once connected, your button grid appears.

### Using Buttons

- **Tap** a button to trigger its action
- **Swipe left/right** to navigate between pages
- Buttons show visual feedback (animations) and haptic feedback on press
- Toggle buttons change appearance between states

### Switching Profiles

Tap the profile name at the top to see a list of available profiles and switch between them.

### Connection Status

The connection bar at the top shows whether you're connected to the desktop:
- **Green** — Connected and synced
- **Red** — Disconnected (tap to reconnect)

### Settings

Access mobile-specific settings by tapping the gear icon:
- **Theme** — Switch between dark and light mode
- **Server** — View or change the connected server
- **About** — Version information

---

## Settings

### Network

- **Server Port** — Change the WebSocket server port (default: 8765)
- **Windows Firewall** — Configure or reset firewall rules for mobile connections

### Appearance

- **Theme** — Dark or light mode
- **Close to Tray** — When enabled, closing the window minimizes to the system tray instead of quitting

### Auto-Start

Configure GlassDeck to launch automatically when Windows starts.

### About & Updates

- View the current version
- **Check for Updates** — Checks the release server for newer versions
- **Install Update** — Downloads and installs the update (restart required)

---

## Updating GlassDeck

GlassDeck includes a built-in auto-update system.

1. Go to **Settings > About**
2. Click **Check for Updates**
3. If an update is available, click **Install Update**
4. The update downloads and installs automatically
5. Restart GlassDeck to apply the update

You can also download the latest version manually from the [Releases](https://github.com/DreamGlyphStudios/GlassDeck-Releases/releases) page.

---

## Troubleshooting

### Phone Can't Find the Desktop

- **Same network**: Both devices must be on the same WiFi network
- **Firewall**: Go to **Settings > Network** and click **Configure** to set up the firewall rule
- **VLANs**: mDNS doesn't work across VLANs — use manual connection with the desktop's IP address
- **Manual connect**: Open a command prompt, type `ipconfig`, and enter the IPv4 address into the mobile app

### Phone Disconnects Frequently

- Check your WiFi signal strength on both devices
- Some routers aggressively power-save WiFi clients — check router settings
- The app reconnects automatically when the connection drops

### Actions Not Working

- **Keystroke/Hotkey**: Make sure the target application is in the foreground on the desktop
- **OBS**: Verify the OBS WebSocket server is running and the password matches
- **Twitch/YouTube/Spotify**: Re-authorize if the token has expired
- **Soundboard**: Check that the audio file path is correct and the file format is supported (MP3, WAV, OGG, FLAC)

### Desktop Build Errors

See the [Development Guide](DEVELOPMENT.md) for build troubleshooting.

### Reset Everything

GlassDeck stores its data in `%APPDATA%/glassdeck/`. To reset:
1. Close GlassDeck completely (right-click tray icon > Quit)
2. Delete the `%APPDATA%/glassdeck/` folder
3. Restart GlassDeck — it will create a fresh database

**Warning**: This deletes all profiles, buttons, integrations, and settings.
