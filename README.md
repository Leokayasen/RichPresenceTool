# RichPresenceTool

Lightweight cross-platform host for Discord and StackSpace Rich Presence with a plugin system.

Features
- Host application that connects to Discord and manages presence updates.
- Plugin system: plugins expose game/app state via a local IPC.
- Example plugin: reads the active window title on your system and sends updates.

Security
- Plugins require user approval before starting.
- No telemetry by default.
- Memory-hooking/injection is NOT included in this repo.

See docs/ for detailed design and contribution guidelines.

Getting started (development)
1. Build the Host (Rust recommended) — TODO: add build instructions.
2. Run the host: `./host --dev`
3. Start example plugin:
   - `cd plugins/window-title-node`
   - `npm install`
   - `npm run dev`

Plugin API
- Plugins should open a WebSocket to ws://localhost:PORT/handshake
- Send JSON messages with this shape:
  {
    "type": "presence",
    "payload": {
      "details": "Playing level 2",
      "state": "In match",
      "largeImageKey": "game_logo",
      "smallImageKey": "mode_icon",
      "startTimestamp": 1670000000
    }
  }

License: MIT
