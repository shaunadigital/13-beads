# Queue

Top item is the next thing to do.

## Next

1. **Shauna's iPhone check of session 9.** Pick sky blue or mint, tap the trash button, tap Surprise: it should string a bracelet (before, the tray slid one column and nothing happened). Also: the page should never scroll, the More menu ends with More games, Feedback, and Made by Shauna, and going back from the collection to an empty string strings a Surprise bracelet. If Surprise still fails, ask for a screen recording; leads are in `_docs/findings/2026-11-03-iphone-surprise-tap.md`.
2. **Content for the "I built this with AI" post (waiting on Shauna).** Options offered: rebuild and capture the flat Oct 7 prototype (code in the origin chat, see the findings note), and a simulated typing clip of her first prompt or her own recording of the real chat. Format probably vertical 1080 x 1920. Do nothing until she answers.
3. **Full collection on a real older phone.** Measured in the cloud renderer (2026-11-02): a full tray of 24 draws about 200 draw calls and 185,000 triangles for the rows on screen, plus a shadow pass; the stringing screen is about 10,000. The shadow pass is now redrawn only when something on the tray moves or it scrolls. If an older phone still stutters, build bracelets lazily (only rows near the viewport) or use fewer segments per bead on the tray.
4. **Heart hands model.** Shauna scans her sculpture (`_docs/findings/2026-10-08-heart-hands-model.md`) or finds an openly licensed model. Low priority; it would be a charm or prop now, not the display.
5. **Older phone checks still open** from earlier sessions: shake to spill strength, trade links end to end with a QR scan, the share sheet for Save card and Send link, Tilt, and adding to the home screen and opening offline.

Done 2026-11-03 (session 9): the game fits one screen with no page scroll (footer links and fan note moved to the More menu and start screen), smaller wells on short phones, a hint on an empty string, Surprise strings itself when coming back from the collection to an empty string, and the bead tray no longer snaps (the likely cause of Surprise doing nothing on her iPhone).

Done 2026-11-02 (session 8): start screen, logo mark and icons, link preview, sample bracelet, bigger desktop beads, `?demo` recording mode, the tray and close-up replacing the wall, restyled share pictures, Web Analytics. Shauna checked the launch polish on her iPhone. The games page card keeps her painted art (her call). Two-strand bracelets checked on the tray and in the close-up. The design board has two new rows at the top with screenshots of the current screens (phone and desktop, light and dark, plus the share pictures).

## Later, agreed in principle

- On short desktop windows (about 760 px tall) with the bead case open, a full string can dip to the bottom edge of the canvas. Consider limiting the sag by the canvas height.
- Bead switching ideas not chosen: press and hold a bead on the string to add another like it, and press and hold a compartment to add three.
- Clasps and cord choices at the finish step.
- Length budget: revisit (Shauna).
- True-size beads with wrist sizes: on hold.
- More props, only if they can be done well: a polaroid once there is a real picture to show (the share card of a bracelet, say).
- Wrist shot: the finished loop over the phone camera, saved as a picture (not built, 2026-10-12).
- Twist and Daisy two-strand patterns (dropped for now, 2026-10-11).
- Unlockable charms behind secret phrases, with an original easter-egg melody.
- Shadow box, keepsake ticket craft, denim jacket craft (the hook wall can hold any of them as a prop).
- Games home page redesign (Shauna, other sessions).
- Optional music player through an official embed.
