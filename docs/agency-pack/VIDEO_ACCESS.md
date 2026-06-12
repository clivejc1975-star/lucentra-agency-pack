# Demo video access

Lucentra ships two 5-minute demo videos as part of this first-contact pack: one for Lucentra (the consumer longevity app) and one for the autonomous quality pipeline that maintains its codebase. Both videos are rendered from the scripts in this repo (`LUCENTRA_5MIN_DEMO_SCRIPT.md` and `BODHI_5MIN_DEMO_SCRIPT.md`) using the production app's own assets, voices, and screen captures.

The MP4 outputs are too large to commit to git, so they are hosted separately. Choose whichever access channel fits.

## Channel 1 — direct link (recommended for reviewers) — LIVE

The rendered versions of both videos are hosted at:

- **Lucentra 5-min demo:** [`https://lucentra-delta.vercel.app/videos/lucentra-5min-demo.mp4`](https://lucentra-delta.vercel.app/videos/lucentra-5min-demo.mp4) (~16 MB MP4)
- **Autonomous quality pipeline 5-min demo:** [`https://lucentra-delta.vercel.app/videos/bodhi-5min-demo.mp4`](https://lucentra-delta.vercel.app/videos/bodhi-5min-demo.mp4) (~10 MB MP4)

These URLs are link-shareable — anyone with the URL can stream or download. No login, no collaborator invite. Suitable for forwarding to colleagues inside an agency for review. Both videos open directly in any modern browser (HTML5 video) and can be saved locally for offline review.

## Channel 2 — read the scripts

Both 5-minute scripts are committed to this repo and are fully agency-agnostic:

- `docs/videos/LUCENTRA_5MIN_DEMO_SCRIPT.md` — Lucentra consumer-app walkthrough, 15 scenes, every voice-over line, every screen capture timestamp, every transition cue
- `docs/videos/BODHI_5MIN_DEMO_SCRIPT.md` — autonomous-quality-pipeline walkthrough, 13 scenes including the PERFECTION IP-moat reveal

Reading the scripts gives the same narrative shape as watching the video. A reviewer can form a first-pass opinion of whether the product story fits their agency's specialism without needing the rendered MP4 in hand.

## Channel 3 — regenerate the videos yourself (technical reviewers only)

The full render pipeline is included in the source repo (`scripts/video/` + `.github/workflows/generate-demo-video.yml`). Anyone with a GitHub Actions runner and Anthropic API access can regenerate the videos from scratch in ~15–20 minutes per video.

This channel is only useful for technical reviewers who want to audit the pipeline itself; agencies in evaluation typically use Channels 1 or 2.

## What's in each video

### Lucentra 5-min demo
Cold open · the longevity-companion thesis · three AI companions (Chloe, James, Flavio) and how they differ · live dashboard with longevity ring + life-score trend · health pillar including blood-test photo upload + biomarker tracking + Apple Health + wearables · money pillar with UK open-banking via TrueLayer + budget categorisation + FIRE projection · mind pillar with seven therapy modes + meditation + journaling · cross-domain intelligence engine sample (how stress affects sleep affects spending affects longevity) · annual letter generation in the user's chosen companion's voice · pricing tiers · close on the founder's brief.

### Autonomous quality pipeline 5-min demo
Cold open · the problem (consumer apps degrade between releases, regression bugs are visible to users before engineers see them) · the pipeline architecture (visual detector → severity classifier → diagnosis → surgical fix → quality gate → merge → ledger) · live install on a fresh repo · scan demo showing detection of a real visual bug · autonomous fix shipped end-to-end with no human intervention · the PERFECTION IP-moat slide (UK provisional patent filed 8 April 2026, non-provisional due April 2027) · ledger-trace receipts (50+ autonomous PRs shipped, 0 regressions, 6+ weeks of clean runs) · close on the licensing / standalone product opportunity.

**Out-of-scope note (added 2026-05-13):** This Bodhi-focused video references only the Bodhi UK provisional patent that's the subject of the PERFECTION IP-moat slide. Two additional UK provisional patents have since been filed at the UK IPO on 2026-05-13 covering the Lucentra consumer-app cross-domain centralisation engine (application GB2611164.1) and the BMS real-time AI-scored meeting-evaluation apparatus (application GB2608130.7) — both joint Clive Chattey + Jenny Olsson-Chattey, pending assignment to Lucentra AI Ltd. These two are out of scope for this Bodhi video but visible to agency reviewers via `/patent-figures/`, `/bms-patent-figures/`, and the partnership-pack documentation.

---

**Document version:** 1.0 (drafted 2026-05-11).
**Owner:** Lucentra AI Ltd · company number 17174304 · England and Wales.
**Status:** First-contact light. Distribute under NDA only.
