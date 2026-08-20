# Receipts

A browser-based prop generator for fanfic. Build fake screenshots — text threads, calls, social posts, Instagram DMs, and more — arrange them into a scene, and export as PNGs to drop into your fic.

No backend, no accounts, no data leaving your browser. Uploaded photos are processed locally and never sent anywhere.

**Live:** https://receipt-studio-black.vercel.app

## Pages

- **`index.html`** — the main toolkit
- **`instagram.html`** — Instagram-specific props
- **`storyboard.html`** — collect panels from either page and arrange them into a sequence

All three link to each other from the top bar.

## Features

### Main tools (`index.html`)
- **Text Thread** — iMessage or Android-style conversation with text bubbles, image bubbles, and location-share cards. Custom contact name, photo, status bar time, and a dark mode toggle.
- **Polaroid** — turn any uploaded photo into a polaroid: caption, tilt, tone filter (original/warm/faded/B&W), and a toggleable soft shadow.
- **Social Post** — X/Twitter or Instagram-style post card with avatar, caption, attached photo, editable stats/timestamp, and dark mode.
- **Incoming Call** — full-screen iPhone incoming call UI with caller name, subtitle (mobile/iPhone/FaceTime), and optional photo background.
- **Outgoing Call** — matching "calling..." screen with the standard iOS in-call icon toolbar and end-call button.
- **Group Chat** — add named participants (auto-colored), assign each line to a speaker, get iMessage-style sender labels above their bubbles, and switch between light/dark.
- **Note / Journal** — a directly-editable "paper" page with lined/grid/blank backgrounds and handwritten/typewriter/print fonts.
- **Lock Screen** — customizable wallpaper (presets or your own photo), time/date, and stackable notification banners.

### Instagram tools (`instagram.html`)
- **Profile** — username, display name, verified badge, bio, editable post/follower/following counts, a photo grid, and dark mode.
- **Chats** — an IG DM thread with solid-purple sent bubbles, gray received bubbles, an "Active now"-style status line, a toggleable "Seen" indicator, and dark mode.
- **Stories** — upload a photo as the story background, set username/avatar/time, optional caption text, and adjustable progress segments.
- **Notes** — add multiple people, each with their own avatar and optional note bubble (leave the note blank for a plain avatar-only entry), plus dark mode.

### Storyboard (`storyboard.html`)
- Every tab on both other pages has a **"+ Add to Storyboard"** button that captures the current panel.
- Panels collect here as a **slideshow** — arrow through them, jump via the thumbnail strip, reorder with "Move earlier/later," or delete individual slides.
- Add plain-text **caption cards** (e.g. "three days later...") to break up the screenshots.
- **Download Storyboard PNG** stitches every panel into one tall composite image.
- Panels are stored via the browser's local storage, shared across pages as long as they're served from the same location (see Notes below).

Every tab across all three pages exports to PNG (3x scale on individual downloads, 2x for storyboard panels).

## Usage

Visit **https://receipt-studio-black.vercel.app**, or run the files locally — see Notes below for a caveat on the Storyboard page specifically.

## Tech

Three standalone HTML files. Vanilla JS, no build step, no dependencies beyond CDN-loaded fonts and [html2canvas](https://html2canvas.hertzen.com/), which rasterizes each preview into a downloadable PNG. Font is Proxima Nova with a Poppins fallback (Proxima Nova is a paid font, so it only renders as such for visitors who have it installed locally).

## Notes

- All uploaded photos are processed locally in-browser and never uploaded anywhere.
- The location-share map is a stylized illustration, not a real map lookup — it doesn't use any geocoding or mapping API.
- The Storyboard page uses `localStorage` to pass panels between pages. This works reliably when all three files are hosted from the same origin (like the Vercel link above, or GitHub Pages). If you download the files and open them individually by double-clicking, some browsers block cross-file storage and panels won't carry over — run a local server or host them together instead.
