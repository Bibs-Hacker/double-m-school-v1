# MERCYVERSE — PWA App Shell

This package turns the MERCYVERSE web project into an installable Progressive Web App.

## Files
- `index.html` — app shell + beautiful custom install UI
- `styles.css` — glass/neumorphic visual layer and installed-app styling
- `app.js` — install prompt, standalone detection, online/offline status and service-worker registration
- `manifest.webmanifest` — app identity, icon, standalone display mode and launch behavior
- `sw.js` — offline app-shell cache

## GitHub / Vercel
Upload these files to the root of your repository and deploy over HTTPS. Vercel provides HTTPS automatically.

If you already have your real MERCYVERSE `index.html`, keep that application UI and merge the PWA parts from this starter:
1. Add the manifest `<link>` and mobile/PWA meta tags from this package to `<head>`.
2. Keep the `styles.css` install-modal styles or merge them into your current CSS.
3. Add the install modal markup to `<body>`.
4. Add `app.js` or merge its install/service-worker logic into your existing JS.
5. Keep `manifest.webmanifest` and `sw.js` at the repository root.

## Important icon note
The manifest currently points directly to the icon URL supplied by Dev-Brian:
`https://files.catbox.moe/lbrtj7.jpeg`

For the most reliable production installation across platforms, also create local PNG copies at 192x192 and 512x512 and change the manifest icon `src` values to those local files. A maskable 512x512 PNG is recommended for adaptive launcher icons.

## About “real application” behavior
`display: standalone` makes the installed PWA launch without the normal browser address bar/navigation UI. It receives its own launcher/home-screen icon and its own application window. It remains a web technology underneath, so it is not literally converted into a native Android/iOS executable.

## Offline vs sync
The service worker makes the app shell available offline. Cross-device data synchronization is a separate backend concern. To sync Mercy's data with Brian's device, connect the existing MERCYVERSE data layer to a cloud database/auth/storage system (for example Supabase) while keeping IndexedDB as the offline local database.
