# Buds Mate

Your personal audio control center for earbuds.

A lightweight progressive web app that connects to earbuds over **Web Bluetooth**, reads real device info and battery levels, and gives you an equalizer + sound studio.

## Features

- **Add device** via Web Bluetooth (name, manufacturer, model, firmware, serial read automatically)
- Live battery levels when the buds expose the standard Battery Service
- 7-band / 10-band equalizer with presets + custom saves
- Sound Studio (bass boost, vocal clarity, spatial width)
- Device finder (rough proximity via RSSI)
- Custom product photos per device
- Dark / Light / Auto theme
- Works offline after first load (PWA)

## Requirements for real Bluetooth

| Requirement | Why |
|-------------|-----|
| **Chrome on Android** | Web Bluetooth is only fully supported there |
| **HTTPS** | Browsers block Web Bluetooth on `file://` and insecure origins |
| Earbuds in pairing / advertising mode | So they appear in the chooser |

Noise control, touch gestures, and ANC modes use brand-private protocols and are **not** available in any website — only in the official manufacturer app.

## Deploy (GitHub Pages)

1. Push this repo to GitHub
2. Go to **Settings → Pages**
3. Under **Build and deployment**, set Source to **GitHub Actions**
4. The workflow in `.github/workflows/build.yml` will deploy on every push to `main`

Your app will be live at:

```
https://<your-username>.github.io/<repo-name>/
```

Open that link in **Chrome on Android** and tap **Add device**.

## Local development

```bash
# Any static server works. Example:
npx serve .
# or
python3 -m http.server 8080
```

Then open `http://localhost:8080` in Chrome.  
(On Android, localhost from the phone needs a tunnel or the machine’s LAN IP over HTTPS for Web Bluetooth.)

## Project structure

```
├── index.html              # Full app (single file)
├── manifest.webmanifest    # PWA manifest
├── icon-192.png
├── icon-512.png
├── icon-1024.png
├── .github/workflows/build.yml
└── README.md
```

## License

MIT — do whatever you want with it.
