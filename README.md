# Receipts

A browser-based prop generator for fanfic. Build fake screenshots — text threads, calls, social posts, Instagram DMs, X/Twitter posts, and more — organize them by project with reusable characters, arrange them into a scene, and export as PNGs to drop into your fic.

No backend, no accounts. Uploaded photos are processed locally in your browser and never sent anywhere.

**Live:** https://receipt-studio-black.vercel.app

## Pages

- **`index.html`** — the main toolkit (text threads, polaroids, calls, group chats, journal pages, lock screens)
- **`instagram.html`** — Instagram-specific props
- **`twitter.html`** — X/Twitter-specific props
- **`projects.html`** — create projects and reusable characters shared across the other pages
- **`storyboard.html`** — collect panels from any page and arrange them into a sequence

All five link to each other from the top bar, and most pages show a project switcher up there too.

## Projects & characters

Create a project on `projects.html`, then build out a roster of characters for it. Each character has:

- A name and a main avatar
- Any number of **Instagram accounts** (label, username, verified toggle, optional avatar override) — e.g. a public account and a finsta for the same character
- Any number of **X/Twitter accounts** (label, username, verified, private toggle, optional avatar override)
- Any number of **message profiles** (label, contact name, optional avatar override) — e.g. how they're saved in different people's phones

On every relevant tab across the Main, Instagram, and X/Twitter pages, there's a "Load a saved character" dropdown. Pick a character, then pick which of their accounts/profiles to use for that tab — it fills in the name, handle, avatar, and verified/private status for you, no retyping.

Each project also gets its **own separate Storyboard** — switching projects on `storyboard.html` swaps to that project's saved panels.

Note: since this needs to work across separate HTML files, characters and projects are stored in the browser's local storage — see the Notes section below for a hosting caveat.

## Features

### Main tools (`index.html`)
- **Text Thread** — iMessage or Android-style conversation with text bubbles, image bubbles, location-share cards, tapback-style reactions, and dark mode.
- **Polaroid** — turn any uploaded photo into a polaroid: caption, tilt, tone filter, and a toggleable soft shadow.
- **Incoming Call** / **Outgoing Call** — full-screen iPhone call UIs, including the standard in-call icon toolbar for outgoing calls.
- **Group Chat** — add named participants (or load them from a project character), assign each line to a speaker, iMessage-style sender labels, light/dark switch.
- **Note / Journal** — a directly-editable "paper" page with lined/grid/blank backgrounds and handwritten/typewriter/print fonts.
- **Lock Screen** — customizable wallpaper, time/date, and stackable notification banners.

### Instagram tools (`instagram.html`)
- **Profile** — bio, stats, verified badge, photo grid, dark mode.
- **Post** — a single feed post: photo, caption, location tag, likes/comments counts, timestamp, dark mode.
- **Chats** — text, photo, or video message bubbles (video shows a play-button overlay since it's a still image), solid-purple sent bubbles, reactions, "Seen" indicator, dark mode.
- **Stories** — photo background, caption, progress segments.
- **Notes** — add multiple people, each with their own avatar and optional note bubble.

### X/Twitter tools (`twitter.html`)
- **Profile** — banner, avatar, bio, verified badge, follower/following counts.
- **Tweet / Thread** — build a multi-post thread with photos and stats; private-account lock icon (color-correct in both light and dark mode); attach comment replies from other people, and reply to those comments too (nested one level deep) — delete any comment or reply without touching the original post.
- **DMs** — solid-blue sent bubbles, gray received, "Seen"-style status, dark mode.
- **Notifications** — mix likes, retweets, replies, follows, and mentions into one feed.

### Storyboard (`storyboard.html`)
- A **"+ Add to Storyboard"** button on every tab across the other pages captures that panel.
- Panels collect as a **slideshow**, scoped to whichever project is active — arrow through them, jump via the thumbnail strip, reorder, or delete individual slides.
- Add plain-text **caption cards** to break up the screenshots.
- **Download Storyboard PNG** stitches every panel into one tall composite image.

## Usage

Visit **https://receipt-studio-black.vercel.app**, or host the files yourself — see the local storage note below.

## Tech

Five standalone HTML files, vanilla JS, no build step. Fonts are Proxima Nova with a Poppins fallback (Proxima Nova is a paid font, so it only renders as such for visitors who have it installed locally). [html2canvas](https://html2canvas.hertzen.com/) rasterizes each preview into a downloadable PNG.

On iOS, if the site is added to the home screen, Safari's standalone mode blocks the normal download trick — the app detects that and instead shows the finished image full-screen with instructions to press-and-hold to save it, which works regardless of standalone mode.

## Notes

- All uploaded photos are processed locally in-browser and never uploaded anywhere.
- The location-share map is a stylized illustration, not a real map lookup — no geocoding or mapping API involved.
- Projects, characters, and storyboards all use `localStorage` to share data between pages. This works reliably when all five files are hosted from the same origin (like the Vercel link above, or GitHub Pages). If you download the files and open them individually by double-clicking, some browsers block cross-file storage and data won't carry over between pages — run a local server or host them together instead.