# Web MIDI Pad Controller

A browser-based MIDI pad controller that sends Note On/Off messages via the Web MIDI API. Designed to work as a remote trigger for a MIDI soundboard over RTP-MIDI networks.

## Features

- Configurable grid of pads sending MIDI Note On (press) / Note Off (release)
- Right-click toggle mode for sustained notes
- MIDI feedback input — pads glow when the instrument reports a sample is playing
- JSON-editable layout (jagged rows, per-pad channel/note/velocity/label)
- Layout persisted in localStorage
- Event log showing sent and received MIDI messages
- Dark theme with visual feedback on press and playback states

## Usage

1. Open in a browser that supports Web MIDI (Chrome, Edge, Opera)
2. Select a MIDI output device from the dropdown
3. Optionally select a MIDI input for playback feedback
4. Press pads to send MIDI notes — left-click for momentary, right-click for toggle
5. Click **Edit Layout** to customize the pad grid via JSON

### Layout format

```json
[
  [
    { "ch": 0, "note": 36, "vel": 127, "label": "Airhorn" },
    { "ch": 0, "note": 37, "vel": 127, "label": "Yeah" }
  ],
  [
    { "ch": 0, "note": 38, "vel": 127, "label": "Ding" }
  ]
]
```

Each inner array is a row of pads. Rows can have different numbers of pads.

## Companion instrument

Pair with [midi-soundboard.mjs](https://github.com/ramonsmits) (Node.js) to play MP3 samples triggered by MIDI events. The instrument sends feedback via a virtual MIDI output port so the controller can visualize playback state.

## License

MIT
