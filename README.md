# SIGNAL — Visual Analyzer

A real-time audio visualization tool built as a single, self-contained HTML file. No dependencies, no build step, no install. Open it in a browser and it works.

![SIGNAL](https://img.shields.io/badge/version-2.4.1-00e5cc?style=flat-square&labelColor=050507) ![HTML](https://img.shields.io/badge/html-single--file-00e5cc?style=flat-square&labelColor=050507) ![License](https://img.shields.io/badge/license-MIT-00e5cc?style=flat-square&labelColor=050507)

---

## What it does

SIGNAL renders generative waveforms and frequency data in real time — either from a synthetic signal you control, or live from your microphone. It captures and exports that output as a video file.

---

## Visualization Modes

| Mode | Description |
|------|-------------|
| **Scope** | Classic oscilloscope — time-domain waveform with fill and glow |
| **Lissajous** | XY phase figure shaped by frequency ratios and the XY pad |
| **Waterfall** | Frequency over time, scrolling downward — like a spectrogram |
| **Radial** | Waveform wrapped in polar coordinates around a center point |

A spectrum analyzer runs persistently at the bottom across all modes, showing harmonic content on a logarithmic frequency axis.

---

## Controls

**Signal**
- `Frequency` — 20 Hz to 2000 Hz
- `Amplitude` — Signal level / volume
- `Phase` — Phase offset in degrees (0–360°)

**Waveform**
- Sine, Square, Sawtooth, Triangle, Noise

**Color**
- 5 color themes — cyan, red, amber, purple, green — applied globally across the visualizer

**Modulation**
- `LFO Rate` — Low-frequency oscillator that modulates amplitude organically
- `Harmonics` — Number of harmonic overtones added (1–12), affects both waveform shape and spectrum

**XY Pad**
- Interactive pad in the right panel — controls frequency ratios in Lissajous mode

---

## Mic Input

Click **ENABLE MIC** to switch all visualizations to live audio input. Requires browser microphone permission.

- Scope and Radial use time-domain data
- Waterfall and Spectrum use frequency-domain (FFT) data
- Click again to stop and return to synthetic signal

---

## Recording

Select a capture duration (5s / 10s / 30s / 60s), then click **RECORD CANVAS**.

- Captures both the main visualizer and spectrum analyzer as a single composited frame
- Runs at 30fps, 10Mbps via the `MediaRecorder` API
- Downloads automatically as a `.webm` file when the duration ends
- Stop early at any time by clicking the button again
- Works with both synthetic signal and live mic input

Output files are named `signal_{mode}_{timestamp}.webm` and play in Chrome, Firefox, VLC, and any modern media player.

---

## Usage

```bash
# Clone
git clone https://github.com/yourname/signal.git

# Open — that's it
open signal.html
```

Or just download `signal.html` and open it directly. No server required.

---

## Browser Support

| Browser | Visualization | Mic Input | Recording |
|---------|--------------|-----------|-----------|
| Chrome / Edge | ✅ | ✅ | ✅ |
| Firefox | ✅ | ✅ | ✅ |
| Safari | ✅ | ✅ | ⚠️ Limited (`captureStream` support varies) |

> Recording uses `video/webm` with VP9 codec where available, falling back to VP8. Safari has partial `MediaRecorder` support — visualization and mic input work fully; video export may vary by version.

---

## Stack

- Vanilla HTML / CSS / JS — zero frameworks, zero dependencies
- Canvas 2D API for all rendering
- Web Audio API for microphone analysis
- MediaRecorder API + `captureStream()` for video export
- Google Fonts (DM Mono) — loaded remotely, works offline with system fallback

---

## File Structure

```
signal.html   ← entire application, ~1400 lines
README.md
```

---

## License

MIT
