# nade-overland.com

The website for [Nade](https://nade-overland.com), a camping map drawn by the
people driving it.

Two static pages, served by GitHub Pages. They have three jobs:

1. **Homepage** — what Nade is.
2. **Landing page after an email link.** Supabase redirects here (it is the
   project's Site URL) once someone clicks the link in a sign-up or
   email-change message. The confirmation has already happened on Supabase's
   side by then; this page only says so.
3. **The privacy policy** (`privacy.html`) — App Store Connect requires a
   public URL for it before the app can be submitted.

## privacy.html is generated — do not hand-edit it

Its words come from `src/app/infoDocs.ts` in the app repo, the same module the
in-app pages are drawn from, so the policy on the web and the policy in the
app cannot drift into saying different things. To change it, edit that file
and run, from the app repo:

```
node scripts/build-legal-pages.mjs ../nade-overland.com
```

Then commit the result here. The same command takes `terms` as a second
argument if the terms of use ever need a public page too.

## How it reads the URL

- Success: `#access_token=…&refresh_token=…&type=signup` (or `email_change`)
- Failure: `#error=…&error_code=otp_expired&…`, sometimes as `?error=…`

The tokens are a live login session. The page **never reads, stores or sends
them**, wipes them from the address bar immediately (`history.replaceState`),
and sets `referrer: no-referrer` so they can't leak to another site. Fonts are
self-hosted, so the page makes no third-party requests at all.

## Brand

Beige `#f2ece0`, Ochre `#d2543f`, Stone `#6e685c`, Ink `#201e19`; Geist.
Same rules as the app: no white, no all-caps, English only.
