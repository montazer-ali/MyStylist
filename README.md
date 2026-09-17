# My Stylist — install on your iPhone

This is a Progressive Web App (PWA). It's not in the App Store — instead, you host
these files at a URL and add it to your Home Screen from Safari, where it behaves
like a real app: its own icon, full-screen with no browser bar, works offline,
camera access, and your closet data stays saved on your phone.

## 1. Host the files

Upload this whole folder (`index.html`, `manifest.json`, `sw.js`, and the `icons/`
folder) to a static host. A few easy free options:

**GitHub Pages**
1. Create a new GitHub repo (public or private).
2. Upload all these files to it, keeping the folder structure intact.
3. Repo Settings → Pages → set source to your main branch.
4. Your app will be live at `https://yourusername.github.io/reponame/`.

**Netlify Drop**
1. Go to https://app.netlify.com/drop
2. Drag this whole folder onto the page.
3. You'll get a live URL immediately (e.g. `https://random-name.netlify.app`).

Either way, the important part is that **everything stays in the same folder together**
— don't rename or move `index.html`, `manifest.json`, `sw.js`, or the `icons/` folder,
since they reference each other by relative path.

## 2. Add it to your iPhone

1. Open the hosted URL in **Safari** on your iPhone (must be Safari, not Chrome —
   only Safari can add PWAs to the Home Screen on iOS).
2. Tap the **Share** button (square with an arrow, at the bottom of the screen).
3. Scroll down and tap **Add to Home Screen**.
4. Tap **Add** in the top right.

You'll now have a "My Stylist" icon on your Home Screen. Opening it launches
full-screen, no Safari address bar, like a native app.

## 3. First-time setup in the app

1. Open the app, go to **Settings**, and add your **Gemini API key**
   (get one free at https://aistudio.google.com/apikey).
2. Optionally add **your photo** in Settings if you want the "you wearing this
   outfit" picture feature on the Get Outfit tab.
3. Go to **Add Item** and start cataloging — tap **Take Photo** to use your
   camera directly, or **Choose from Library** to pick existing photos.

## What works offline vs. what needs internet

- **Opening the app, browsing your closet, editing items**: works offline once
  you've loaded it at least once (the app shell is cached).
- **Identifying new items and getting outfit suggestions**: needs internet,
  since those call Gemini's API.
- **Your closet data**: stored locally on your phone (`localStorage`), not on
  any server. It persists between opens automatically. Use Export in Settings
  periodically to keep a backup file, especially before clearing Safari's
  website data (which would erase it).

## Updating the app later

If you (or I) make changes to `index.html` later, just re-upload the updated
file(s) to your host. Since there's a service worker caching the app shell,
you may need to close the app fully (swipe it away from the app switcher) and
reopen it once or twice for the update to fully take effect.
