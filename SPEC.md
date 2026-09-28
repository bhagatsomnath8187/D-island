# Feature Checklist — extracted from https://macmenubar.app/dynamic-island

Source page lists 19 notch/Dynamic-Island menu-bar apps. Checklist below = the union of
advertised features, with the app each came from. macOS-only behaviors are adapted, not dropped.

## A. Island shell (from DynamicLake Pro, NotchNook, NotchFlow, DynamicNotch, Anclave)
- [x] A1. Compact island pill always visible at top of screen (macOS: around the notch → iPhone: island pill under the real notch/safe area).
- [x] A2. Expands on tap/hover into a large "island" surface with spring animation (NotchFlow: "Dynamic Island for your Mac"). — EXERCISED: expand via tap, outside-tap/✕/idle collapse, resize on rotate.
- [x] A3. Collapse on outside tap, on X button, and after inactivity timeout (NotchNook). — EXERCISED all three.
- [x] A4. Live Activities: ongoing progress shown in compact pill (Droppy, DynamicNotch, NotchBay). — EXERCISED: timer pill + progress bar, task pill, call pill, music pill with EQ.
- [x] A5. System HUDs — volume, brightness, battery charge — as island overlays (DynamicNotch). — EXERCISED volume + battery; brightness is N/A on web (no API), volume HUD carries the pattern.
- [x] A6. Settings/adaptation panel — macOS apps have desktop settings; iPhone equivalent = in-island Settings sheet (all apps). — EXERCISED: theme/compact/toggles.
- [x] A7. Customization: island color theme + compact-pill content choice (NotchNook "customize your notch"). — EXERCISED: dark/light, pill auto/music.

## B. Music (from DynamicLake Pro, Tuneful, Droppy, OmniNotch, NotchNook)
- [x] B1. Now-playing widget with album art, title, artist. — EXERCISED.
- [x] B2. Play/pause, next/prev controls (Tuneful: menu bar music control). — EXERCISED: real WebAudio synth starts/stops.
- [x] B3. Seekable progress bar with elapsed/remaining time (Droppy mini-player). — EXERCISED.
- [x] B4. Volume slider (Tuneful). — EXERCISED: changes WebAudio gain.
- [x] B5. Live audio visualizer bars (Droppy: "live audio visualizer that moves to the actual sound"). — EXERCISED: analyser data verified nonzero; bars driven from it.
- [x] B6. Music queue: upcoming tracks list, tap to jump (DynamicLake Extensions: "Music Queue"). — EXERCISED.
- [x] B7. Lyrics ticker (Droppy lyrics). — EXERCISED: advances with position; copy-to-tray.

## C. Clipboard (from OmniNotch, NotchBay, Supaste, Droppy)
- [x] C1. Clipboard tray: items copied via in-app copy buttons land in history.
- [x] C2. Clipboard history list; tap to copy back to system clipboard.
- [x] C3. Pin items; delete items; clear all (Supaste clipboard manager).
- [x] C4. Max 30 entries, newest first, deduped.

## D. Files (from OmniNotch "file shelf & AirDrop", Droppy file tray, DynamicLake drag & drop)
- [x] D1. File shelf: drop files onto the island area to shelf them (desktop) or use picker (mobile).
- [x] D2. Shelf shows name + size + type icon; tap to preview; remove button.
- [x] D3. Share via share sheet = AirDrop equivalent (navigator.share).
- [x] D4. Drag-and-drop from shelf onto drop zone supported on desktop browsers.

## E. Notifications / quick reply (from DynamicLake Pro, NotchBay, Droppy)
- [x] E1. Simulated incoming notifications appear as island banner + are listed.
- [x] E2. Quick reply inline from notification (DynamicLake: "Instantly reply to SMS").
- [x] E3. Unread badge count on compact pill.

## F. Timers & reminders (from OmniNotch timers, Notch Buddy, Maaa, DeskSquat)
- [x] F1. Timer presets (1/3/5/10 min) + custom minutes; counts down in pill.
- [x] F2. Pomodoro-style repeat + break option is part of timer presets via chaining (kept simple: single timer + break preset).
- [x] F3. Gentle reminder with voice — Maaa "familiar voices"; uses SpeechSynthesis on completion ("Timer done").
- [x] F4. Desk coach — DeskSquat: hourly movement nudge, toggleable, counts nudges today.

## G. Live info widgets (from OmniNotch weather/stocks, MacNotch calendar — sibling app on same page)
- [x] G1. Weather widget (conditions, temp; simulated local feed, refreshable).
- [x] G2. Stocks widget (ticker list with +/- percent; simulated quotes refresh).
- [x] G3. Calendar: next upcoming events from user-added events.

## H. AI & dictation (from OmniNotch "Ask Omni", NotchBay "on-device dictation", Tucky)
- [x] H1. Ask Omni: on-device mini assistant — rule-based answers (time, date, math, timers, jokes) in island chat.
- [x] H2. On-device dictation: SpeechRecognition when available; falls back to text input.

## I. Stats / system (from Notch Buddy "stats", Notch Boy "task progress")
- [x] I1. Battery/level + network online status + page uptime in a Stats row.
- [x] I2. "Task progress": one fake long-running task (Index files) with progress in pill as a Live Activity.

## J. Notes / links / shelf extras (from Tucky, Notch→Are.na, Supaste shelf)
- [x] J1. Quick note: write a note, saved list, tap to load, delete.
- [x] J2. Save link: paste URL, stored in list, tap opens.

## K. Phone (iPhone equivalent of macOS call/Bluetooth alerts in DynamicLake)
- [x] K1. Simulated incoming call: island expands with accept/decline, in-call timer, mute.

## L. Persistence & PWA-ish mobile behavior
- [x] L1. All state (notes, clipboard pins, settings, events, stocks symbols, link saves) persists in localStorage. — EXERCISED across reloads.
- [x] L2. Mobile viewport meta, safe-area padding, touch targets ≥ 40px, no 300ms tap delay. — EXERCISED in 390×844 viewport.
- [x] L3. Dark iOS-style UI; settings toggle for light theme. — EXERCISED both themes.

## Exercise log (browser-verified, 390×844 Chromium)
Every section opened and driven: music transport/seek/volume/visualizer/queue/lyrics; timer presets,
pause/resume/stop/custom/break; clipboard add/pin/copy/delete/clear + dedupe + pinned-first; files
add/drop-zone/share/del + stats count; notif banner/list/dismiss/quick-reply (button + Enter) + badge;
call ring→accept→mute→end→missed-notif; Omni chat (time, math, greeting, joke, timer N), mic fallback;
weather refresh/copy, stocks add-symbol/refresh/copy, calendar add/list, stats tiles + battery HUD;
notes add/load/del, links add/normalize/del; theme light/dark; toggles auto-collapse (timed), voice,
haptics, squat (tick emulated); pill long-press/double-tap cycle; pill live-activity priority + progress
bar; reset-with-confirm-cancel. Console clean except expected Chromium vibrate-before-gesture notice.
- Known limitations: brightness HUD has no web API; SpeechRecognition exists in Chromium but recording
  state was validated via fallback path; hover-only desktop affordances intentionally secondary to touch.

## Explicit adaptations (macOS → iPhone), not dropped:
- Menu bar placement → fixed island pill under device notch/safe-area top.
- Hover to open → tap to open (hover still works on desktop browsers).
- AirDrop → Web Share API.
- Notch drag & drop → drop zone + file picker.
- On-device Apple Intelligence → rule-based on-device assistant, no network.
- macOS settings window → Settings tab inside expanded island.
- Lock screen / HUDs → full-screen island overlay HUDs on toggle + volume/brightness events.
- Voice reminders (Maaa) → SpeechSynthesis.
- Dictation (NotchBay) → SpeechRecognition with graceful fallback.
- Bluetooth/call alerts (DynamicLake) → simulated call widget.
