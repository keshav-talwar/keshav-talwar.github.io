# Project log: keshav-talwar.github.io
<!-- last-updated: 2026-11-22T09:11:10Z (maintained by /updaterepo) -->

## Current state
- Single static page `index.html` (no build step): fixed left sidebar (KT avatar placeholder, name,
  email, nav, GitHub/LinkedIn/email icons, Dark/Light toggle), sections About / News / Research /
  Projects / Experience & Education / Skills. Inter font, navy accent `#1e3c78`, dark mode via
  `data-theme` + `prefers-color-scheme`, News "Show more" expander, active-section nav highlight.
- Layout modelled on https://sukratii.github.io (structure only; own palette and content).
- Content is taken only from verified repo facts / `69cad…/PROFILE.md`. FLMSec paper shown as
  **Under review** (Keshav's decision, 2026-11-22). Links go only to public repos.
- Verified with Playwright screenshots at 1366px (light + dark) and 390px (mobile): no horizontal scroll.
- **NOT LIVE YET.** Committed locally only; no `origin`. GitHub refuses to create the repo
  ("You have created too many repositories, too quickly"), on CLI and website alike.
  A background job (started 2026-11-22 ~14:45 IST) retries every 10 min for 24 h, then pushes,
  enables Pages (branch `main`, path `/`) and checks https://keshav-talwar.github.io returns 200.
  It only runs while that Claude Code session stays open.

## Tried: don't repeat
| Approach | Last tried | Result | Why it failed / note |
|---|---|---|---|
| Creating many GitHub repos back-to-back (9 via `gh repo create` in ~3 min) | 2026-11-22 | ❌ Account hit "created too many repositories, too quickly" for hours; blocked this site | Space out repo creation; create the site repo first next time |
| Creating the repo on github.com/new to bypass the limit | 2026-11-22 | ❌ Same error on the website | Limit is per account, not per client |
| Site name `keshavt.github.io` / `keshavtalwar` / `keshavv` | 2026-11-22 | ❌ Usernames taken (keshavt 2014, KeshavTalwar 2020 not Keshav's, keshavv 2016) | User site must equal the GitHub username |
| Username availability check via `gh api users/X -q .login` | 2026-11-22 | ❌ Reported free names as "taken" | A 404 prints JSON to stdout; check the exit code instead |
| Waiting on the old `Keshav-cse.github.io` repo name | 2026-11-22 | ❌ Abandoned | Account renamed to `keshav-talwar`; folder + links updated |
| Driving GitHub settings with Playwright | 2026-11-22 | ⚠️ Not used | Fresh browser isn't signed in; would need password/2FA. Claude in Chrome extension wasn't connected |

## What worked
- Hand-written single-file site + Playwright CLI screenshots for visual checks (`npx playwright screenshot`, incl. `--color-scheme=dark`) (2026-11-22)
- Renaming the GitHub account `Keshav-cse` → `keshav-talwar` via Settings → Account; all repo remotes updated and pushed (2026-11-22)

## Decisions
- 2026-11-22: domain `keshav-talwar.github.io` (Keshav chose `keshav-talwar` over keeping `keshav-cse`).
- 2026-11-22: keep the FLMSec paper on the public site, labelled "Under review".
- 2026-11-22: own navy palette instead of the reference site's terracotta; Inter font kept.
- 2026-11-22: removed unverifiable dates (when Keshav joined SR DTU).

## Open questions / next steps
- [ ] Get the repo created once GitHub lifts the limit (or run "push the site" in a new session):
      `gh repo create keshav-talwar/keshav-talwar.github.io --public --source . --remote origin --push`,
      then `gh api -X POST repos/keshav-talwar/keshav-talwar.github.io/pages -f "source[branch]=main" -f "source[path]=/"`
- [ ] Add a real photo (`assets/photo.jpg`, replace the `KT` placeholder).
- [ ] Add the steer-to-C spoofing demo GIF (in `gnss-spoof-lab/media/`) to the Research section?
- [ ] Update when the paper's review outcome is known.

## History
### 2026-11-22: site built, renamed, waiting on GitHub
- Did: built `index.html` from the reference layout; marked paper "Under review"; renamed account to
  `keshav-talwar` and moved folder `Keshav-cse.github.io` → `keshav-talwar.github.io`; updated links.
- Result: renders correctly (desktop, dark, mobile). Not published: repo creation rate-limited all afternoon.
- Learned: bulk repo creation triggers a long GitHub limit; GitHub user-site name must equal the username.
