# ElectAR site

The public landing page for ElectAR, the AR practice app for Senior High TVL Electrical Installation and Maintenance.

A static site: `index.html` plus the scene renders in `img/`. No build step.

- **Local preview:** `python -m http.server 8000`, then open http://localhost:8000
- **Deploy:** Vercel builds nothing and serves the folder as-is; every push to `main` redeploys.

## APK download

The hero's "Download Android APK" button points at
`https://github.com/ettagg/electar-site/releases/latest/download/ElectAR-debug.apk`,
so it always serves the newest GitHub Release on this repo. The APK (~80 MB release build) lives
on Releases, not in git: GitHub rejects files over 100 MB, and the app repo is private,
so its releases can't be downloaded publicly.

To publish a new build:

1. Build the APK. Since 2026-10-04 the site serves a signed **release** build, made in a separate copy of the
   app project (compressed model textures, R8, ARM-only, signed with the key in `../release-signing/`).
   A plain `./gradlew assembleDebug` in `../ElectAR-app` still works but is ~300 MB and won't install over the release build.
2. Copy the APK to `ElectAR-debug.apk`. The name has to match exactly (the link and the QR code use it), even for a release build.
3. On GitHub: electar-site, then Releases, then Draft a new release. Use a new tag (e.g. `apk-2026-10-02`), attach the file and publish.
   With the GitHub CLI: `gh release create apk-2026-10-02 ElectAR-debug.apk --repo ettagg/electar-site --title "Debug build 2026-10-02"`
