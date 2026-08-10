# Receipts

A browser-based prop generator for fanfic. Build fake screenshots — text threads, calls, social posts, and more — and export them as PNGs to drop into your fic.

No backend, no accounts, no data leaving your browser. It's a single HTML file.

## Features

- **Text Thread** — iMessage or Android-style conversation with text bubbles, image bubbles, and location-share cards. Custom contact name, photo, and status bar time.
- **Polaroid** — turn any uploaded photo into a polaroid: caption, tilt, tone filter (original/warm/faded/B&W), and a toggleable soft shadow.
- **Social Post** — X/Twitter or Instagram-style post card with avatar, caption, attached photo, and editable stats/timestamp.
- **Incoming Call** — full-screen iPhone incoming call UI with caller name, subtitle (mobile/iPhone/FaceTime), and optional photo background.
- **Outgoing Call** — matching "calling..." screen with the standard iOS in-call icon toolbar and end-call button.
- **Group Chat** — add named participants (auto-colored), assign each line to a speaker, and get iMessage-style sender labels above their bubbles.
- **Note / Journal** — a directly-editable "paper" page with lined/grid/blank backgrounds and handwritten/typewriter/print fonts.
- **Lock Screen** — customizable wallpaper (presets or your own photo), time/date, and stackable notification banners.

Every tab exports to PNG at 3x scale for crisp screenshots.

## Usage

Link!! https://receipt-studio-black.vercel.app

## Tech

Single HTML file. Vanilla JS, no build step. Uses [html2canvas](https://html2canvas.hertzen.com/) (via CDN) to rasterize the preview into a downloadable PNG.

## Notes

- All uploaded photos are processed locally in-browser and never uploaded anywhere.
- The location-share map is a stylized illustration, not a real map lookup — it doesn't use any geocoding or mapping API.
