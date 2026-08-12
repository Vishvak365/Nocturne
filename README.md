# Nocturne site

The public-facing site for **Nocturne — Reader for Hacker News**
(the app's code lives at
[hackernews-offline-app](https://github.com/Vishvak365/hackernews-offline-app)).

This repo exists specifically to host **GitHub Pages** for the app —
it's where the App Store-required **Privacy Policy** and **Support**
URLs live, plus a landing page for what the app does. Static HTML/CSS,
no build step, no framework — every page here is meant to be readable
and editable directly.

## Pages

- `index.html` — the landing page: what the app does, screenshots, the
  free/Pro feature table.
- `privacy.html` — the Privacy Policy. Referenced from
  `app_store_checklist.md` in the main app repo as the required App Store
  Connect Privacy Policy URL, and from the in-app paywall
  (`lib/pages/paywall_page.dart`'s Privacy link, currently still pointing
  at a GitHub-repo placeholder — **update that link to this site once
  Pages is live**).
- `support.html` — the Support page. Same story as Privacy: this is meant
  to become the App Store Connect Support URL and replace the paywall's
  placeholder link once Pages is live.
- `terms.html` — links out to Apple's own standard EULA rather than
  hosting a custom one; see `plan.md`'s Phase 5 section in the app repo
  for why a custom EULA was deliberately skipped.
- `styles.css` — shared styling across all pages.
- `assets/` — screenshots, currently copied from the app repo's
  `docs/screenshots/`.

## Enabling GitHub Pages (one-time, manual)

This repo's content is ready, but **GitHub Pages itself still needs to be
turned on** in this repo's settings — that's a repo-admin action outside
of what a coding session can do via `git push` alone:

1. Go to this repo's **Settings → Pages**.
2. Under "Build and deployment", set **Source** to "Deploy from a branch".
3. Set **Branch** to `main`, folder `/ (root)`.
4. Save. GitHub will publish at `https://vishvak365.github.io/Nocturne/`
   (or a custom domain, if one gets added later via a `CNAME` file here).

Once Pages is live, come back to the main app repo and:

- Update `lib/pages/paywall_page.dart`'s Terms/Privacy links to point at
  the real hosted URLs instead of the GitHub-repo placeholder (there's a
  `TODO` marking exactly where).
- Update `README.md` and `project_specs/app_store_checklist.md` in the app
  repo to reference the live URLs instead of describing them as pending.

## Keeping this in sync with the app

The Privacy Policy here should stay accurate to what
`README.md`'s "Data source and legal posture" section in the app repo
says the app actually does — if that section changes (a new permission,
a new SDK, anything data-related), this site's `privacy.html` needs the
matching update, not just the app repo's own docs.
