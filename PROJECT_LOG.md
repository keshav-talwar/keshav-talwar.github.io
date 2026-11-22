# Project log: keshav-talwar.github.io
<!-- last-updated: 2026-11-22T10:22:12Z (maintained by /updaterepo) -->

## Current state
- Single static page `index.html` (no build step): fixed left sidebar (KT avatar placeholder, name,
  email, nav, GitHub/LinkedIn/email icons, Dark/Light toggle), sections About / News / Research /
  Projects / Experience & Education / Skills. Inter font, navy accent `#1e3c78`, dark mode via
  `data-theme` + `prefers-color-scheme`, News "Show more" expander, active-section nav highlight.
- Layout modelled on https://sukratii.github.io (structure only; own palette and content).
- Content is taken only from verified repo facts / `69cad…/PROFILE.md`. Paper shown as
  **Manuscript · not yet submitted** (it was never submitted; no 'lead author' / 'under review'). Links go only to public repos.
- Verified with Playwright screenshots at 1366px (light + dark) and 390px (mobile): no horizontal scroll.
- **LIVE** at https://keshav-talwar.github.io since 2026-11-22 14:51 IST (GitHub Pages, branch `main`, path `/`,
  HTTPS enforced). Pushing to `main` redeploys in about a minute.

## Tried: don't repeat
| Approach | Last tried | Result | Why it failed / note |
|---|---|---|---|
| Naming the target venue (FLMSec / NeurIPS workshop) on the site, CVs or docs | 2026-11-22 | ❌ removed at Keshav's request | Paper isn't submitted; don't name a venue anywhere public |
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
- 2026-11-22: link every project to its repo. Made public: f1-race-predictor, chess-engine, rag-prototype, px4-gz-custom-sim
  (history scanned for keys first: clean). Kept private, marked "available on request": the paper + its code, and the GNSS
  spoofing repos (gnss-spoof-lab, Spoofing-of-drone-in-simulation). Human detection and OS-lab code have no public repo.
- 2026-11-22: domain `keshav-talwar.github.io` (Keshav chose `keshav-talwar` over keeping `keshav-cse`).
- 2026-11-22: keep the paper on the site, labelled "Manuscript · not yet submitted" (the earlier "Under review" label was wrong).
- 2026-11-22: own navy palette instead of the reference site's terracotta; Inter font kept.
- 2026-11-22: removed unverifiable dates (when Keshav joined SR DTU).

## Open questions / next steps
- [ ] Add a real photo (`assets/photo.jpg`, replace the `KT` placeholder).
- [ ] Add the steer-to-C spoofing demo GIF (in `gnss-spoof-lab/media/`) to the Research section?
- [ ] Update when the paper's review outcome is known.

## History
### 2026-11-22 (later): venue mentions removed
- Did: removed every FLMSec mention from the site; paper .tex files and README.txt left untouched (they're the manuscript itself)

### 2026-11-22 (later): research journey section
- Did: added a "Research Journey" section (8-step timeline with kept/dropped ideas, pilot probe summary, next steps)
  from the Research_progress Overleaf doc (`6b02ad8b…/main.tex`), plus nav link and a news item.
- Decision: the public page keeps the probe findings at summary level with limitations; jailbreak screenshots and
  harmful outputs stay in the private Overleaf write-up.
### 2026-11-22: site built, renamed, waiting on GitHub
- Did: built `index.html` from the reference layout; labelled the paper (later corrected to "manuscript, not yet submitted"); renamed account to
  `keshav-talwar` and moved folder `Keshav-cse.github.io` → `keshav-talwar.github.io`; updated links.
- Result: renders correctly (desktop, dark, mobile). Repo creation was rate-limited for ~1 h; the retry job got through at 14:51 IST and the site went live (HTTP 200).
- Learned: bulk repo creation triggers a long GitHub limit; GitHub user-site name must equal the username.
