# Veilfall — offline app for iPhone & iPad

## 1. Put it on GitHub Pages

1. Create a repo (for example `veilfall`), or use a folder inside an existing Pages repo.
2. Upload **the contents of the `veilfall/` folder**: `index.html`, `sw.js`, `manifest.webmanifest`, `.nojekyll`, and the `assets/`, `fonts/` and `icons/` folders.
   - `.nojekyll` is a hidden file. If you upload through the GitHub website, check it made it across.
3. Go to **Settings → Pages**, set the source to your branch (root), and save.
4. Wait a minute, then open `https://<your-username>.github.io/veilfall/` and check the game loads.

Everything uses relative paths, so it works at any sub-path. You don't need to change anything.

## 2. Install it on each device (while you're still on Wi-Fi)

1. Open the Pages link in **Safari**. It has to be Safari: other iOS browsers can't install web apps offline.
2. Let the title screen finish loading. On that first visit, the whole game (about 1 MB) is saved to the device.
3. Tap **Share → Add to Home Screen → Add**.
4. Open Veilfall from the new home-screen icon **once** while you're still online.

## 3. Test it before you leave

1. Turn on **Airplane Mode** (and make sure Wi-Fi is off too).
2. Force-close Veilfall, then reopen it from the home screen.
3. Start a run, fight one battle, go back to the title screen, and confirm **Continue this journey** appears.

If all of that works in Airplane Mode, it will work on the ship.

## Good to know

- **Saves stay on the device you play on.** The iPhone and the iPad each keep their own saves. To move a run between them, use **Save Code** in town, then **Resume from a save code** on the other device.
- **The home-screen app and Safari keep separate saves.** Always play from the icon.
- **Updates:** after you push a new version, open the app twice while online. The first launch downloads the update in the background, and the second launch runs it. When you're offline, it keeps running the last version it downloaded.
- **Don't clear Safari's website data** before or during the trip. That deletes the offline copy and your saves.

## Rebuilding after game changes

```
python3 build_pwa.py --html veilfall.html --assets assets --fonts <fontsource files> \
    --out veilfall --license <font LICENSE files>
```

The build swaps Google Fonts for bundled copies, adds the install tags and the service worker, and stamps a new cache version from a hash of every file. It also lists any art the game expects that is missing from `assets/`.

Fonts: Cinzel, Lora and JetBrains Mono, all under the SIL Open Font License (`fonts/OFL.txt`).
