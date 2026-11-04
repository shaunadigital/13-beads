# Surprise did nothing on iPhone, and where the first versions live

Session 9, 2026-11-03.

## The question

Shauna, on iPhone Chrome: after adding a bracelet to the collection and going back to the string with the back arrow, the string was empty and tapping Surprise did nothing. Later she added: "tapping Surprise just makes the bead tray scroll to the right and you can't see Surprise anymore". Her screen recording showed it happens only on some colors (sky blue and mint did it, green and navy did not).

## What was tried and ruled out

- Chromium (pre-installed Playwright) at 400 x 780 and the `iPhone 13` device profile, with `click` and with touch `tap`, against the local build and the live site. Every path back from the collection worked: back arrow, Make another, the Collection button, after the close-up, after two bracelets in a row, with reduced motion, and with the Recent group showing in the tray (switch tabs once after picking beads so the tray redraws).
- WebKit (`python3 -m playwright install webkit`, then `p.webkit.launch()` with `p.devices["iPhone 13"]`) on the same paths, and a loop over all 20 strip colors: pick color, trash, tap Surprise, read `#tray` `scrollLeft` and `#count`. Every color worked and `scrollLeft` stayed 0.
- So simulated taps cannot reproduce it. The real iOS touch path (a touch that the browser decides is a scroll gets no click) is not exercised by Playwright.

## What the recording showed

Frames at 2 per second (`ffmpeg -i rec.mp4 -vf "fps=2,scale=300:-1,tile=8x3" -frames:v 1 sheet.png`): on sky blue, each tap on Surprise shifted the tray one well to the right, hiding Surprise, and the bead count stayed the same. Switching to green, taps worked.

## Cause (likely, not proven)

The phone tray had `scroll-snap-type: x proximity` with `scroll-snap-align: start` on each well, and `.bead-btn:active` scaled the well. On a real iPhone a touch can make the tray re-snap to the next column; a scroller that moves under the finger turns the touch into a scroll, so the click never fires. Why only some colors is unexplained; probably where the tray was resting after the color change (`buildTray(true)` keeps the scroll position).

## What shipped

- `scroll-snap-type: none` on the tray, no snap align on wells, the press shrinks the picture (`.bead-btn:active img`) instead of the well. Comment above the rule in `src/style.css`.
- `backToString()` in `src/main.js`: the three ways back from the collection redraw the tray from the start, and an empty string gets a Surprise bracelet on its own after 350ms (0 with reduced motion). Edit and Take a copy call `setMode('line')` directly and are untouched, because Take a copy strings its beads after `setMode`.
- Not confirmed on her phone yet. If it still happens, ask for a new recording and look next at the color strip's `scrollIntoView`-like centering after a color pick, and at `markJump`.

## Where the first versions of the game live (for the "I built this with AI" post)

- The origin chat is "10/7 game bracelet" in Shauna's claude.ai history (chat id `ef1f0dbf-ac9d-4d5c-8c24-729044a5e492`; she also has a share link to it). Its first message: "Lets discuss a game/web app concept where the user can 'make' a beaded friendship bracelet in the browser window." The share page loads by script, so WebFetch gets nothing; read it through the past-chats tool instead. That tool returns text only, no images.
- The very first prototype (flat 2D canvas, pony beads, ENCORE starter, "Tied off and ready to trade.") was published as the artifact "13 Beads" (https://claude.ai/artifact/K3LuQcqjn9u7mwLuWJ3qV6), which was later republished in place with the first 3D build. The 2D code survives only in that chat, turn 5 (the `Write` of `index.html`). It can be rebuilt exactly from there.
- The first 3D build is the repo's first commit, `bfdc224` (2026-10-08). `git worktree add <dir> bfdc224`, copy `node_modules`, `npx vite build`, serve `dist`. Phone screenshots of it were sent to Shauna on 2026-11-03.
