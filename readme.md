# Password Generator — Pixelated Nerd

Client-side password generator using Web Crypto, with copy and local history (site/username tags).

## Live demo

When you publish with GitHub Pages your site will be here:

```
https://<your-username>.github.io/<your-repo-name>
```

If you use a user site (repo named `<your-username>.github.io`), it’ll be:

```
https://<your-username>.github.io
```

## Features

- One‑file app (`index.html`) — just upload and it works
- Generates passwords with adjustable length (4–64) and character sets
- Entropy meter + rough cracking‑time estimate
- Cyberpunk animated background + custom favicon
- History with site/username tags; **Copy**, **Use**, **Edit**, **Delete**
- Cross‑tab/window sync on the same device
- Export history as `.txt`
- Keyboard shortcuts: **g** = generate, **c** = copy, **x** = clear

## Security & privacy

- 100% local: uses `window.crypto.getRandomValues`; no network calls
- History is stored in your browser’s `localStorage` under `pwdHistory_v1`
- Optional “avoid similar characters” filter (e.g., `O/0`, `l/1`)
- Tip: for sensitive accounts, also consider a dedicated password manager

## Files to upload

- `index.html` (this app)
- `.nojekyll` (empty file so GitHub Pages serves files as‑is)
- `LICENSE` (MIT)
- `README.md` (this file)

## Local development

Just open `index.html` in a browser. For the newest Clipboard API and service worker features, serve over `https` or `http://localhost`.

### Self‑tests (optional)

Append `?selftest` to the URL to run built‑in sanity tests in the console:

```
index.html?selftest
```

By default tests are **off** so your history doesn’t get auto‑generated entries.

## How it works (short version)

- Character pools are built from your selections; similar characters can be excluded.
- Randomness comes from the browser’s CSPRNG; characters are then securely shuffled.
- Entropy = `length × log2(poolSize)`.
- History entries are saved with optional site/username metadata and synced across tabs via `BroadcastChannel` and the `storage` event.

## Known limitations

- Clearing site data or running in private mode may wipe history.
- History is not encrypted at rest. If you need encryption, we can add passphrase‑protected AES‑GCM.

## FAQ

**Copy doesn’t work locally** — Use HTTPS or GitHub Pages. The async Clipboard API requires a secure context; the app falls back to the legacy method, but some browsers still restrict it on `file://`.

**Can I import/export history?** — Export to `.txt` is built‑in. Import/JSON can be added quickly if you want it.

## Credits

Made by **Pixelated Nerd**.

## License

MIT © 2025 Pixelated Nerd

