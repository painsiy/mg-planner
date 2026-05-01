# MG Planner — Deployment Guide

## What you have
- `index.html` — the full planner app
- `manifest.json` — makes it installable as a phone app
- `sw.js` — offline support
- `icons/` — app icons

---

## Step 1 — Set up Firebase (free, 5 min)

Firebase stores your daily data and syncs it across all your devices.

1. Go to **https://console.firebase.google.com**
2. Click **Add project** → name it `mg-planner` → click through the setup
3. In your new project, click **Build → Realtime Database**
4. Click **Create Database** → choose a region near you → start in **test mode**
5. Click the gear icon (top left) → **Project settings**
6. Scroll to **Your apps** → click the **</>** (Web) icon
7. Register app name: `mg-planner` → you'll see a config block like:

```js
const firebaseConfig = {
  apiKey: "AIza...",
  authDomain: "mg-planner-xxxxx.firebaseapp.com",
  databaseURL: "https://mg-planner-xxxxx-default-rtdb.firebaseio.com",
  projectId: "mg-planner-xxxxx",
  storageBucket: "mg-planner-xxxxx.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456..."
};
```

8. Open `index.html` in a text editor
9. Find the section marked `── REPLACE WITH YOUR FIREBASE CONFIG ──`
10. Replace the placeholder values with your real config values
11. Save the file

**Lock down your database** (do this after testing):
- In Firebase Console → Realtime Database → Rules
- Replace the rules with:
```json
{
  "rules": {
    "users": {
      "$uid": {
        ".read": true,
        ".write": true
      }
    }
  }
}
```

---

## Step 2 — Push to GitHub Pages (free, permanent URL)

1. Go to **https://github.com/new**
2. Create a new repo named `mg-planner` → set to **Public** → click Create
3. Upload your files — click **Add file → Upload files**
4. Drag in: `index.html`, `manifest.json`, `sw.js`, and the `icons/` folder
5. Click **Commit changes**
6. Go to **Settings → Pages** (left sidebar)
7. Under **Source** → select **Deploy from a branch**
8. Branch: `main`, folder: `/ (root)` → click **Save**
9. Wait ~60 seconds, then your URL appears:
   **`https://yourusername.github.io/mg-planner`**

That's your permanent link — bookmark it on every device.

---

## Step 3 — Install to phone home screen

### iPhone (Safari):
1. Open your GitHub Pages URL in Safari
2. Tap the **Share** button (box with arrow)
3. Scroll down → tap **Add to Home Screen**
4. Tap **Add**

### Android (Chrome):
1. Open your GitHub Pages URL in Chrome
2. Tap the **three dots** menu
3. Tap **Add to Home screen** or **Install app**
4. Tap **Install**

The app opens full-screen, no browser bar, just like a native app.

---

## Step 4 — Sync across devices

When you first open the app, it asks for a username. Use the **exact same username** on your phone and PC. That's all — everything syncs automatically through Firebase.

---

## Updating the app later

If you want to make changes to the app:
1. Edit `index.html` locally
2. Go to your GitHub repo
3. Click on `index.html` → click the pencil (edit) icon → paste the new content
4. Commit — GitHub Pages auto-deploys in ~60 seconds

---

## Quick links
- Firebase Console: https://console.firebase.google.com
- GitHub Pages docs: https://docs.github.com/en/pages
- Your app (after deploy): https://yourusername.github.io/mg-planner
