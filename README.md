# jeton

The public web pages for **Jeton**, an Android game app. This repo holds no
application code — only what has to be reachable by a URL.

Live at **https://fatihbarackilic.github.io/jeton/**

| Page | URL |
| --- | --- |
| Landing | https://fatihbarackilic.github.io/jeton/ |
| Privacy policy (TR) | https://fatihbarackilic.github.io/jeton/privacy.html |
| Privacy policy (EN) | https://fatihbarackilic.github.io/jeton/privacy-en.html |

The Turkish privacy URL is the one entered in **Play Console → App content →
Privacy policy**. It also shows on the store listing. If it ever 404s, Play can
suspend the app, so treat the file name as fixed: rename nothing here without
updating Play Console in the same sitting.

## Why this is a separate repo

The app's source lives in a **private** repo (`mobile-games`). GitHub Pages on
a free account only publishes from **public** repos — Pro is required for Pages
on a private one. So the pages that must be public live here, and the code
stays private. Nothing secret belongs in this repo.

## Layout

```
index.html        landing page, links to both policies
privacy.html      privacy policy, Turkish
privacy-en.html   privacy policy, English
style.css         shared stylesheet
```

Flat on purpose: this is a project repo, so Pages serves the repo root at
`/jeton/`, which is what puts `privacy.html` at the URL above. Moving a file
into a subfolder changes its URL.

## Publishing

GitHub Pages, configured under **Settings → Pages → Deploy from a branch →
`main` / `(root)`**. A push to `main` republishes within a minute or two; the
build shows up in the Actions tab as *pages build and deployment*. There is no
build step and no Jekyll theme — these are plain files, served as they are.

## Editing the policy

Both language versions say the same thing and **must be changed together**.
Bump the two dates at the bottom of each page when the text changes.

Every factual claim in the policy is read out of the app, not assumed. If any
of the following changes in `mobile-games`, the policy is wrong until it is
updated here:

- **`AndroidManifest.xml`** — the app requests `VIBRATE` and nothing else. The
  absence of `INTERNET` is what makes "collects no data" defensible: without
  that permission the operating system itself prevents data from leaving. Add
  that permission for any reason and the whole policy has to be rewritten.
- **`app/build.gradle.kts`** — no analytics, advertising or crash-reporting
  dependency. Crashlytics is on the roadmap; the day it lands, this policy
  gains a data-collection section and the Play Data safety form changes with
  it.
- **`res/xml/backup_rules.xml`** and **`data_extraction_rules.xml`** — exactly
  three stores travel to the player's own Google account (scores, games in
  progress, settings). The policy names those three.
- **The Settings screen** — the policy tells players they can erase scores and
  erase everything from it.

The palette in `style.css` is copied from the app's `ui/theme/CabinetColors.kt`
so the pages and the product cannot drift apart. It carries both halves of the
theme and follows the reader's system setting.

## Contact

The policy publishes `fatihb469@gmail.com` as the contact address, which Play
requires and already shows publicly as the developer contact.
