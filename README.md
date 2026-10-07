# Kink Jars

A one-page questionnaire. Pick a color, rate each jar from 1 (a little) to 5 (overflowing), then download a picture or share a link. Your answers stay in your browser unless you share them.

Based on [LockedTony/kink-jars](https://github.com/LockedTony/kink-jars), with editable jars, decorations and shareable links.

## Using it

1. Add a name if you want, then pick a color and a container (Jar, Potion, Mug, Heart, Fishbowl, Cauldron, Wine glass, Milk bottle or Measuring jug). The container applies to every jar on the sheet, and the picture's title follows it (Kink Jars, Kink Potions, and so on).
2. Rate any jars you like. Skip a jar to leave it empty, or tap its rating again to clear it.
3. Choose **Copy link** to save or share your answers, or **Download image** to save a PNG.

Use **Edit / order jars** to rename, move, add or remove jars. Put `/` in a label for a line break, for example `being / a dom`. The picture updates as you type, and answers stay with their jars.

Open **Decoration** on a filled jar to add hearts or ants. Jars rated 5 also offer overflow effects, chosen automatically unless you pick one. The two ants jars have their own default artwork. **Flip** appears for decorations that can face either way.

## Saving and privacy

Your answers and edits are saved in the page address after `#`. **Keep the link to reopen or edit them later.** There is no separate browser save; a downloaded picture only saves the image.

The part after `#` is not sent to the server. It is scrambled, but **not encrypted**: anyone with the link can open your answers.

## Hosting

The app is a single `index.html` file with no build step or backend. You can serve it from a static web host.

For GitHub Pages:

1. Add `index.html` to a public repository.
2. In **Settings → Pages**, choose **Deploy from a branch**, select `main` and `/ (root)`, then save.
3. Once deployed, open `https://<your-username>.github.io/<repo-name>/`.

Use HTTPS so **Copy link** can access the clipboard. If copying fails, the page shows the link for you to copy manually.

## Customizing

Edit these settings in the `<script>` in `index.html`:

- `JARS`: default jars, with each label split into lines. The grid has seven columns and adds rows as needed.
- `JAR_LIDS`: default overflow decoration for a jar, keyed by its full label.
- `PRESETS`: color choices.
- `CONTAINERS`: container shapes. Each one only describes its own outline, liquid area, lid and overflow area; decorations are drawn for the jar and moved onto the container's sides automatically.
- `STYLE_NAMES`: all decoration styles. `RANDOM_STYLES` sets how many styles from the start of this list are used automatically.
- `DECORATIONS`: styles available for jars rated 1–4, in menu order.
- `DIRECTIONAL`: styles with a **Flip** button.

### Keeping existing links working

- You can reorder, add or remove default jars. Renaming a default jar loses its saved answers because links match jars by label.
- Only append styles to `STYLE_NAMES`; changing their order changes how old links display decorations. The link format supports up to 16 styles.
- The same applies to `CONTAINERS` (up to 16). Links made before containers existed open as jars.
- Add new link settings only as optional fields at the end of the link, where a missing field means the old behavior.

For details of the link format, see the comment above `encodeState()`.
