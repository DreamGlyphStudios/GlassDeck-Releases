# GlassDeck User Guide

This guide covers everything you need to know to set up and use GlassDeck — from first launch to advanced features like plugins, voice commands, and hardware controllers. Every integration is explained step by step so you can get connected even if you've never worked with an API before.

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
10. [Sliders](#sliders)
11. [Dynamic Labels & Variables](#dynamic-labels--variables)
12. [Live State Feedback](#live-state-feedback)
13. [Canvas Backgrounds](#canvas-backgrounds)
14. [Profiles & Pages](#profiles--pages)
15. [Integrations](#integrations)
    - [OBS Studio](#obs-studio)
    - [Twitch](#twitch)
    - [YouTube](#youtube)
    - [Spotify](#spotify)
    - [Elgato Key Light](#elgato-key-light)
    - [Discord](#discord)
    - [Philips Hue](#philips-hue)
    - [Home Assistant](#home-assistant)
    - [vMix](#vmix)
    - [Streamlabs](#streamlabs)
    - [XSplit Broadcaster](#xsplit-broadcaster)
    - [Wirecast](#wirecast)
    - [Lightstream](#lightstream)
    - [OneStream](#onestream)
    - [Restream](#restream)
16. [Scheduled Actions](#scheduled-actions)
17. [Webhooks](#webhooks)
18. [Game Auto-Detection](#game-auto-detection)
19. [Multi-Deck View](#multi-deck-view)
20. [Lottie Animated Icons](#lottie-animated-icons)
21. [Chat Overlay](#chat-overlay)
22. [Marketplace](#marketplace)
23. [Plugins & Marketplace](#plugins--marketplace)
24. [Hardware Input](#hardware-input)
25. [Voice Commands](#voice-commands)
26. [Cloud Sync & Sharing](#cloud-sync--sharing)
27. [Collaborative Editing](#collaborative-editing)
28. [Mobile App](#mobile-app)
29. [Settings](#settings)
30. [Updating GlassDeck](#updating-glassdeck)
31. [Troubleshooting](#troubleshooting)

---

## Installation

### Desktop App (Windows)

1. Go to the [GlassDeck Releases](https://github.com/DreamGlyphStudios/GlassDeck-Releases/releases) page
2. Download the latest installer — you'll see files ending in `.msi` (recommended) or `.exe`
3. Run the installer and follow the on-screen prompts
4. When installation finishes, launch **GlassDeck** from the Start menu or the desktop shortcut

The desktop app is free.

### Desktop App (Linux)

1. Go to the [GlassDeck Releases](https://github.com/DreamGlyphStudios/GlassDeck-Releases/releases) page
2. Download the `.deb` package (for Ubuntu/Debian) or the `.AppImage` (for any Linux distribution)
3. Install:
   - **Deb**: `sudo dpkg -i glassdeck_*.deb` — then launch from your application menu
   - **AppImage**: `chmod +x GlassDeck_*.AppImage` — then double-click or run it from the terminal
4. The WebSocket server starts automatically when you launch GlassDeck

The desktop app is free.

### Mobile App (Android)

Available on the Google Play Store (coming soon). Search for **GlassDeck** by DreamGlyph Studios.

### Mobile App (iOS)

Available on the Apple App Store (coming soon). Search for **GlassDeck** by DreamGlyph Studios.

---

## First-Time Setup

When you first launch the desktop app:

1. **Windows Firewall** — A prompt appears asking to configure a firewall rule so your phone can connect over your local network. Click **Configure** and approve the administrator prompt. If you skip this, you can do it later from **Settings > Network**.

2. **Server starts automatically** — The WebSocket server launches on port 8765 by default. Look for the green status indicator in the bottom bar — this means the server is running and ready for your phone to connect.

3. **Create a profile** — Click **New Profile** to create your first button layout. Choose a name, grid size (columns and rows), and how many pages you want.

> **Tip:** If you're setting up for streaming, start with a 5x3 grid and 2 pages. This gives you 30 button slots, which is plenty for OBS scenes, audio controls, and chat commands.

---

## Pairing Your Phone

Both devices must be on the **same WiFi network**. If your desktop is connected via Ethernet, that works too — as long as both devices are on the same local network.

### Automatic Discovery (mDNS)

This is the easiest method and works on most home networks:

1. Open the GlassDeck mobile app on your phone
2. The app automatically searches for your desktop on the network
3. If found, your desktop appears in the server list with its name
4. Tap it to connect
5. Your button layout loads automatically on the phone

### QR Code Pairing

If automatic discovery doesn't find your desktop:

1. On the desktop app, go to the **Devices** tab
2. A QR code is displayed on screen
3. On the mobile app, tap **Scan QR Code**
4. Point your phone's camera at the QR code on your monitor
5. The phone connects and receives your button configuration automatically

### Manual Connection

If neither method works (common with some routers, guest networks, or VLANs):

1. On your desktop, open a **Command Prompt** (press `Win + R`, type `cmd`, press Enter)
2. Type `ipconfig` and press Enter
3. Find the line that says **IPv4 Address** — it will look like `192.168.1.XXX` or `10.0.0.XXX`
4. On the mobile app, tap **Manual Connect**
5. Enter the IP address from step 3 and the port (default: **8765**)
6. Tap **Connect**

> **Tip:** If you have multiple network adapters listed in `ipconfig`, look for the one under "Wireless LAN adapter Wi-Fi" or "Ethernet adapter Ethernet" — whichever matches how your desktop connects to your router.

---

## Creating Your First Profile

1. Go to the **Profiles** page on the desktop app
2. Click **New Profile**
3. Enter a name (e.g., "Streaming", "Productivity", "Music")
4. Set the **grid size** — columns and rows determine how many buttons fit on screen
   - **5 columns x 3 rows** = 15 buttons per page (good for most uses)
   - **4 columns x 2 rows** = 8 buttons per page (larger buttons, easier to tap)
   - **8 columns x 4 rows** = 32 buttons per page (small buttons, more options)
5. Set the **page count** — each page is a separate screen of buttons you can swipe between
6. Click **Create**

The new profile opens in the deck editor where you can start adding buttons.

---

## Working with Buttons

### Adding a Button

1. Click any empty cell in the grid
2. The button editor panel opens on the right side
3. Configure the button:
   - **Label** — The text shown on the button (optional)
   - **Label Size** — Font size in pixels
   - **Label Color** — Pick a color for the label text
   - **Label Position** — Where the label appears: top, center, or bottom of the button
   - **Icon** — Choose from the built-in library (1500+ icons), upload a custom image, or use an animated GIF
   - **Background Color** — The button's fill color
4. Add one or more **actions** (see [Actions Reference](#actions-reference))
5. Changes save automatically and push to connected phones in real time

### Editing a Button

Click any existing button to select it and open the editor panel.

### Moving Buttons

Drag and drop buttons to rearrange them. Dropping a button on an occupied cell swaps the two buttons.

### Custom Icons

- **Icon Library** — Browse 1500+ built-in icons by name. Type keywords like "microphone", "camera", or "play" to filter.
- **Image Upload** — Upload any PNG, JPG, or GIF. An image cropper lets you resize and position the image before applying it.
- **Animated GIFs** — Uploaded GIFs retain their animation on both desktop and mobile.

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
| **Set Variable** | Sets a user-defined variable to a value (see [Dynamic Labels & Variables](#dynamic-labels--variables)) |
| **If Variable** | Conditionally runs actions based on a variable's value |
| **Delay** | Waits a specified number of milliseconds (used in multi-action sequences) |

### Integration Actions

These appear in the action picker only when the corresponding integration is enabled and connected. See [Integrations](#integrations) for setup instructions.

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

**Example — "Go Live" button:**
1. Switch OBS to the "Live" scene
2. Wait 1 second (Delay: 1000ms)
3. Send a Twitch chat message: "We're live!"
4. Set Elgato Key Light to full brightness

**Example — "End Stream" button:**
1. Send Twitch chat message: "Thanks for watching! See you next time."
2. Wait 2 seconds (Delay: 2000ms)
3. Switch OBS to "Outro" scene
4. Wait 10 seconds (Delay: 10000ms)
5. Stop OBS streaming

---

## Toggle Buttons

Toggle buttons have two states, each with its own set of actions.

1. Select a button and enable **Toggle** in the editor
2. Configure **State 1 Actions** (what happens on the first press)
3. Configure **State 2 Actions** (what happens on the second press)
4. The button alternates between states on each press

**Example — Mute/Unmute button:**
- State 1: Send `Ctrl+M` to mute, change icon to muted microphone
- State 2: Send `Ctrl+M` to unmute, change icon to active microphone

**Example — Stream Start/Stop:**
- State 1: Start OBS streaming, change button color to red, change label to "Stop Stream"
- State 2: Stop OBS streaming, change button color to green, change label to "Go Live"

---

## Button Folders

Organize buttons into folders for hierarchical navigation.

1. Create a button and set it as a **Folder** in the editor
2. Click the folder button to navigate into it — you'll see an empty grid
3. Add buttons inside the folder just like the main grid
4. A **Back** button automatically appears to return to the parent level

Folders work on both desktop and mobile. They're useful for grouping related actions — for example, a "Lights" folder containing individual buttons for each Philips Hue light.

---

## Sliders

Slider buttons add a draggable slider control to a grid cell on your mobile device. Use them for smooth, continuous control of things like volume, brightness, or opacity.

### Creating a Slider Button

1. Select a button in the deck editor
2. Enable **Slider Mode** using the toggle in the button editor
3. Configure slider settings:
   - **Min** — The minimum value (default: 0)
   - **Max** — The maximum value (default: 100)
   - **Step** — How much the value changes per increment (default: 1)
   - **Orientation** — Horizontal or vertical
4. Add an action to the button — the action executes as you drag the slider

### How Sliders Work

On the mobile app, slider buttons display as a draggable slider instead of a tappable button. As you drag, the current value is sent to the desktop app up to 10 times per second (throttled to avoid flooding).

The slider value is available in dynamic labels using `{{slider_value}}` — for example, a label of `Vol: {{slider_value}}%` updates in real time as you drag.

### Example Uses

- **Spotify volume** — Add a Spotify Set Volume action to a slider button (min 0, max 100)
- **Hue brightness** — Add a Hue Set Brightness action with a 0-254 range
- **Key Light temperature** — Vertical slider from warm (2900K) to cool (7000K)
- **OBS audio** — Control source volume with a horizontal fader

> **Tip:** Vertical sliders work well for volume faders. Set the orientation to vertical and place them in a narrow column for a mixer-style layout.

---

## Dynamic Labels & Variables

Dynamic labels let button text update automatically based on variables, counters, or live integration data. Instead of a static label like "Volume", you can show `Vol: {{var.volume}}%` which updates in real time.

### Variables

Variables are named values you create and modify with button actions. They persist across button presses and app restarts.

**Creating variables:**

Variables are created automatically when you use a **Set Variable** action. You can also manage them from the desktop app (they're stored in the database).

**Using Set Variable actions:**

1. Add a **Set Variable** action to a button
2. Enter a **Variable Name** (e.g., `scene_mode`)
3. Choose an **Operation**:
   - **Set** — Set to a specific value
   - **Increment** — Add a number to the current value
   - **Decrement** — Subtract a number from the current value
   - **Toggle** — Switch between "true" and "false"
4. Enter a **Value** (for set/increment/decrement operations)

**Using If Variable actions:**

1. Add an **If Variable** action to a button
2. Enter the **Variable Name** to check
3. Choose an **Operator** (equals, not equals, greater than, less than, contains)
4. Enter the **Value** to compare against
5. Configure **Then Actions** (run when the condition is true)
6. Configure **Else Actions** (run when the condition is false)

### Dynamic Label Syntax

Set a button's **Dynamic Label** to a template string. Templates use `{{namespace.key}}` syntax:

| Template | What It Shows |
|---|---|
| `{{var.scene_mode}}` | The value of a variable named `scene_mode` |
| `{{counter.deaths}}` | The current value of a counter named `deaths` |
| `{{obs.current_scene}}` | The current OBS scene name (see [Live State Feedback](#live-state-feedback)) |
| `{{spotify.track}}` | The currently playing Spotify track |

You can mix template tags with static text:

- `Mode: {{var.scene_mode}}` → "Mode: gaming"
- `Deaths: {{counter.deaths}}` → "Deaths: 42"
- `Now Playing: {{spotify.track}}` → "Now Playing: Bohemian Rhapsody"

Dynamic labels update on both the desktop preview and the mobile app.

> **Tip:** If a variable doesn't exist yet, the template resolves to an empty string. Create your variables with **Set Variable** actions before relying on them in labels.

---

## Live State Feedback

GlassDeck polls your connected integrations every few seconds and makes their current state available in dynamic labels. This means your buttons can show live information like the current OBS scene, what song is playing on Spotify, or which Hue lights are on — without pressing anything.

### Supported Integrations

| Integration | Available Values | Example Template |
|---|---|---|
| **OBS Studio** | `current_scene`, `streaming`, `recording` | `{{obs.current_scene}}` |
| **Spotify** | `track`, `artist`, `album`, `playing` | `{{spotify.track}} - {{spotify.artist}}` |
| **Philips Hue** | `light_count`, `lights_on`, per-light on/off and brightness | `{{hue.desk_lamp}}`, `{{hue.desk_lamp_brightness}}` |

### How It Works

1. Make sure the integration is **connected** (green status indicator on the Integrations page)
2. GlassDeck automatically polls the integration in the background
3. Set a button's **Dynamic Label** using the template syntax above
4. The label updates live on both desktop and mobile

### Example: "Now Playing" Button

1. Create a button with a music icon
2. Set the **Dynamic Label** to: `{{spotify.track}}`
3. Add a **Spotify Play/Pause** action
4. The button now shows the current track name and toggles playback when pressed

### Example: "Current Scene" Indicator

1. Create a button with a camera icon
2. Set the **Dynamic Label** to: `{{obs.current_scene}}`
3. No action needed — this button just displays the current OBS scene
4. The label updates automatically whenever you switch scenes (from OBS or from another button)

### Notes

- Polling runs every 3 seconds, so there may be a brief delay before labels update
- If an integration is disconnected, its template values resolve to empty strings
- Hue light names are normalized in templates: spaces become underscores and names are lowercase (e.g., "Desk Lamp" becomes `{{hue.desk_lamp}}`)

---

## Canvas Backgrounds

Set a single image that spans the entire button grid, appearing behind all buttons.

1. Go to the profile settings (gear icon in the deck editor)
2. Click **Canvas Background**
3. Upload an image (PNG, JPG)
4. The image stretches across the full grid area
5. Set button backgrounds to transparent or semi-transparent to let the canvas show through

Canvas backgrounds sync to connected mobile devices.

> **Tip:** Use a dark, low-contrast image so button labels remain readable. An image resolution of 1920x1080 works well for most grid sizes.

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

> **Tip:** To find the process name of an application, open **Task Manager** (Ctrl+Shift+Esc), right-click the app in the Processes tab, and look at the process name (e.g., `obs64.exe`, `chrome.exe`, `Code.exe`).

### Import & Export

- **Export**: Right-click a profile and select **Export** to save it as an `.scprofile` file
- **Import**: Click **Import Profile** and select an `.scprofile` file

---

## Integrations

Integrations connect GlassDeck to external software and hardware. All integrations are configured on the desktop app under the **Integrations** page.

Each integration section below includes:
- What it does and why you'd want it
- Prerequisites (what you need before starting)
- Step-by-step setup instructions
- How to test that it's working
- Available actions
- Troubleshooting tips

---

### OBS Studio

Control OBS Studio directly from your macro board — switch scenes, toggle sources, and start/stop streaming and recording without touching OBS.

#### Prerequisites

- OBS Studio version **28 or newer** (ships with WebSocket v5 built in)
- OBS must be running on the **same computer** as the GlassDeck desktop app
- If you use an older OBS version (below 28), install the [obs-websocket plugin](https://github.com/obsproject/obs-websocket/releases) separately

#### Step-by-Step Setup

**Step 1 — Enable the WebSocket server in OBS:**

1. Open **OBS Studio**
2. Click the **Tools** menu at the top
3. Click **WebSocket Server Settings**
4. You'll see a settings panel. Check the box that says **Enable WebSocket server**
5. The **Server Port** defaults to **4455** — leave this as-is unless you have a conflict
6. **Server Password**: You can optionally set a password for security. If you do, write it down — you'll need it in the next step. If you're the only person on your network, leaving it blank is fine.
7. Click **Apply** (or **OK**)

> **What you should see:** At the bottom of the WebSocket settings panel, it should say "Server Status: Listening" or similar. This means OBS is ready to accept connections.

**Step 2 — Connect GlassDeck to OBS:**

1. Open the **GlassDeck** desktop app
2. Go to the **Integrations** page (icon in the left sidebar)
3. Find **OBS Studio** in the list and click it
4. You'll see three fields:
   - **Host**: Enter `localhost` (this means "this computer")
   - **Port**: Enter `4455` (or whatever port you set in OBS)
   - **Password**: Enter the password you set in OBS, or leave it blank if you didn't set one
5. Click **Connect**

> **What you should see:** The status indicator next to OBS Studio should turn green, showing "Connected". If it stays red, see Troubleshooting below.

**Step 3 — Test it:**

1. Go to the **Deck Editor** (click on a profile)
2. Click an empty button cell
3. Click **Add Action**
4. In the action picker, you should now see an **OBS Studio** section
5. Select **Switch Scene** and choose one of your OBS scenes from the dropdown
6. Save the button, then press it — OBS should switch to that scene

#### Available Actions

| Action | What It Does |
|---|---|
| **Switch Scene** | Switches to a specific OBS scene |
| **Toggle Source Visibility** | Shows or hides a specific source within a scene |
| **Start Streaming** | Starts the OBS stream output |
| **Stop Streaming** | Stops the OBS stream output |
| **Start Recording** | Starts recording |
| **Stop Recording** | Stops recording |

#### Troubleshooting

- **"Connection refused"**: Make sure OBS is running and the WebSocket server is enabled. Double-check the port number.
- **"Authentication failed"**: The password in GlassDeck doesn't match the one in OBS. Re-enter it carefully.
- **Actions do nothing**: Make sure OBS is the correct version (28+). Older versions need the separate obs-websocket plugin.
- **Scenes not appearing in dropdown**: Disconnect and reconnect the integration. GlassDeck fetches the scene list when it first connects.

---

### Twitch

Send chat messages, create clips, run ads, and add stream markers on your Twitch channel — all from a button press.

#### Prerequisites

- A **Twitch account** (the account you stream from)
- You must be a **Twitch Affiliate or Partner** to run ads (chat messages and clips work for all accounts)

#### Step-by-Step Setup

**Step 1 — Register a Twitch application (one-time setup):**

GlassDeck needs a Twitch Application to authenticate with your account. This is a standard process that Twitch requires for any third-party tool.

1. Open your web browser and go to **https://dev.twitch.tv/console**
2. Log in with your Twitch account if you aren't already
3. Click **Register Your Application** (or **Applications** in the left menu, then **Register**)
4. Fill in the form:
   - **Name**: Enter `GlassDeck` (or any name you like — this is just for your reference)
   - **OAuth Redirect URLs**: Enter `http://localhost:8765/auth/twitch/callback`
     - Click **Add** after entering the URL
   - **Category**: Select **Application Integration**
   - **Client Type**: Select **Confidential**
5. Complete the CAPTCHA and click **Create**
6. You'll be taken to your application's settings page
7. You'll see a **Client ID** — copy this (click the copy icon or select and Ctrl+C)
8. Click **New Secret** to generate a **Client Secret** — copy this too

> **Important:** Keep the Client Secret private. Don't share it or post it publicly.

**Step 2 — Enter credentials in GlassDeck:**

1. Open the **GlassDeck** desktop app
2. Go to **Integrations > Twitch**
3. Paste the **Client ID** from step 7
4. Paste the **Client Secret** from step 8
5. Click **Authorize with Twitch**
6. A browser window opens asking you to log in to Twitch and grant permissions
7. Review the permissions and click **Authorize**
8. The browser will redirect back to GlassDeck and close automatically

> **What you should see:** The Twitch integration shows "Connected" with your Twitch username displayed. GlassDeck stores the token securely and will refresh it automatically when it expires.

**Step 3 — Test it:**

1. Open the Deck Editor and click an empty button
2. Add an action — look for the **Twitch** section
3. Select **Send Chat Message**
4. Type a test message like "Hello from GlassDeck!"
5. Press the button — the message should appear in your Twitch chat

#### Permissions Explained

When you authorize, Twitch asks you to grant specific permissions (called "scopes"). Here's what each one does:

| Permission | Why GlassDeck Needs It |
|---|---|
| **chat:edit** | Send messages in your chat |
| **chat:read** | Read messages from your chat |
| **clips:edit** | Create clips from your stream |
| **channel:manage:broadcast** | Update your stream title, game, and tags |
| **channel:edit:commercial** | Run ads on your channel |
| **channel:manage:ads** | Manage ad schedules |

#### Available Actions

| Action | What It Does |
|---|---|
| **Send Chat Message** | Posts a message in your Twitch chat |
| **Create Clip** | Creates a 30-second clip of the current stream moment |
| **Run Ad** | Starts a commercial break (30/60/90/120/150/180 seconds) |
| **Add Stream Marker** | Places a marker in your VOD for easy editing later |

#### Troubleshooting

- **"Invalid Client ID"**: Make sure you copied the entire Client ID from the Twitch Developer Console without extra spaces.
- **"Redirect URI mismatch"**: The redirect URL in Twitch must exactly match `http://localhost:8765/auth/twitch/callback`. Check for typos.
- **Authorization window doesn't close**: Manually close the browser tab and check GlassDeck — it may have already received the token.
- **Chat messages not sending**: Make sure you authorized with the account that owns (or is a moderator of) the channel you're chatting in.
- **Token expired**: Click **Re-authorize** in the Twitch integration settings. Tokens expire periodically and GlassDeck usually refreshes them automatically, but sometimes a manual re-auth is needed.

---

### YouTube

Send live chat messages, control your YouTube stream, and update your stream title — all from your macro board.

#### Prerequisites

- A **Google account** with a YouTube channel
- Your YouTube channel must have **live streaming enabled** (go to YouTube Studio > Go Live; if you haven't streamed before, YouTube may require a 24-hour wait after your first request)

#### Step-by-Step Setup

**Step 1 — Create a Google Cloud project (one-time setup):**

This sounds technical, but it's just a few clicks. Google requires this for any app that connects to YouTube.

1. Open your browser and go to **https://console.cloud.google.com**
2. Log in with the Google account that owns your YouTube channel
3. At the top of the page, click the project dropdown (it may say "Select a project" or show a project name)
4. In the popup, click **New Project** (top right)
5. Enter a project name: `GlassDeck` (or anything you like)
6. Leave the organization as-is (or select your organization if you have one)
7. Click **Create**
8. Wait a few seconds for the project to be created, then select it from the project dropdown

**Step 2 — Enable the YouTube Data API:**

1. In the Google Cloud Console, click the **hamburger menu** (three horizontal lines, top left)
2. Navigate to **APIs & Services > Library**
3. In the search bar, type **YouTube Data API v3**
4. Click on **YouTube Data API v3** in the results
5. Click the blue **Enable** button
6. Wait for it to activate (a few seconds)

> **What you should see:** The page changes to show the API dashboard with "API Enabled" status.

**Step 3 — Configure the OAuth consent screen:**

1. In the left sidebar, click **APIs & Services > OAuth consent screen**
2. Select **External** as the user type and click **Create**
3. Fill in the required fields:
   - **App name**: `GlassDeck`
   - **User support email**: Select your email from the dropdown
   - **Developer contact information**: Enter your email address
4. Click **Save and Continue**
5. On the **Scopes** page, click **Add or Remove Scopes**
6. Search for and check these scopes:
   - `https://www.googleapis.com/auth/youtube` (Manage your YouTube account)
   - `https://www.googleapis.com/auth/youtube.force-ssl` (Manage YouTube videos)
7. Click **Update**, then **Save and Continue**
8. On the **Test users** page, click **Add Users** and enter your own Gmail address
9. Click **Save and Continue**, then **Back to Dashboard**

> **Note:** While your app is in "Testing" status, only the test users you added can authorize. This is fine — you only need your own account.

**Step 4 — Create OAuth credentials:**

1. In the left sidebar, click **APIs & Services > Credentials**
2. Click **+ Create Credentials** at the top
3. Select **OAuth client ID**
4. For **Application type**, select **Web application**
5. Give it a name: `GlassDeck Desktop`
6. Under **Authorized redirect URIs**, click **+ Add URI**
7. Enter: `http://localhost:8765/auth/youtube/callback`
8. Click **Create**
9. A popup shows your **Client ID** and **Client Secret** — copy both of these

> **Important:** Click the **Download JSON** button to save a backup of these credentials. Keep them private.

**Step 5 — Enter credentials in GlassDeck:**

1. Open the **GlassDeck** desktop app
2. Go to **Integrations > YouTube**
3. Paste the **Client ID** from step 9
4. Paste the **Client Secret** from step 9
5. Click **Authorize with Google**
6. A browser window opens for Google login
7. Select your Google account (the one with your YouTube channel)
8. You may see a "This app isn't verified" warning — click **Advanced**, then **Go to GlassDeck (unsafe)**. This warning appears because your app is in testing mode; it's safe since you created the app yourself.
9. Grant the requested permissions and click **Allow**
10. The browser redirects back to GlassDeck

> **What you should see:** The YouTube integration shows "Connected" with your channel name.

**Step 6 — Test it:**

1. Start a YouTube live stream (or have one running)
2. In the Deck Editor, add a button with the **YouTube > Send Chat Message** action
3. Type a test message and press the button
4. The message should appear in your live chat

#### Available Actions

| Action | What It Does |
|---|---|
| **Send Chat Message** | Posts a message in your YouTube live chat |
| **Start Stream** | Transitions your YouTube broadcast to "live" |
| **Stop Stream** | Ends your YouTube live broadcast |
| **Set Stream Title** | Updates the title of your current or next live stream |

#### Troubleshooting

- **"Access blocked" during authorization**: Make sure you added your email as a test user in the OAuth consent screen settings.
- **"This app isn't verified" warning**: This is normal for testing mode. Click Advanced > Go to GlassDeck. It's safe because you created the app yourself.
- **"YouTube Data API has not been used" error**: Go back to the Google Cloud Console and make sure the YouTube Data API v3 is enabled.
- **Chat messages not appearing**: You must have an active live stream running. YouTube chat actions only work during a live broadcast.
- **Quota exceeded**: The YouTube API has daily usage limits. Normal usage won't hit these, but if you send hundreds of chat messages rapidly, you may be temporarily rate-limited.

---

### Spotify

Control your Spotify playback — play, pause, skip tracks, and adjust volume from your macro board.

#### Prerequisites

- A **Spotify account** (free accounts can browse, but **Spotify Premium** is required for playback control — play, pause, skip, volume)
- **Spotify must be open and playing** on any device linked to your account for playback controls to work

#### Step-by-Step Setup

**Step 1 — Create a Spotify app (one-time setup):**

1. Open your browser and go to **https://developer.spotify.com/dashboard**
2. Log in with your Spotify account
3. Click **Create App** (or **Create an App**)
4. Fill in the form:
   - **App name**: `GlassDeck`
   - **App description**: `Macro board for Spotify control` (anything is fine)
   - **Redirect URIs**: Enter `http://localhost:8765/auth/spotify/callback` and click **Add**
   - **Which API/SDKs are you planning to use?**: Check **Web API**
5. Check the box agreeing to Spotify's terms of service
6. Click **Save**
7. On the app's dashboard page, you'll see the **Client ID** — click **Show Client ID** and copy it

> **Note:** You do NOT need a Client Secret. GlassDeck uses the PKCE (Proof Key for Code Exchange) authentication method, which is more secure and doesn't require a secret.

**Step 2 — Connect GlassDeck to Spotify:**

1. Open the **GlassDeck** desktop app
2. Go to **Integrations > Spotify**
3. Paste the **Client ID** from step 7
4. Click **Connect to Spotify**
5. A browser window opens asking you to log in to Spotify
6. Review the permissions and click **Agree**
7. The browser redirects back to GlassDeck

> **What you should see:** The Spotify integration shows "Connected" with your Spotify display name.

**Step 3 — Test it:**

1. Open Spotify on your computer (or phone, or any device on your account) and start playing a song
2. In the Deck Editor, add a button with the **Spotify > Next Track** action
3. Press the button — the song should skip to the next track

> **Important:** Spotify must be actively playing on some device. If nothing is playing, playback commands have nothing to control. Start a song first, then use your buttons.

#### Available Actions

| Action | What It Does |
|---|---|
| **Play/Pause** | Toggles playback on/off |
| **Next Track** | Skips to the next song in the queue |
| **Previous Track** | Goes back to the previous song |
| **Set Volume** | Sets playback volume to a specific percentage (0-100%) |

#### Troubleshooting

- **"Invalid Client ID"**: Make sure you copied the full Client ID without extra spaces. It should be a long string of letters and numbers.
- **"INVALID_CLIENT: Invalid redirect URI"**: The redirect URI in Spotify must exactly match `http://localhost:8765/auth/spotify/callback`. Go back to the Spotify Developer Dashboard, click your app, click **Settings**, and verify the redirect URI.
- **Playback controls do nothing**: Spotify must be actively playing on a device. Open Spotify, start a song, then try again.
- **"Premium required" error**: Free Spotify accounts cannot control playback. You need Spotify Premium for play/pause, skip, and volume actions.
- **Token expired**: Click **Reconnect** in the Spotify integration settings. Tokens usually refresh automatically.

---

### Elgato Key Light

Control your Elgato Key Light or Key Light Air — toggle it on/off, adjust brightness, and change color temperature.

#### Prerequisites

- An **Elgato Key Light**, **Key Light Air**, or **Key Light Mini** connected to your WiFi network
- The **Elgato Control Center** app installed on your computer (useful for finding the light's IP address, but not required for GlassDeck to work)
- Your light and desktop must be on the **same local network**

#### Step-by-Step Setup

**Step 1 — Find your Key Light's IP address:**

There are two ways to find it:

**Option A — Using Elgato Control Center:**
1. Open the **Elgato Control Center** app on your computer
2. Your light should appear in the list
3. Click the gear icon next to the light
4. The IP address is shown in the settings (it looks like `192.168.1.XXX`)
5. Write this down

**Option B — Using your router:**
1. Log in to your router's admin page (usually `192.168.1.1` or `192.168.0.1` in your browser)
2. Look for the connected devices / DHCP client list
3. Find the device named "Elgato Key Light" (or similar)
4. Note its IP address

**Step 2 — Connect GlassDeck to the Key Light:**

1. Open the **GlassDeck** desktop app
2. Go to **Integrations > Elgato Key Light**
3. Enter the **IP address** from step 1
4. The port is **9123** (this is hardcoded in all Elgato lights — you don't need to change it)
5. Click **Connect**

> **What you should see:** The integration shows "Connected" and may display the light's current state (on/off, brightness level).

**Step 3 — Test it:**

1. In the Deck Editor, add a button with the **Elgato Key Light > Toggle On/Off** action
2. Press the button — your Key Light should turn on or off

#### Available Actions

| Action | What It Does |
|---|---|
| **Toggle On/Off** | Switches the light on or off |
| **Set Brightness** | Sets brightness to a specific percentage (0-100%) |
| **Set Color Temperature** | Sets the color temperature (warm to cool, measured in Kelvin) |

#### Troubleshooting

- **"Connection timed out"**: Make sure the IP address is correct and the light is powered on and connected to WiFi. Try pinging the IP from a command prompt: `ping 192.168.1.XXX`
- **Light doesn't respond**: Some routers assign new IP addresses when devices reconnect. Check if the IP has changed by looking in Elgato Control Center or your router's device list again.
- **Multiple lights**: Add a separate integration instance for each light. Each one needs its own IP address.

> **Tip:** Set a static IP for your Key Light in your router's DHCP settings. This prevents the IP from changing and breaking the connection.

---

### Discord

Toggle mute and deafen in Discord from your macro board. This integration works by sending the same keyboard shortcuts that Discord uses for mute/deafen.

#### Prerequisites

- **Discord** desktop app installed and running
- Discord must have keyboard shortcuts configured for mute and deafen

#### Step-by-Step Setup

**Step 1 — Set up Discord keyboard shortcuts:**

1. Open **Discord**
2. Click the **gear icon** (User Settings) next to your username at the bottom left
3. In the left sidebar, scroll down and click **Keybinds**
4. Click **Add a Keybind**
5. Set the following:
   - **Action**: Toggle Mute
   - **Keybind**: Press `Ctrl+Shift+M` (or any shortcut you prefer)
6. Click **Add a Keybind** again
7. Set:
   - **Action**: Toggle Deafen
   - **Keybind**: Press `Ctrl+Shift+D` (or any shortcut you prefer)
8. Click **Save Changes** (or the changes save automatically)

> **Important:** Remember the exact key combinations you chose. GlassDeck will send these same shortcuts.

**Step 2 — Enable in GlassDeck:**

1. Open the **GlassDeck** desktop app
2. Go to **Integrations > Discord**
3. Toggle the integration **on**
4. The default shortcuts are `Ctrl+Shift+M` (mute) and `Ctrl+Shift+D` (deafen). If you used different shortcuts in Discord, update them here to match.

**Step 3 — Test it:**

1. Open Discord and join a voice channel
2. In the Deck Editor, add a button with the **Discord > Toggle Mute** action
3. Press the button — your microphone in Discord should mute/unmute

> **Note:** Discord does NOT need to be the active (foreground) window. As long as Discord is running, it listens for global keyboard shortcuts in the background.

#### Available Actions

| Action | What It Does |
|---|---|
| **Toggle Mute** | Mutes/unmutes your microphone in Discord |
| **Toggle Deafen** | Deafens/undeafens (mutes all audio) in Discord |

#### Troubleshooting

- **Nothing happens when pressing the button**: Make sure the keyboard shortcuts in GlassDeck match exactly what you set in Discord's Keybinds settings.
- **Works sometimes, not always**: Some applications can intercept global shortcuts before Discord gets them. Try a different key combination that isn't used by other running applications.
- **Using Discord in browser**: Browser-based Discord doesn't support global keyboard shortcuts. You need the Discord desktop app.

---

### Philips Hue

Control your Philips Hue smart lights — toggle them on/off, change brightness, set colors, and activate scenes.

#### Prerequisites

- A **Philips Hue Bridge** (the square device that connects to your router via Ethernet)
- One or more **Philips Hue lights** set up through the Hue app
- The Hue Bridge and your desktop must be on the **same local network**

#### Step-by-Step Setup

**Step 1 — Discover and pair with your Hue Bridge:**

1. Open the **GlassDeck** desktop app
2. Go to **Integrations > Philips Hue**
3. Click **Discover Bridge**
4. GlassDeck searches your network for Hue Bridges. This usually takes a few seconds.

> **What you should see:** A message saying "Hue Bridge found at 192.168.x.x" with a **Pair** button.

5. **Before clicking Pair**: Walk over to your Hue Bridge (the physical device) and **press the large button on top of it**
6. Within **30 seconds** of pressing the physical button, click **Pair** in GlassDeck
7. The pairing completes and GlassDeck retrieves your lights and scenes

> **Why the physical button?** This is Philips Hue's security measure. It ensures that only someone with physical access to the bridge can grant control. You only need to do this once.

> **What you should see:** The integration shows "Connected" and lists your lights, rooms, and scenes.

**Step 2 — Test it:**

1. In the Deck Editor, add a button with the **Philips Hue > Toggle Light** action
2. Select one of your lights from the dropdown
3. Press the button — the light should turn on or off

#### Available Actions

| Action | What It Does |
|---|---|
| **Toggle Light** | Turns a specific light on or off |
| **Set Brightness** | Sets a light's brightness (0-100%) |
| **Set Color** | Sets a light's color (using a color picker) |
| **Activate Scene** | Activates a Hue scene (pre-configured light states you've set in the Hue app) |

#### Troubleshooting

- **"No Hue Bridge found"**: Make sure the bridge is powered on and connected to your router via Ethernet. The green lights on the bridge should be on.
- **Pairing fails**: You must press the physical button on the bridge and then click Pair within 30 seconds. If you're too slow, try again.
- **Lights don't show up**: If you recently added new lights in the Hue app, disconnect and reconnect the GlassDeck integration to refresh the light list.
- **"Bridge not found" after it worked before**: Your bridge may have gotten a new IP address from your router. Click **Discover Bridge** again to find the new IP.

> **Tip:** Set a static IP for your Hue Bridge in your router's DHCP settings to prevent the IP from changing.

---

### Home Assistant

Control any device in your Home Assistant setup — toggle lights, switches, locks, fans, media players, run automations, and call any service.

#### Prerequisites

- A running **Home Assistant** instance (on a Raspberry Pi, VM, or any server)
- Your Home Assistant instance must be accessible from your desktop's network
- You need a **Long-Lived Access Token** (created in Home Assistant)

#### Step-by-Step Setup

**Step 1 — Get your Home Assistant URL:**

Your Home Assistant URL depends on how you set it up:

- **Local access**: Usually `http://192.168.1.XXX:8123` (replace XXX with your HA device's IP)
- **Home Assistant Cloud (Nabu Casa)**: Your remote URL like `https://xxxxxxxx.ui.nabu.casa`
- **Custom domain**: Whatever domain you configured

> **Tip:** Open your browser and go to your Home Assistant dashboard to verify the URL. The address in the browser bar is what you'll enter in GlassDeck.

**Step 2 — Create a Long-Lived Access Token:**

1. Open your **Home Assistant** dashboard in a browser
2. Click your **profile icon** (bottom left of the sidebar — it may show your initials or a person icon)
3. Scroll down to the **Long-Lived Access Tokens** section
4. Click **Create Token**
5. Enter a name: `GlassDeck`
6. Click **OK**
7. A long token string appears — **copy it immediately**. You will NOT be able to see it again after closing this dialog.

> **Important:** Copy the token right away and paste it somewhere safe (or directly into GlassDeck). If you lose it, you'll need to delete it and create a new one.

**Step 3 — Connect GlassDeck to Home Assistant:**

1. Open the **GlassDeck** desktop app
2. Go to **Integrations > Home Assistant**
3. Enter the **URL** from step 1 (e.g., `http://192.168.1.50:8123`)
4. Paste the **Long-Lived Access Token** from step 7
5. Click **Connect**

> **What you should see:** The integration shows "Connected" and may list your entities (lights, switches, automations, etc.).

**Step 4 — Test it:**

1. In the Deck Editor, add a button with the **Home Assistant > Toggle Entity** action
2. Select a light or switch entity from the list
3. Press the button — the device should toggle on or off

#### Available Actions

| Action | What It Does |
|---|---|
| **Toggle Entity** | Toggles any entity (lights, switches, fans, locks, etc.) on/off |
| **Call Service** | Calls any Home Assistant service with custom data |
| **Set State** | Sets a specific state on an entity |
| **Trigger Automation** | Triggers a Home Assistant automation to run |

#### Troubleshooting

- **"Connection refused"**: Make sure the URL is correct and includes the port (`:8123`). Try opening the URL in your browser to verify it works.
- **"401 Unauthorized"**: The access token is wrong or expired. Create a new Long-Lived Access Token in your Home Assistant profile.
- **Entities not appearing**: Some entities may take a moment to load. Disconnect and reconnect the integration, or wait a few seconds after connecting.
- **"Cannot connect" from outside your home network**: If you're trying to connect remotely, make sure you have a way to access Home Assistant externally (Nabu Casa, VPN, or port forwarding).

---

### vMix

Control vMix video production software — switch inputs, manage streaming/recording, and adjust audio levels.

#### Prerequisites

- **vMix** installed and running on the same computer (or a computer accessible on your network)
- The vMix **Web Controller** must be enabled

#### Step-by-Step Setup

**Step 1 — Enable the vMix Web Controller:**

1. Open **vMix**
2. Click **Settings** (gear icon, bottom right)
3. Go to the **Web Controller** tab
4. Check **Enable Web Controller**
5. Note the **port number** — the default is **8088**
6. Click **OK**

**Step 2 — Connect GlassDeck:**

1. Open the **GlassDeck** desktop app
2. Go to **Integrations > vMix**
3. Enter the **Host**: `localhost` (or the IP address if vMix is on another computer)
4. Enter the **Port**: `8088` (or whatever port vMix showed)
5. Click **Connect**

> **What you should see:** The integration shows "Connected".

**Step 3 — Test it:**

1. In the Deck Editor, add a button with a **vMix > Switch Input** action
2. Select an input from the dropdown
3. Press the button — vMix should switch to that input

#### Available Actions

| Action | What It Does |
|---|---|
| **Switch Input** | Transitions to a specific input |
| **Start/Stop Streaming** | Controls the stream output |
| **Start/Stop Recording** | Controls recording |
| **Adjust Audio** | Sets volume levels for inputs |

#### Troubleshooting

- **"Connection refused"**: Make sure the Web Controller is enabled in vMix settings.
- **Can't connect from another computer**: Make sure the Windows Firewall allows connections on port 8088 from your local network.

---

### Streamlabs

Control Streamlabs Desktop — switch scenes, toggle sources, and manage your stream.

#### Prerequisites

- **Streamlabs Desktop** installed and running
- A Streamlabs account

#### Step-by-Step Setup

**Step 1 — Get your Streamlabs API token:**

1. Open your browser and go to **https://streamlabs.com/dashboard**
2. Log in with your Streamlabs account
3. Click **Settings** (gear icon, left sidebar)
4. Go to **API Settings** (or **API Tokens**)
5. Copy your **API Token** (sometimes called "Socket API Token")

> **Note:** If you don't see an API token option, look under **Account > API** or check the developer section of your Streamlabs dashboard.

**Step 2 — Connect GlassDeck:**

1. Open the **GlassDeck** desktop app
2. Go to **Integrations > Streamlabs**
3. Paste the **API Token** from step 5
4. Click **Connect**

> **What you should see:** The integration shows "Connected".

**Step 3 — Test it:**

1. In the Deck Editor, add a button with a **Streamlabs** action
2. Press the button to verify it works

#### Available Actions

| Action | What It Does |
|---|---|
| **Switch Scene** | Switches to a specific scene |
| **Toggle Source** | Shows or hides a source |
| **Start/Stop Stream** | Controls streaming |

---

### XSplit Broadcaster

Control XSplit Broadcaster — switch scenes, toggle sources, and manage streaming/recording.

#### Prerequisites

- **XSplit Broadcaster** installed and running
- The XSplit **HTTP API** must be enabled

#### Step-by-Step Setup

**Step 1 — Enable the XSplit HTTP API:**

1. Open **XSplit Broadcaster**
2. Click **Tools** in the menu bar
3. Click **Settings**
4. Go to the **Advanced** tab
5. Find the **HTTP API** section
6. Check **Enable HTTP API**
7. Note the **port** — the default is **8090**
8. Click **Apply** and **OK**

**Step 2 — Connect GlassDeck:**

1. Open the **GlassDeck** desktop app
2. Go to **Integrations > XSplit**
3. Enter the **Host**: `localhost`
4. Enter the **Port**: `8090`
5. Click **Connect**

> **What you should see:** The integration shows "Connected".

**Step 3 — Test it:**

1. Add a button with an **XSplit** action and test it

#### Available Actions

| Action | What It Does |
|---|---|
| **Switch Scene** | Switches to a specific scene |
| **Toggle Source** | Shows or hides a source |
| **Start/Stop Stream** | Controls streaming output |
| **Start/Stop Recording** | Controls recording |

---

### Wirecast

Control Wirecast video production — switch shots, trigger transitions, and manage streaming/recording.

#### Prerequisites

- **Wirecast** installed and running

#### Step-by-Step Setup

Wirecast integration uses keyboard shortcuts to control the application, similar to how the Discord integration works.

1. Open the **GlassDeck** desktop app
2. Go to **Integrations > Wirecast**
3. Toggle the integration **on**
4. The default keyboard shortcuts for Wirecast's common actions are pre-configured

> **Note:** Make sure Wirecast's keyboard shortcut settings match what GlassDeck expects. Check Wirecast's **Preferences > Shortcuts** and GlassDeck's Wirecast integration settings.

#### Available Actions

| Action | What It Does |
|---|---|
| **Switch Shot** | Changes to a specific shot layer |
| **Trigger Transition** | Activates the transition between shots |
| **Toggle Stream** | Starts or stops streaming |
| **Toggle Recording** | Starts or stops recording |

---

### Lightstream

Control Lightstream cloud-based streaming — switch scenes and manage your stream.

#### Prerequisites

- A **Lightstream** account with an active plan
- Access to the Lightstream dashboard

#### Step-by-Step Setup

**Step 1 — Get your Lightstream API key:**

1. Open your browser and go to the **Lightstream dashboard** (log in at **https://app.golightstream.com**)
2. Click your **account settings** or **profile icon**
3. Look for **API Key** or **Developer Settings**
4. Copy your **API Key**

**Step 2 — Connect GlassDeck:**

1. Open the **GlassDeck** desktop app
2. Go to **Integrations > Lightstream**
3. Paste the **API Key**
4. Click **Connect**

#### Available Actions

| Action | What It Does |
|---|---|
| **Switch Scene** | Switches to a specific scene in Lightstream |
| **Start/Stop Stream** | Controls the stream output |

---

### OneStream

Control OneStream multi-streaming — manage your stream and destinations.

#### Prerequisites

- A **OneStream** account
- Access to the OneStream dashboard

#### Step-by-Step Setup

**Step 1 — Get your OneStream API key:**

1. Open your browser and log in to **OneStream** at **https://app.onestream.live**
2. Go to your **Account Settings**
3. Look for **API Access** or **API Key**
4. Copy your **API Key**

**Step 2 — Connect GlassDeck:**

1. Open the **GlassDeck** desktop app
2. Go to **Integrations > OneStream**
3. Paste the **API Key**
4. Click **Connect**

#### Available Actions

| Action | What It Does |
|---|---|
| **Control Stream** | Start/stop your OneStream broadcast |
| **Manage Destinations** | Enable or disable specific streaming destinations |

---

### Restream

Control Restream multi-streaming — manage your stream, channels, and titles.

#### Prerequisites

- A **Restream** account
- Access to the Restream dashboard

#### Step-by-Step Setup

**Step 1 — Get your Restream API key:**

1. Open your browser and log in to **Restream** at **https://app.restream.io**
2. Go to your **Account** or **Settings**
3. Look for **API Access** or **Developer Settings**
4. Copy your **API Key**

**Step 2 — Connect GlassDeck:**

1. Open the **GlassDeck** desktop app
2. Go to **Integrations > Restream**
3. Paste the **API Key**
4. Click **Connect**

#### Available Actions

| Action | What It Does |
|---|---|
| **Control Stream** | Start/stop your Restream broadcast |
| **Manage Channels** | Enable or disable specific streaming channels |
| **Update Title** | Change the stream title across all connected platforms |

---

## Scheduled Actions

Scheduled Actions let you automatically trigger button actions without pressing anything — perfect for recurring tasks, timed reminders, or automated workflows.

### Getting There

Click **Schedules** (clock icon) in the sidebar.

### Schedule Types

| Type | How It Works | Example |
|---|---|---|
| **Interval** | Fires every N seconds | "Refresh OBS stats every 30 seconds" |
| **Cron** | Fires on a cron schedule (6-field: sec min hour day month weekday) | "Every weekday at 9 AM: `0 0 9 * * 1-5`" |
| **One-Time** | Fires once at a specific date/time, then auto-disables | "Remind me at 3:00 PM today" |

### Creating a Schedule

1. Click **New Schedule**
2. Give it a name (e.g., "Hourly scene rotate")
3. Select the **button** to trigger — only buttons with labels are shown, organized by profile
4. Choose the **type** (Interval, Cron, or One-Time) and configure:
   - **Interval:** Set the number of seconds between fires (minimum 5 seconds)
   - **Cron:** Enter a 6-field cron expression (e.g., `0 */5 * * * *` for every 5 minutes)
   - **One-Time:** Pick a date and time (UTC)
5. Click **Create Schedule**

### Managing Schedules

- **Enable/Disable:** Toggle the switch to pause or resume a schedule without deleting it
- **Delete:** Remove a schedule permanently
- **Last Fired:** See when each schedule last triggered

### Notes

- The scheduler checks for due schedules every **10 seconds**, so there may be up to a 10-second delay
- One-time schedules automatically disable after firing
- The linked button's full action sequence runs (including multi-action, conditional logic, etc.)
- Schedules work even if no mobile device is connected

---

## Webhooks

Webhooks let external services trigger your button actions via HTTP. Connect IFTTT, Zapier, Home Assistant automations, shell scripts, or any tool that can send an HTTP request.

### Getting There

Click **Webhooks** (webhook icon) in the sidebar.

### Creating a Webhook

1. Click **New Webhook**
2. Give it a name (e.g., "IFTTT scene trigger")
3. Select the **button** to trigger
4. Optionally set a **Bearer Token** for authentication (a random token is pre-generated for you)
5. Click **Create Webhook**

### Using a Webhook

Each webhook gets a unique URL displayed on the card:

```
POST http://<your-ip>:8766/webhook/<webhook-id>
```

**Without authentication:**
```bash
curl -X POST http://192.168.1.100:8766/webhook/abc-123-def
```

**With authentication:**
```bash
curl -X POST -H "Authorization: Bearer YOUR_TOKEN" http://192.168.1.100:8766/webhook/abc-123-def
```

Use the **Copy URL** or **Copy curl** buttons on each webhook card to get the exact command.

### Webhook Responses

| Status | Meaning |
|---|---|
| `200 {"status":"triggered"}` | Action executed successfully |
| `401 {"error":"Unauthorized"}` | Wrong or missing bearer token |
| `403 {"error":"Webhook is disabled"}` | Webhook exists but is toggled off |
| `404 {"error":"Webhook not found"}` | No webhook with that ID |

### Managing Webhooks

- **Enable/Disable:** Toggle the switch to pause without deleting
- **Trigger Count:** See how many times each webhook has been called
- **Last Triggered:** See when it was last used
- **Delete:** Remove a webhook permanently

### Health Check

The webhook server also provides a health endpoint:

```
GET http://<your-ip>:8766/health
```

Returns `{"status":"ok","service":"glassdeck-webhooks"}`.

---

## Game Auto-Detection

GlassDeck includes a built-in database of 120+ popular games and applications. When auto-switch is enabled, GlassDeck can automatically detect which game you're playing and suggest profile associations.

### Using the Game Selector

1. Go to **Profiles** and select a profile
2. In the **Auto-Switch** section, click **Add Application**
3. The **Game Selector** appears with a searchable list of known games
4. Type to search by game name or executable name
5. Click a game to add it to the profile's auto-switch list
6. You can also manually enter any executable name

### Auto-Detection

When a game from the database is detected in the foreground and no profile is assigned to it, GlassDeck shows a suggestion banner letting you quickly associate it with the current profile.

**Supported categories:** FPS, Battle Royale, MOBA, MMO, RPG, Action RPG, Sandbox, Survival, Strategy, Racing, Sports, Simulation, Horror, Card Game, Party, Streaming, Creative, Communication, Music, Browser, Development, Action, Adventure.

---

## Multi-Deck View

View 2-4 profiles simultaneously in a split-pane layout — useful for monitoring multiple profiles at once.

### Opening Multi-Deck

Click **Multi-Deck** in the sidebar to open the multi-deck view.

### Layout Options

| Layout | Icon | Description |
|--------|------|-------------|
| **Horizontal** | Columns | Side-by-side panes |
| **Vertical** | Rows | Stacked panes |
| **Quad** | Grid | 2x2 grid of panes |

### Managing Panes

- **Add Pane** — Click "Add Pane" (up to 4 panes maximum)
- **Change Profile** — Use the dropdown in each pane's header to select a profile
- **Navigate Pages** — Use the arrow buttons in each pane to switch pages
- **Remove Pane** — Click the X button on any pane

The multi-deck view is read-only — buttons are displayed but not editable. Use the Deck Editor for editing.

---

## Lottie Animated Icons

Buttons can use Lottie JSON animations as icons for smooth, scalable, animated button graphics.

### Uploading a Lottie Animation

1. Select a button in the Deck Editor
2. Open the **Icon** section and switch to the **Custom** tab
3. Click to upload and select a `.json` Lottie file
4. The animation is saved and renders on the button

### Animation Modes

| Mode | Behavior |
|------|----------|
| **Loop** | Animation plays continuously (default) |
| **Once** | Animation plays once when the button appears |
| **On Press** | Animation plays when the button is pressed |

Lottie files are typically much smaller than GIFs and render at any resolution without quality loss. You can find free Lottie animations at [LottieFiles.com](https://lottiefiles.com).

---

## Chat Overlay

View live Twitch chat directly in GlassDeck's Deck Editor without switching windows.

### Enabling Chat

1. Open the **Deck Editor**
2. Click the **chat bubble icon** in the header toolbar (next to the canvas background buttons)
3. The chat overlay panel appears in the bottom-right corner
4. Enter a Twitch channel name and press Enter or click Send
5. Chat messages stream in real-time

### Features

- **Anonymous connection** — No Twitch login required (read-only)
- **Username colors** — Displays each chatter's chosen color
- **Auto-scroll** — Automatically scrolls to show new messages
- **Message buffer** — Keeps the last 100 messages
- **Disconnect** — Click "Disconnect" in the footer to stop the feed

### Toggling

Click the chat bubble icon again or the X button on the overlay to hide it. The connection persists while hidden — click the icon to show it again.

---

## Marketplace

The **Marketplace** page provides a unified browsing experience for all downloadable content.

### Accessing the Marketplace

Click **Marketplace** in the sidebar. You'll see three tabs:

| Tab | Content |
|-----|---------|
| **Plugins** | Action plugins that add new capabilities |
| **Templates** | Pre-built profile configurations |
| **Icon Packs** | Themed icon bundles for your buttons |

### Browsing and Installing

1. Switch between tabs to browse different content types
2. Use the **search bar** to filter by name, description, or tags
3. Click **Install** or **Import** to add content to your GlassDeck
4. Installed plugins appear on the Plugins page; imported templates appear as new profiles

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

> **Tip:** MIDI controllers are great for volume faders and brightness controls. Map a MIDI knob to a Spotify volume or Key Light brightness action for smooth, physical control.

### USB HID Devices

Connect macro pads, button panels, and other USB HID devices.

1. Go to **Settings > Hardware > USB HID**
2. Select your device from the dropdown
3. Use learn mode to map physical buttons to GlassDeck buttons

### Serial Devices

Connect Arduino, ESP32, and other serial devices.

1. Go to **Settings > Hardware > Serial**
2. Select the **COM port** and **baud rate** for your device
3. Map serial messages to button actions

> **Tip:** If you've built a custom button box with an Arduino, you can send serial messages when physical buttons are pressed, and GlassDeck will trigger the mapped actions.

### Network Hardware

ESP32 or Raspberry Pi devices can connect as WebSocket clients using the same protocol as the mobile app. This allows you to build fully custom hardware controllers that communicate wirelessly with GlassDeck.

---

## Voice Commands

Control GlassDeck hands-free with offline speech recognition.

1. Go to **Settings > Voice Commands**
2. Click **Download Language Model** — this is a one-time download (~50MB)
3. Select your **microphone** from the dropdown
4. Click **Enable Voice Commands**
5. Add keyword mappings:
   - **Keyword**: The word or phrase to listen for (e.g., "go live", "mute", "next song")
   - **Button**: The button action to trigger when the keyword is recognized

Voice recognition runs entirely offline using the Vosk engine — **no audio is sent to the cloud**.

> **Tip:** Use short, distinct keywords that don't sound like everyday words. "Go live" works better than "start" because it's less likely to trigger accidentally.

---

## Cloud Sync & Sharing

### Cloud Sync (GitHub)

Back up your profiles to a GitHub repository and sync them across multiple computers.

1. Go to **Settings > Cloud Sync**
2. Enter a **GitHub Personal Access Token** with repo access
   - To create one: go to **https://github.com/settings/tokens**, click **Generate new token (classic)**, check the **repo** scope, and click **Generate token**
   - Copy the token — you won't see it again
3. Enter the **repository name** (e.g., `your-username/glassdeck-profiles`)
   - The repository must already exist on GitHub. Create it first if needed (can be private).
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

> **Tip:** This is great for teams where a producer sets up the layout and the streamer customizes their preferences. Both can work at the same time without stepping on each other's changes.

---

## Mobile App

### Home Screen

When you open the mobile app, it shows a splash screen and then automatically searches for your desktop. Once connected, your button grid appears.

### Using Buttons

- **Tap** a button to trigger its action
- **Swipe left/right** to navigate between pages
- Buttons show visual feedback (animations) and haptic feedback on press
- Toggle buttons change appearance between states

### Switching Profiles

Tap the profile name at the top to see a list of available profiles and switch between them.

### Connection Status

The connection bar at the top shows whether you're connected to the desktop:
- **Green (wifi icon)** — Connected and synced
- **Yellow (connecting icon)** — Attempting to connect
- **Red (wifi-off icon)** — Error or disconnected

Tap the **X** button to disconnect, or the **gear icon** (when connected) to open settings.

### Settings

Access mobile-specific settings by tapping the gear icon:
- **Theme** — Switch between dark and light mode
- **Server** — View or change the connected server
- **About** — Version information and links

---

## Settings

### Network

- **Server Port** — Change the WebSocket server port (default: 8765). Only change this if you have a port conflict.
- **Windows Firewall** — Click **Configure** to set up or reset the firewall rule that allows your phone to connect.

### Appearance

- **Theme** — Dark or light mode
- **Close to Tray** — When enabled, closing the window minimizes to the system tray instead of quitting. GlassDeck keeps running in the background so your phone stays connected.

### Auto-Start

Configure GlassDeck to launch automatically when Windows starts. This ensures the desktop server is always running and ready for your phone.

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

- **Same network**: Both devices must be on the same WiFi network (or wired + WiFi on the same router)
- **Firewall**: Go to **Settings > Network** and click **Configure** to set up the firewall rule
- **VLANs**: mDNS doesn't work across VLANs — use manual connection with the desktop's IP address
- **Manual connect**: Open a command prompt, type `ipconfig`, and enter the IPv4 address into the mobile app
- **Router isolation**: Some routers have "AP isolation" or "client isolation" enabled, which blocks devices from talking to each other. Check your router settings and disable this feature.

### Phone Disconnects Frequently

- Check your WiFi signal strength on both devices
- Some routers aggressively power-save WiFi clients — check router settings for "WiFi power saving" and disable it
- The app reconnects automatically when the connection drops
- If on 5GHz WiFi, try switching to 2.4GHz — it has better range through walls

### Integration Won't Connect

- Make sure the external software (OBS, vMix, etc.) is running **before** you click Connect in GlassDeck
- Double-check the host, port, and password/token values
- For integrations that use OAuth (Twitch, YouTube, Spotify): try clicking **Re-authorize** to get a fresh token
- Check that your antivirus or firewall isn't blocking GlassDeck's network connections

### Actions Not Working

- **Keystroke/Hotkey**: Make sure the target application is in the foreground on the desktop
- **OBS**: Verify the OBS WebSocket server is running and the password matches
- **Twitch/YouTube/Spotify**: Re-authorize if the token has expired
- **Soundboard**: Check that the audio file path is correct and the file format is supported (MP3, WAV, OGG, FLAC)
- **Discord**: Make sure the keybinds in GlassDeck match exactly what you set in Discord

### Desktop Build Errors

See the [Development Guide](DEVELOPMENT.md) for build troubleshooting.

### Reset Everything

GlassDeck stores its data in `%APPDATA%/glassdeck/`. To reset:
1. Close GlassDeck completely (right-click tray icon > **Quit**)
2. Open File Explorer and type `%APPDATA%/glassdeck/` in the address bar
3. Delete the entire `glassdeck` folder
4. Restart GlassDeck — it will create a fresh database

**Warning:** This deletes all profiles, buttons, integration credentials, and settings. Consider exporting your profiles first.
