# KP-4 Sales Report — Installable App

Daily sales tracker with 9% GST, MTD, tender breakdown, and offline support.
After hosting once, anyone with the URL can install it on their phone like
a native app.

---

## ⚠️ READ THIS FIRST

Your GitHub repo must contain **exactly these 9 files**, all at the root
(no subfolders, no `.zip` files):

```
✓ index.html
✓ manifest.webmanifest
✓ sw.js
✓ icon-192.png
✓ icon-512.png
✓ icon-maskable-512.png
✓ apple-touch-icon.png
✓ favicon.ico
✓ favicon-32.png
```

If any of these is missing, or if extra files like `kp2-app.zip`,
`icon-512-maskable.png`, or `favicon.png` are present, **the install will
fail** and you'll see a gray fallback icon on your phone.

---

## 🧹 If your repo already has wrong files

Delete everything in the repo first, then upload only the 9 files above.

**From GitHub on phone:**
1. Open each wrong file → tap **⋯** menu → **Delete file** → **Commit changes**.
2. Repeat for every file that doesn't belong.
3. Then upload the correct files (next section).

**Easier: delete the repo and start fresh.**
1. Repo → **Settings** → scroll to bottom → **Delete this repository**.
2. Create a new empty repo.
3. Upload the 9 files below.

---

## 📤 How to upload (GitHub, from phone or desktop)

1. Open the repo on GitHub.
2. Tap **Add file → Upload files**.
3. Select all 9 files from the unzipped `kp4-sales-app/` folder.
   - On phone: tap the upload button, browse to where you extracted the
     zip, multi-select if your file manager allows, or upload one by one.
   - On desktop: drag all 9 files onto the upload page in one go.
4. Scroll down → **Commit changes**.
5. Once committed, go to **Settings → Pages**:
   - Source: **Deploy from a branch**
   - Branch: **main** / **(root)** → **Save**.
6. Wait ~1 minute. Your URL appears at the top of the Pages settings:
   `https://<your-username>.github.io/<repo-name>/`

---

## 🧪 Verify the upload worked

After GitHub Pages says it's deployed:

1. Open the URL in **Chrome** on your Android phone.
2. The page should load the KP-4 Sales Report with the **dark theme**.
3. Within ~3 seconds, a **blue banner** should appear at the bottom
   saying *"📱 Install KP-4 as an app"*.
4. Tap the white **INSTALL** button on the banner.
5. Confirm **Install** in the system popup.
6. The home screen now has the blue KP-4 ring icon. Tap it — the app
   opens full-screen.

**If the blue banner never appears**, the install won't work. Most likely
causes:
- A file is missing from the repo. Compare against the 9-file list above.
- You opened the URL inside WhatsApp / Facebook / Instagram — those
  use their own embedded browser that blocks PWA install. Long-press the
  link → "Open in Chrome" instead.
- The URL is still `http://` instead of `https://`. GitHub Pages always
  serves https, so just retype the URL with `https://`.

---

## 🍎 iPhone / iPad

1. Open the URL in **Safari** (not Chrome — Apple doesn't allow PWA
   install in any browser other than Safari).
2. Tap **Share** ⎘ → **Add to Home Screen** → **Add**.
3. The KP-4 ring icon appears on the home screen.

---

## 🔁 Pushing an update later

If you ever change the app:
1. Open `sw.js`, change the line near the top:
   `const CACHE_VERSION = 'kp4-v2.0.0';` — bump to `kp4-v2.0.1` (or any
   newer value).
2. Re-upload the changed files to GitHub (replacing the old ones).
3. Installed apps detect the new worker on the next launch and update
   automatically.

---

## ⚙️ Features

- Works fully offline after first visit.
- Local data only — each device keeps its own history in `localStorage`.
  Nothing is sent to any server.
- Print monthly history or a single day's report from inside the app.
- WhatsApp / Copy / Print buttons for quick sharing of daily totals.

KP-4 · Daily Sales Automation · GST @ 9%
