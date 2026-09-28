# Auto Finance website

This repository contains a static Auto Finance website. `index.html` is the entry point for GitHub Pages; `auto-finance.html` is the original copy of the same page. The separate [privacy policy](privacy-policy.html) can be linked directly from Meta Ads.

After GitHub Pages is enabled with **GitHub Actions** as the source, the site is available at `https://focuseditor93-alt.github.io/auto-finance/` and the policy at `https://focuseditor93-alt.github.io/auto-finance/privacy-policy.html`.

## Authentication and enquiry flow

There is no customer account or website authentication component. The site has no login page, server, database, session cookie, API key, password, or access token in its HTML or JavaScript. GitHub Pages serves the public files to visitors without a sign-in.

1. A visitor loads `index.html` from GitHub Pages. The browser displays the embedded images and CSS; the only site JavaScript handles the mobile menu and the enquiry form.
2. When the visitor submits `#leadForm`, its `submit` handler calls `preventDefault()`, reads the name, phone, car or budget, and message fields, and builds a WhatsApp message.
3. The handler uses `encodeURIComponent(text)` and opens `https://wa.me/917736150713?text=...` in a new tab. The page does not POST the details to this repository or save them in browser storage. The draft text is present in the outgoing URL, and WhatsApp handles any message the visitor chooses to send.
4. The `tel:` links ask the device to place a call. `7736150713` is the public contact number, not a credential or token.

The [Pages workflow](.github/workflows/pages.yml) runs on pushes to `main`. GitHub supplies a short-lived `GITHUB_TOKEN` to the workflow. Its declared permissions are `contents: read`, `pages: write`, and `id-token: write` so the official Pages actions can upload and deploy the site. The workflow does not put that token in the site files or require a stored personal access token. Visitors never receive GitHub credentials. The `id-token` permission supports GitHub's deployment identity check; it is not a customer sign-in token.

The [privacy policy](privacy-policy.html) describes the current static site's handling of enquiries and links to third-party services. Review it before adding analytics, pixels, server-side forms, or a lender application flow.
