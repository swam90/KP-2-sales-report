# KP2 Sales Report — Installable App

Turn your sales report into an installable phone app that staff and partners can
add to their home screen on **Android** or **iOS**, with offline support.

---

## What's in this folder

| File | Purpose |
|---|---|
| `index.html` | The app itself |
| `manifest.webmanifest` | Tells phones it's an installable app |
| `sw.js` | Service worker — enables offline mode |
| `icon-192.png` / `icon-512.png` | App icons (standard) |
| `icon-512-maskable.png` | Android adaptive icon |
| `apple-touch-icon.png` | iOS home-screen icon |
| `favicon.png` | Browser tab icon |

You need to **upload all of these together** to a web host.
The app won't install correctly if files are missing or the host isn't HTTPS.

---

## Step 1 — Host it (pick one, ~3 minutes)

### Option A: Netlify Drop (easiest, no account needed to try)

1. Go to **https://app.netlify.com/drop**
2. Drag this entire folder onto the page
3. You instantly get a URL like `https://lucky-name-12345.netlify.app`
4. (Optional) Sign up free to claim the site permanently and rename it

### Option B: Cloudflare Pages

1. Go to **https://pages.cloudflare.com** → sign up free
2. Click "Upload assets" → drag the folder
3. Get a URL like `https://kp2-report.pages.dev`

### Option C: GitHub Pages (most permanent)

1. Create a free GitHub account
2. Create a new repository (e.g. `kp2-report`), make it **public**
3. Upload all files in this folder to the repo root
4. Settings → Pages → Source: "Deploy from branch" → `main` / `/ (root)` → Save
5. After ~1 minute, your site is at `https://YOURNAME.github.io/kp2-report/`

> **Important:** the host **must use HTTPS**. All three options above do this
> automatically. PWAs will not install over plain `http://`.

---

## Step 2 — Share the URL with your team

Once hosted, just send the URL via WhatsApp, email, or paste it into a group chat.
Below is the message users will need to install it.

### For Android users

> Open this link in **Chrome**: `https://your-url-here`
> Chrome will show an "Install app" banner — tap it.
> If you don't see the banner, tap the **⋮ menu → Install app** (or "Add to Home screen").

### For iPhone / iPad users

> Open this link in **Safari** (not Chrome — iOS requires Safari for this):
> `https://your-url-here`
> Tap the **Share button** (square with up arrow) → scroll down →
> **Add to Home Screen** → Add.

After installing, the app icon appears on the home screen and opens fullscreen
without browser bars — just like a real app from the Play Store / App Store.

---

## Step 3 — Updating the app later

When you change `index.html`:

1. Open `sw.js` and bump the version line:
   ```js
   const CACHE_VERSION = 'kp2-v1';   // change to 'kp2-v2', 'kp2-v3', etc.
   ```
2. Re-upload the changed files to your host.
3. Users will pick up the new version the next time they open the app
   (may need to close and reopen once for the service worker to refresh).

---

## Important limitations to share with your team

1. **Each phone stores its own data.** Sales saved by Person A are not visible
   to Person B. The data lives in the browser's local storage on that one device.
   If a user clears their browser data or uninstalls, their history is gone.

2. **No central database.** If you need shared sales data across staff or
   locations, the app needs a real backend — that's a bigger build.

3. **No Play Store / App Store listing.** This installs via the browser. It
   looks and works like an app but doesn't appear in the stores. (Listing in
   stores requires extra wrapping work — TWA for Play Store, Capacitor + a paid
   Apple Developer account for App Store.)

4. **iOS is stricter.** Some PWA features (like notifications) are limited on
   older iOS versions. Adding to home screen has worked since iOS 11.3 though,
   so install itself is fine.

5. **First open needs internet.** After that the app works offline thanks to the
   service worker, but the very first visit must download the files.

---

## Troubleshooting

**"Install app" option doesn't appear on Android**
→ The site must be HTTPS (✓ if you used Netlify/Cloudflare/GitHub Pages).
→ Visit the page once, wait a few seconds, then check the ⋮ menu.

**iOS shows a blank icon on home screen**
→ Make sure `apple-touch-icon.png` is in the same folder as `index.html` and
  was uploaded together.

**"This site cannot provide a secure connection"**
→ Your host isn't HTTPS. Switch to one of the three options above.

**Users on different phones see different data**
→ Expected — see limitation #1 above. This app is single-device by design.
