# REFX

**A/B audio referencing, for people who suspect their mix is lovely but cannot quite prove it.**

*by Massive Impulsion — Olivier ELBHAR*

---

## What is this, then?

You have finished a track. You are rather pleased with it. You play it straight after a record you adore — something by Flume, say — and your track promptly sounds like it was recorded in a biscuit tin, three rooms away.

REFX exists to tell you, politely but firmly, *why*.

Load a **reference** (a released track you admire) and **your track**. REFX measures both, compares them, tells you what to change, and — should you be feeling brave — has a go at changing it for you.

It will not make your track good. It will, however, make it *comparably loud*, which in modern music is often mistaken for the same thing.

---

## Features

### 01 · Face-off
Both tracks, side by side, in enormous numbers. Integrated LUFS, true peak, punch, width, key and tempo, plus a **match score out of 100**. Scoring 100 means you sound exactly like the reference. Scoring 0 means you have, in fairness, made something original.

### 02 · Auto-match
The headline act. Press **MATCH IT** and REFX processes your track to sit closer to the reference:

1. **Match EQ.** A linear-phase EQ built from the difference between the two spectra. A slider sets how much of the gap to close (default 70%, capped at ±12 dB, and it leaves the sub-rumble and dog-whistle regions alone).
2. **Stereo width.** Mid/side adjustment towards the reference's width, with optional mono bass below 120 Hz, because nobody enjoys a kick drum that only exists in the left speaker.
3. **Loudness.** Gain plus a look-ahead true-peak limiter, iterated until it hits the target (reference, −14 LUFS for streaming, or "leave it as it is, thank you").

REFX then re-analyses the result and shows you the **before → after**. You can listen to it as **B+** and download it as a 24-bit or 16-bit WAV, which arrives in a zip, because the platform is fussier about file types than a sommelier.

### 03 · A/B listening
Switch between **A** (reference), **B** (yours) and **B+** (yours, matched) at the same position. Loudness matching is on by default, so you compare the *sound* rather than simply concluding that louder is better, which it is not, though it will try very hard to convince you otherwise.

Comes with mirrored waveforms, a live spectrum analyser and L/R meters, mainly so that it looks like serious equipment.

### 04 · Action plan
Ranked recommendations, colour-coded by how worried you ought to be:

- **Red:** fix this before you send it to a label.
- **Yellow:** worth a look.
- **Green:** already fine. Have a biscuit.
- **Blue:** for your information, no action required.

Each tonal recommendation comes with a starting EQ setting. Start at 50–70% of the suggested value. Your ears outrank the algorithm; that is, after all, why you have two of them.

### 05 · Tonal balance
Seven faders, from **Sub** to **Air**, showing where your track sits against the reference at matched loudness. Plus the average spectrum and the gap between the two, which you can scrub with a finger or a cursor, depending on how modern you are.

### 06 · Suggested EQ
The combined EQ curve with numbered bands and a little knob for each. You can listen to it on your track before committing, and copy the settings to your clipboard for your DAW of choice.

### 07 · Metrics
Everything measured, in tiles, plus a full table for those who enjoy tables.

### 08 · Loudness over time
Short-term loudness across the whole track, so you can see precisely where the drop fails to drop.

---

## What it measures

| Metric | What it tells you |
|---|---|
| **Integrated LUFS** | How loud the whole track feels. Measured per ITU-R BS.1770 / EBU R128, with gating, like a grown-up meter. |
| **Short-term / momentary max** | The loudest 3-second and 400 ms moments. |
| **True peak (dBTP)** | The real peak, including those between samples. Above −1 dBTP, encoders may introduce you to distortion. |
| **PLR** | Peak-to-loudness ratio. Roughly: how much punch you have left. |
| **LRA** | Loudness range: how much the level moves between sections. |
| **RMS, crest factor** | The classics. Still with us. |
| **Stereo correlation** | Below 0.2 and your track may partially vanish in mono. Clubs are in mono. Phones are in mono. Do take note. |
| **Width** | Side level relative to mid, overall, below 120 Hz and above 2 kHz. |
| **Spectral centroid** | Whether your mix is, broadly speaking, darker or brighter than the reference. |
| **Key (Camelot)** | Estimated key, with DJ-friendly Camelot notation and a compatibility verdict. |
| **BPM** | Estimated. It may occasionally report 87 when you meant 174. Drum & bass producers will be used to this sort of disrespect. |

---

## How to use it

1. Drop your **reference** into slot **A**.
2. Drop **your track** into slot **B**. WAV if you can. Long fades at either end will skew the averages, so trim them off.
3. Press **Run the comparison**.
4. Read the action plan. Sigh, if appropriate.
5. Adjust the Auto-match sliders, press **MATCH IT**, and listen to **B+**.
6. Download it, or better still, take the advice back to your mix and do it properly.

Keyboard shortcuts: **Space** plays, **A / B / M** switch between reference, yours and matched.

---

## Privacy

Everything runs in your browser. Your files are never uploaded anywhere. Your unreleased masterpiece remains entirely your own business.

---

## Known limitations (a candid list)

- **The spectrum also compares the arrangement.** If the reference has a vocal and yours does not, REFX will notice a shortage of mids and say so. It is a meter, not a mind-reader.
- **Copying a tonal balance at 100% copies the arrangement too.** 50–70% is usually more musical and considerably less embarrassing.
- **A large loudness gap makes the limiter work hard.** If you are 6–8 dB short, REFX will warn you. The tasteful fix is more density in the mix (bus compression, a clipper), not more faith in the limiter.
- **Key and BPM are estimates.** Confirm by ear, as people did in the olden days.
- **The exported sample rate follows your browser's audio engine** (often 48 kHz on a Mac).
- **It is a v0.3 draft.** It has opinions. Some of them are correct.

---

## Under the bonnet

- Single self-contained HTML5 page, Web Audio API, no external audio libraries.
- Loudness: BS.1770 K-weighting with absolute and relative gating.
- True peak: 4× oversampled interpolation around loud samples.
- Spectrum: 16k-point FFT, mid/side, 1/6-octave bands, compared at matched loudness with a +3 dB/oct tilt for readability.
- Key: chroma profile correlated with Krumhansl–Kessler templates.
- Tempo: spectral flux plus autocorrelation, with a polite bias towards plausible tempos.
- Match EQ: 8192-tap linear-phase FIR (frequency sampling, Blackman window), applied via an offline convolver.
- Limiter: offline look-ahead brickwall, iterated against a LUFS target and verified against the true-peak ceiling.
- Export: hand-rolled WAV encoder (24-bit, or 16-bit with TPDF dither), wrapped in a hand-rolled ZIP. We had our reasons.

---

## Roadmap, of sorts

- Several references at once, averaged into a target.
- Platform presets (Spotify, Apple Music, YouTube, Beatport, club).
- Dark, light and "oldschool chrome" themes, for those who miss 1984.
- A proper VST/AU plugin, so you can be told off without leaving your DAW.

---

## Credits

Designed and built by **Massive Impulsion** — *Olivier ELBHAR*.

No biscuit tins were harmed in the making of this tool.
