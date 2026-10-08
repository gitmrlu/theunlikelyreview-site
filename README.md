# The Unlikely Review: OAuth homepage and privacy policy (static site)
Files: `index.html` (homepage), `privacy.html` (privacy policy), `style.css`. There's no JavaScript, cookies or trackers.

**Before publishing:** replace `[CONTACT EMAIL: TO BE ADDED BEFORE PUBLISHING]` in both HTML files (one place each).

## Hosting options (free, stable HTTPS)
**A. GitHub Pages.** Needs a GitHub account.
1. On the box, run `gh auth login`. Maxwell approves via the device code.
2. Then run:
   `gh repo create unlikely-review-site --public --source . --push`
   `gh api -X POST repos/{owner}/unlikely-review-site/pages -f 'source[branch]=main' -f 'source[path]=/'`
3. URLs:
   - `https://<user>.github.io/unlikely-review-site/`
   - `https://<user>.github.io/unlikely-review-site/privacy.html`

**B. Firebase Hosting.** Uses Maxwell's existing Google account and his Google Cloud project, with no new account and no billing.
1. Run `npx firebase-tools login --no-localhost`. Maxwell approves.
2. Run `npx firebase-tools deploy --only hosting --project <gcp-project-id>`. Firebase must first be added to the project in the Firebase console.
3. URL: `https://<project-id>.web.app/` and `/privacy.html`.

**C. Google Sites.** Uses Maxwell's existing Google account, no CLI. Paste the text of both pages into a new site at sites.google.com and publish it. URL: `https://sites.google.com/view/<name>`.

**Domain note:** Google's *verification* process (only needed if the app is ever opened to other users) requires the homepage to be on a domain you own and have verified in Search Console. A custom domain such as theunlikelyreview.com works for that. A shared host domain like sites.google.com doesn't. For owner-only use in "In production" without verification, any public HTTPS URL is fine.
