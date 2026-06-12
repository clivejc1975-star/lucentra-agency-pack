# Bodhi — 5-Minute Demo Video Script

**Narrator:** Chloe (voice: Kokoro `bf_emma`, British female — same voice as the Lucentra app).

**Session 82+ AUDIT PASS verification (2026-05-29):** Bodhi receipts available for script: 35+ self-heal commits on Lucentra main + 32-audit forensic chain executed during single session + Rule 91 7-layer architecture operational + plug-and-play `npx bodhi-init` (Session 54) + independent £5-50M valuation tier 7-of-10 gates green. Master register: `docs/audits/AUDIT_INDEX.md`.
**Audience:** engineering leaders evaluating Bodhi for their own production codebase. CTOs, VPEs, Head of Engineering, Staff+ engineers with buying influence.
**Runtime target:** 5:00 exact. ~750 words total narration.
**Structure:** 15 scenes of 18-22s, each with (a) narration, (b) screenshot/recording spec, (c) motion direction, (d) caption.
**Tone:** technical, specific, forensic. No marketing adjectives. Every number source-cited to the production Command Center dashboard or a git-log commit reference.

---

## Scene 1 — 0:00 to 0:18 (cold open — the problem)

**Narration (Chloe):**
> Every production web app accumulates quality debt between sprints. Empty loading states. Broken charts after schema migrations. Layout breaks on specific mobile viewports. Your team catches ninety percent. The other ten percent compounds.

**Screenshot:** montage of 3 real broken-render before-states from Lucentra pre-Bodhi fixes (empty dashboard void, NaN in chart, dead-button state).
**Motion:** quick cuts between the 3 broken states, each visible ~5s.
**Caption:** "quality debt compounds between sprints."

## Scene 2 — 0:18 to 0:40 (what Bodhi is)

**Narration (Chloe):**
> Bodhi is an autonomous code-quality loop. UK patent pending. It runs on a schedule against your production repository. It detects the ten percent your team misses. It ships the surgical fix as a pull request. You review and merge — or Bodhi merges itself, once you trust it.

**Screenshot:** Bodhi Suite concept slide (`/bodhi-concept.png`).
**Motion:** slow zoom-in on the architecture diagram 1.0× → 1.08×.
**Caption:** "Bodhi — autonomous quality loop · patent pending."

## Scene 3 — 0:40 to 1:02 (the four-phase loop)

**Narration (Chloe):**
> Four phases per scan. Detect — thirteen detector classes running Claude Vision against real production pages. Diagnose — Claude reads your code, produces a surgical fix. Verify — nine-layer quality gate rejects fixes that don't converge. Ship — surgical pull request against your branch.

**Screenshot:** Bodhi scan workflow running — `bodhi-scan.yml` GitHub Actions panel showing Phases 0 through 7 with green checkmarks.
**Motion:** scroll down the Actions panel revealing each phase.
**Caption:** "detect · diagnose · verify · ship."

## Scene 4 — 1:02 to 1:24 (detectors A through M)

**Narration (Chloe):**
> Thirteen detectors. Console errors. Density violations. Chloe-overlap. Dead buttons. Missing empty states. Responsive breaks. Chart rendering. Dark patterns. Emergency gates. Each detector has a JSDOM meta-test — Bodhi catches its own drift before it catches yours.

**Screenshot:** `tests/visual-qa/visual-audit.spec.ts` with Check A through Check M code visible.
**Motion:** scroll through the detector file showing each Check being highlighted.
**Caption:** "13 detectors · 75 deterministic predicates · self-audited."

## Scene 5 — 1:24 to 1:46 (the 9-layer quality gate)

**Narration (Chloe):**
> Every fix passes nine layers before it reaches your branch. Search-string match. Normalised whitespace match. Component-count check. Declaration-dedup check. Size-explosion check. Test-suite check. Type-check. CANON convergence check. Quality score delta. One layer fails, the fix is rejected. Bodhi iterates.

**Screenshot:** `src/lib/self-healing/ceiling-seeker.ts` showing the 9-layer protection list as comments or code.
**Motion:** slow scroll revealing each layer annotation.
**Caption:** "9-layer gate · zero-regression record · 6 weeks live."

## Scene 6 — 1:46 to 2:08 (the Command Center)

**Narration (Chloe):**
> Your Command Center. Every scan, every fix, every metric — one dashboard. Suite effectiveness rolls up precision, fix rate, mean-time-to-fix, regression rate, cost per fix. Product convergence rolls up your own code's quality score over time.

**Screenshot:** `/admin/bodhi-command-center` dashboard full-page showing Suite Effectiveness Ledger + Product Convergence Ledger + Health Score gauge.
**Motion:** pan top-to-bottom across the dashboard over 22s.
**Caption:** "one dashboard · two ledgers · hands-off."

## Scene 7 — 2:08 to 2:30 (health score + trend)

**Narration (Chloe):**
> The health score aggregates five dimensions — precision, fix rate, mean time to fix, regression rate, cost per fix. A single number from zero to one hundred. Every scan rolls a row. Ten weeks of history, continuous trend line, you see the direction of travel.

**Screenshot:** Health Score gauge + TimelineChart with 10-week continuous trend line visible.
**Motion:** zoom into the health score number, then pan along the trend line left-to-right.
**Caption:** "86 out of 100 · 10-week trend · live production data."

## Scene 8 — 2:30 to 2:52 (real autonomous commits)

**Narration (Chloe):**
> Every commit shipped by Bodhi lives in your git log under the bodhi-convergence-bot identity. Twenty-seven plus autonomous pull requests merged. Zero regressions across six weeks. Every commit is yours to inspect — no black box.

**Screenshot:** GitHub commits filtered by `author:bodhi-convergence-bot` showing a list of merged commits with SHAs + timestamps + file deltas.
**Motion:** scroll the commit history revealing commit messages.
**Caption:** "bodhi-convergence-bot · git-log proof · customer-owned repo."

## Scene 9 — 2:52 to 3:14 (ninety-second install)

**Narration (Chloe):**
> Install is one command. Npx bodhi-init. The CLI asks seven questions — your Anthropic key, your GitHub token, your scan cadence. It writes the workflow files. It writes the config file. Your first scheduled scan runs inside thirty minutes.

**Screenshot:** terminal screen-recording of `npx bodhi-init` wizard running through its 7 prompts.
**Motion:** real-time terminal capture showing each prompt + response.
**Caption:** "npx bodhi-init · 90 seconds · zero runtime dependencies."

## Scene 10 — 3:14 to 3:36 (review mode first)

**Narration (Chloe):**
> First two weeks run in review mode. Every fix is a pull request for your engineer to approve. You watch Bodhi work. You see the fix diff. You learn the quality. Then — and only then — you flip auto-merge on.

**Screenshot:** example Bodhi PR on GitHub showing diff + Vercel preview deploy link + CI checks green.
**Motion:** slow scroll through PR page showing diff + comments + checks.
**Caption:** "review mode 14 days · trust ramp · your call."

## Scene 11 — 3:36 to 3:58 (the 5 tiers)

**Narration (Chloe):**
> Five tiers. Starter — one hundred scans a month, two ninety-nine. Team — five hundred scans, fourteen ninety-nine, most popular. Growth — two thousand five hundred. Enterprise — ten thousand. Dedicated — negotiated. Every tier kill-switched at four times quota. Every tier loss-proof.

**Screenshot:** Bodhi pricing ladder from `bodhi.lucentra.app/pricing` or the pitch-pack unit-economics table.
**Motion:** slow pan across the 5 tier cards.
**Caption:** "5 tiers · kill-switch protected · 89-94% gross margin."

## Scene 12 — 3:58 to 4:20 (rejection learning + self-improvement)

**Narration (Chloe):**
> Bodhi learns from its own rejections. When your team rejects a fix, the reason is captured. Future diagnoses for that file include the rejected pattern. Bodhi doesn't make the same mistake twice. The detector themselves can be improved by Bodhi under strict contract — the system fixes the system.

**Screenshot:** Supabase `bodhi_rejection_patterns` table or `bodhi_knowledge` file-list showing Rule 91 Layer 4 architecture.
**Motion:** zoom-in on the rejection-learning feedback loop diagram.
**Caption:** "Rule 91 · the system fixes the system · Layer 4."

## Scene 13 — 4:20 to 4:42 (the 60-day pilot offer)

**Narration (Chloe):**
> Lucentra AI Ltd is picking a small number of friendly teams for a thirty-day free pilot. Six months of Team tier free after the case study publishes. You keep your repository, your engineers, your control. You gain an autonomous quality loop against your own code.

**Screenshot:** `bodhi.lucentra.app/pilot` landing page showing the 30-day pilot offer details.
**Motion:** slow zoom-in on the pilot CTA button.
**Caption:** "30 days free · 6 months Team tier free · bodhi.lucentra.app/pilot."

## Scene 14 — 4:42 to 4:58 (the moat)

**Narration (Chloe):**
> Patent pending in the UK. Fifteen months of production scans against our own consumer app. Over ninety-six operating rules encoded in the pipeline. Six-week zero-regression record. Every claim you just heard — verifiable in our public repository.

> **Out-of-scope note (2026-05-13):** the Bodhi UK provisional referenced in this video was filed 2026-04-08 (non-provisional / PCT due 2027-04-08). Two additional UK provisional patents were filed at the UK IPO on 2026-05-13, both in joint Clive Chattey + Jenny Olsson-Chattey names: the Lucentra consumer-app cross-domain centralisation engine (application **GB2611164.1**) and the BMS real-time AI-scored meeting evaluation apparatus (application **GB2608130.7**). Both are out of scope for this Bodhi-focused video script but are visible to reviewers via `/patent-figures/`, `/bms-patent-figures/`, and the partnership-pack documentation.

**Screenshot:** GitHub `lucentra-ai/Lucentra` repository landing page showing the README + CLAUDE.md + data-room folder.
**Motion:** scroll through the repo structure.
**Caption:** "verifiable · public · reproducible."

## Scene 15 — 4:58 to 5:00 (close)

**Narration (Chloe):**
> Bodhi. Your code — watched, healed, shipped.

**Screenshot:** Bodhi wordmark over a gradient background + the slogan animating in.
**Motion:** slow pull-back 1.15× → 1.0× + wordmark fade-in to 100%.
**Caption:** "bodhi.lucentra.app"

---

## Production notes (same rig as Lucentra script)

**Audio:**
- Kokoro `bf_emma` voice throughout — same narrator across both videos signals brand coherence.
- -3dBFS peak normalised per TTS call, -16 LUFS final track.
- 500ms fade-in + 300ms fade-out per scene.

**Video:**
- 1920×1080, 30fps, H.264 MP4, ~18 MB final file size.
- Ken Burns + cross-fade + terminal-capture for Scene 9.
- Scenes 3, 8, 10 use real GitHub screenshot capture (not mocked).

**Branding:**
- Bodhi wordmark bottom-right, 0.6 opacity, 40px.
- Captions Inter 24px white on 0.4 black backdrop.
- No background music.

## Rule 43 flags

1. **Scene 3 requires the workflow to be currently running or have recently run.** If no recent scan exists to capture, render a post-hoc screenshot from a completed run. Accept this fallback — the video is evergreen, the screenshot is a snapshot.

2. **Scene 8 "27+ autonomous PRs" count is Session 56-era.** Update the script every 30 days as the count grows — a video claiming "27+" when the real count is 87 looks dated. Auto-populate from GitHub PR count filtered by author at render-time.

3. **Scene 11 pricing must stay in sync with `src/lib/bodhi/quota.ts`.** Pre-render check validates the numbers.

4. **Scene 14 "96 operating rules" is Session 52-era (Rule 96 is the last).** Update if new rules are added.

5. **The Scene 13 pilot offer ("30 days free") must match the live contents of `bodhi.lucentra.app/pilot`.** Do not render the video until the pilot landing page is live. Blocker: the pilot page needs to exist as a live URL.

6. **Bodhi-convergence-bot commit filter URL changes when GitHub repo migrates to `lucentra-ai` org.** Re-render the video after the org migration to update the URL shown in Scene 8.

7. **Terminal recording in Scene 9 requires an actual macOS or Linux terminal capture.** Playwright-only cannot record terminal UI. Use `asciinema` to record the terminal session + convert to video. Script needs to stage a fresh install against a throwaway directory.

8. **The video positions Bodhi before Lucentra AI Ltd is incorporated.** If the pilot offer or MSA requires legal signature, references in Scenes 12-13 must match the incorporation date. Do not publish the video before Ltd incorporates.
---

## Session 85 addition (2026-06-05) — self-improvement is now a headline

Add to the Bodhi demo: the suite now learns from HUMAN triage — when a reviewer closes a self-heal PR as a false positive, that judgement is recorded into the rejection-learning store the diagnoser reads, so the next scan avoids the wrong file. Talking point: "Bodhi doesn't just fix your repo while you sleep — it gets measurably more accurate every cycle, from its own gates AND from human review. Always better than last time."
