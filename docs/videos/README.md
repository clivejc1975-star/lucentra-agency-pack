# Lucentra + Bodhi Demo Video Pipeline

**Purpose:** generate world-class narrated 5-minute product demo videos for Lucentra and Bodhi, using Chloe's production voice + real app screenshots + ffmpeg-polished motion + captions. One-click runnable from GitHub Actions by a non-technical user.

**Session 82+ AUDIT PASS context (2026-05-29):** every video claim should be forensically backed per audit chain. Highlights: 87 features Pro+ (audit #16), value ratio 1.33-2.28× vs competitor stack (audit #31), Apple submission READY_FOR_REVIEW (audit #29), Pillar 12 memory bond moat (audit #30), Bodhi autonomous loop with 35+ self-heal commits. Master register: `docs/audits/AUDIT_INDEX.md`.

**Output quality:** 1920×1080, 30fps, H.264 MP4, ~15-18MB per video, Chloe narrator (Kokoro `bf_emma`), -16 LUFS broadcast-normalised audio, Ken Burns zoom motion, cross-fades, wordmark overlay.

**Clive's action:** 4 clicks + 15-20 minute wait + download.

---

## How to generate a video

1. Go to `github.com/<org>/Lucentra/actions`.
2. Click "Generate Demo Video" in the workflow list (left sidebar).
3. Click "Run workflow" (right side).
4. Pick `lucentra` or `bodhi` from the dropdown.
5. (Optional) Override the base URL if rendering from a non-production deploy.
6. Click the green "Run workflow" button.
7. Wait ~15-20 minutes. Refresh the page to see live progress.
8. When green, scroll to the bottom of the run page — download the artefact named `<product>-demo-video-<run-number>`.
9. Unzip. Inside is `<product>-demo-5min.mp4`. That's the video.

## What each artefact contains

- **`<product>-demo-video-<run-number>`** — the finished 5-min MP4 ready for distribution.
- **`<product>-demo-source-<run-number>`** — diagnostic artefact containing the 15 captured frames + 15 generated WAV files + intermediate ffmpeg scenes. Useful if the final MP4 has an issue with a specific scene — inspect the source, identify the problem, regenerate.

## Regenerating

Every run costs ~£0.50-£1.00 in Kokoro TTS calls + GitHub Actions compute. Regenerate as many times as needed to get a result Clive is happy with. If the pipeline needs to change (different voice, different scene order, different pacing), edit the matching script in `docs/videos/` or `scripts/video/` and re-trigger the workflow — no CI waiting, no deployment gates.

## The 6 files that compose the pipeline

| File | Purpose | Lines |
|---|---|---:|
| `docs/videos/LUCENTRA_5MIN_DEMO_SCRIPT.md` | 15-scene Chloe narration + screenshot spec for Lucentra | ~190 |
| `docs/videos/BODHI_5MIN_DEMO_SCRIPT.md` | 15-scene Chloe narration + screenshot spec for Bodhi | ~180 |
| `scripts/video/capture-frames.ts` | Playwright captures 15 scene frames per product | ~100 |
| `scripts/video/generate-narration.ts` | Calls `/api/tts` with Chloe's voice for each scene | ~100 |
| `scripts/video/stitch-video.sh` | ffmpeg 4-stage render pipeline | ~110 |
| `.github/workflows/generate-demo-video.yml` | One-click wrapper | ~145 |

## Quality bar

- **Chloe's voice:** same Kokoro `bf_emma` config users hear in the app. No voice cloning, no synthesised stand-in, no AI-vibe text-to-speech that screams "robot."
- **Screenshots:** real production pixels captured at 2× DPI. No mockups, no Figma frames, no synthetic renderings.
- **Motion:** Ken Burns zoompan per scene (1.0× → 1.08× over scene duration), cross-fades between scenes (500ms), audio fade-in/out (500ms/1s).
- **Audio normalisation:** -16 LUFS final track per broadcast standard (EBU R128 / ATSC A/85). Per-scene peak-normalised to -3dBFS from `/api/tts`.
- **Captions:** Inter 24px, white text, 0.4 opacity black backdrop. Mobile-readable.
- **Brand:** wordmark overlay bottom-right at 0.6 opacity, 40px height, persistent throughout.

## What this pipeline does NOT produce

- **Cinematic film.** Ken Burns + cross-fades is demo-grade motion, not Hollywood. Agencies expect demo-grade for product walkthroughs; this clears that bar, doesn't clear the festival-film bar.
- **Music-backed narrative.** No background music by default. Script + Chloe's voice + natural pauses carry the piece. Music can be added post-render if needed — royalty-free licence required.
- **Live-action B-roll.** No hands-on-keyboard footage, no founder-on-camera interviews, no user testimonial montage. Strictly structured screenshots + narration.
- **Multi-language.** English only today. Kokoro supports other voices but the scripts would need translation + re-recording.

## Known trade-offs (Rule 43 flags)

1. **Kokoro `bf_emma` is tied to the production TTS server.** If the Kokoro server goes down mid-render, narration generation fails. The pipeline retries each scene once, then emits a diagnostic. Re-trigger the workflow when the server's back.

2. **Scene 5 of the Lucentra script mentions voice conversation "with my voice, on your device, in real time" — this is a spoken claim, not a real-time capture.** We're recording Chloe describing Chloe; the user's screen shows a static ChloeOverlay capture. This is a demo-video convention, not a fidelity issue. If the reviewer probes, show them the live app.

3. **Screenshots dated to the render day** — any pricing or engine-count change after the render invalidates the video. Per-product freshness is tracked at the script level; the script's Rule 43 flags list the specific numeric claims to watch.

4. **Captions are baked into the video (hard-burned).** No subtitle-track export. If translation is ever needed, separate SRT + overlay export would be a follow-up deliverable.

5. **File size ~15-18MB per 5-min video.** Uploads to LinkedIn (file-size limits 5GB so fine), email (most mail servers accept 25MB attachments so fine), YouTube (unlimited so fine). If a specific surface needs sub-10MB, re-render with `-crf 25` in `stitch-video.sh` for smaller output at 80% quality.

6. **No A/B test variants built in.** If Clive wants two script versions to test, duplicate `LUCENTRA_5MIN_DEMO_SCRIPT.md` → `LUCENTRA_5MIN_DEMO_SCRIPT_V2.md` + edit the narration + `generate-narration.ts` to branch on script version. Not built today; buildable in one session.

7. **Video generation is not gated by any guardrail.** The pipeline will render even if tsc fails or jest fails on the current branch — the video is a snapshot of the production deploy, not the branch code. Good: lets you generate a pitch video while fixing a guardrail-failing branch. Bad: it's possible to publish a video from a branch that doesn't ship to production. Sanity check: verify `/api/version` on the base URL matches the branch you expect before shipping externally.

## Post-generation review checklist

Before distributing externally:

- [ ] Watch the full 5 minutes on a laptop at full-screen.
- [ ] Watch muted to check captions + visual pacing.
- [ ] Watch on a phone screen (375px wide) to verify caption readability.
- [ ] Listen through headphones to catch audio glitches / volume jumps.
- [ ] Verify no placeholder UI strings leaked ("Loading...", skeleton states).
- [ ] Verify pricing / engine count / achievement count on-screen matches what Chloe says.
- [ ] Verify final 2-second close lands the wordmark reveal + "Both." / "shipped." word.
- [ ] Export a 30-second teaser cut for social via `ffmpeg -ss 00:00:00 -t 30 -c copy`.

## Distribution surfaces

Post-approval, the videos should land at:

- **`lucentra.app/demo`** — permalink, embed-able.
- **`bodhi.lucentra.app/demo`** — permalink for Bodhi.
- **LinkedIn company page** — post as native video (not link) for max reach.
- **Agency outreach emails** — attach directly or link to permalink.
- **Investor decks** — embed via hyperlink in the one-page summary slide.
- **Pilot onboarding** — include in the pilot-welcome email so customers watch before their first install.

Keep master archive in `docs/videos/archive/v<n>-<YYYY-MM-DD>.mp4` under git-lfs (if set up) or external storage. Maintain a changelog line in this README per major re-render (voice bump, script rewrite, screenshot refresh).
---

## Session 85 addition (2026-06-05) — showcase the new flagship

Add to the demo (and the scene-plan JSON on next render):
- **Longevity Labs** (Health → Longevity) — the differentiator no wearable-only app has: enter grip strength + ApoB + a biological-age result, watch them grade against best-practice ranges and move the Real Age score. Talking point: "Lucentra captures the Attia-grade longevity panel + biological age, not just steps — and fuses it with wealth + mind."
- **Editable / backdated entries** — "forgot to log yesterday? Just tell Chloe, or pick the date." One reading is enough; no blank graphs.
- **Reliability** — manual entries are deploy-proof (can't be clobbered by an auto-sync), and every trend chart now frames the data so a real change is visible.


## v2 capture item (2026-06-12, Sessions 86–87) — the Concierge scene

INSERT (after the cross-domain intelligence scene): the Call Card — ask
"call my wife and tell her I love her" → card appears (disclosure preview +
price) → tap LET MY ASSISTANT HANDLE IT → 3–5s of the real call audio in the
persona's cloned voice → CALL DONE ✓ transcript lands → chat relay line.
NOTE: scene-plan.json is bound to captured screenshots — this scene ships in
the NEXT capture run (MASTER_TODO item; do not hand-edit the scene-plan
without fresh captures or the render breaks).
