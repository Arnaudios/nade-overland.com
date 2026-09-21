# nade-overland.com

The website for [Nade](https://nade-overland.com), camping spots mapped by people on the road.

One static page, served by GitHub Pages. It has two jobs:

1. **Homepage** — what Nade is.
2. **Landing page after an email link.** Supabase redirects here (it is the
   project's Site URL) once someone clicks the link in a sign-up or
   email-change message. The confirmation has already happened on Supabase's
   side by then; this page only says so.

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
