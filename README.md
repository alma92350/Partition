# 🎼 Partition Copier

A **single-file, fully static SPA** for manually copying a music score (partition)
and turning it into a **MIDI file**. No build step, no server, no dependencies —
just open `index.html` in any modern browser.

## What it does

1. **Upload** an image of a music partition. It is shown as a background layer
   (adjustable opacity).
2. **Lay a staff ("portée")** over the image — a movable, resizable 5-line staff
   with a treble or bass clef. Add as many staves as you need and align each one
   with the printed staves on your image.
3. **Copy the notes by hand.** Pick a duration — **noire** (♩, quarter),
   **croche** (𝅘𝅥𝅮, eighth) or **double croche** (𝅘𝅥𝅯, sixteenth) — and an optional
   accidental (♯ / ♮ / ♭), then click on the staff. The vertical position snaps to
   lines and spaces and determines the pitch (ledger lines are drawn automatically).
4. **Replay** the result in the browser (Web Audio) and **export a `.mid`** file.
5. **Save / load** the whole project (image + staves + notes) as JSON.

## Usage

Open the file directly:

```
# just double-click index.html, or:
xdg-open index.html      # Linux
open index.html          # macOS
```

### Quick workflow
- **📁 Upload** your partition image.
- **➕ Add staff**, then with the **✋ Move** tool drag it over a printed staff and
  match its **Width** and **Spacing** sliders to the image.
- Switch to the **🎵 Note** tool, choose a duration/accidental, and click to drop
  notes. The footer shows the pitch under the cursor.
- Use **🩹 Erase** to remove notes.
- Set the **Tempo**, hit **▶ Play**, then **💾 Export MIDI**.

### Keyboard shortcuts
- `1` Move · `2` Note · `3` Erase · `Space` Play

## How pitch is derived
The bottom line of each staff is the clef anchor (treble → E4, bass → G2). Every
line/space step above or below is one diatonic (white-key) step; the chosen
accidental shifts the result by a semitone. Notes are sequenced top staff to
bottom, left to right, into a monophonic Type-0 MIDI track at 480 ticks/quarter.

## Files
- `index.html` — the entire application (HTML + CSS + JS, no dependencies).
