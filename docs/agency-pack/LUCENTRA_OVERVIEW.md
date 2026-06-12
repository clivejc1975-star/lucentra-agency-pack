# Lucentra — Product Overview

**One-paragraph version:** Lucentra is an AI longevity companion app. It tracks, analyses, and advises across health, wealth, mind, relationships, purpose, and career — the six domains that affect how long and how well a person lives. Three AI companions (Chloe, James, Flavio) with distinct voices and personalities deliver the experience. The web app is live at lucentra-delta.vercel.app and the iOS build is in TestFlight running user-acceptance testing ahead of App Store launch. Commercial infrastructure is in place — Stripe (four price tiers from £19.99 to £44.99 per month plus add-on credit packs) and Apple IAP — tested and ready to activate at launch. Built on Next.js, Supabase (EU/Ireland), Vercel Pro, Claude Sonnet, Stripe, and Twilio. Three UK provisional patents filed: Bodhi autonomous quality pipeline (2026-04-08); Lucentra app cross-domain centralisation engine GB2611164.1 (2026-05-13); BMS real-time AI-scored meeting evaluation GB2608130.7 (2026-05-13). All three in joint Clive Chattey + Jenny Olsson-Chattey names pending assignment to Lucentra AI Ltd.

---

## What it is

Lucentra is a consumer subscription application aimed at the longevity-curious adult market — people who want to live longer and healthier and are willing to pay for tooling that helps them do it. The product positions live-longer alongside live-better as a single integrated promise: tracking quality of life across six interlocking domains rather than treating health, money, and mind as separate apps.

The headline KPI for the user is **projected lifespan in years**, with sub-metrics for life-quality across each of the six domains. Every interaction in the app feeds the model that calculates this number.

## What's built and live today

- **Web app:** live at `https://lucentra-delta.vercel.app` — accessible to anyone with the URL
- **iOS:** in TestFlight running user-acceptance testing (Apple Developer account active, App Store submission pending UAT completion)
- **Payment processing:** Stripe configured live (4 subscription tiers + 4 add-on credit packs, products + prices + webhooks tested end-to-end, ready to activate at App Store launch)
- **In-app purchase:** Apple IAP registered (same 4 tiers + 4 add-on packs, server-side receipt verification wired)
- **Notifications:** Twilio SMS active (3 to 50 SMS / month tier-dependent)
- **Database:** Supabase Pro tier, EU region (Ireland), 57+ tables with RLS
- **CDN + hosting:** Vercel Pro
- **AI backend:** Anthropic Claude Sonnet (current model), prompt caching enabled

**Current commercial state:** no paying users yet — closed-beta TestFlight UAT with founder + small testing pool. Revenue starts at App Store launch.

## Three AI companions

Each companion is a distinct persona with its own voice, system prompt, conversational style, and voice-clip library. The user chooses one at onboarding and can switch later. The same product experience runs through whichever companion the user selected — what changes is the tone of the conversation, the humour, the warmth.

- **Chloe** — warm British female. The default companion for most users. Kokoro `bf_emma` voice.
- **James** — dry British male wit. The Wilde-Churchill-Connery blend with light playfulness. Kokoro voice.
- **Flavio** — flamboyant camp male warmth. The companion users pick when they want playful directness with affection. Kokoro `bm_daniel` voice.

All three operate on the same Claude Sonnet backbone with companion-specific system prompts. None of the companion files have been changed since they were locked in production — change requires explicit per-file per-session approval (institutional rule in the codebase).

## What sets it apart commercially

1. **Cross-domain intelligence.** The intelligence engines correlate signals across all six domains rather than treating them as silos — fatigue affects mood affects spending affects sleep affects fatigue. The cross-correlation is the moat versus single-domain competitors (fitness app, money app, journal app).

2. **Three-persona architecture.** Users build a relationship with a specific companion over time. Switching costs are emotional, not just data. Most consumer wellness apps run one voice; Lucentra runs three.

3. **Autonomous quality pipeline.** A patent-pending pipeline (codename Bodhi, UK provisional filed 2026-04-08; separate concept slide) watches every Vercel deploy, identifies regressions before users see them, and ships surgical fixes autonomously. This is the system that keeps the app to a senior-engineering quality bar without a senior-engineering headcount. Two additional UK provisional patents filed 2026-05-13 protect the Lucentra app's cross-domain centralisation engine (GB2611164.1) and the BMS real-time AI-scored meeting evaluation apparatus (GB2608130.7) — full drawings at `/patent-figures/` and `/bms-patent-figures/`.

4. **Premium pricing power.** Top tier at £44.99 / month (or £449 annual saving £90) is the most expensive consumer wellness app of this category — and the metrics support it. Blended gross margin sits at 63.8% at 30% usage, every paid tier is loss-proof at 100% worst-case usage.

## What's NOT in this overview

This document is deliberately light. Materials covering commercial unit economics, the intelligence-engine architecture, the autonomous quality pipeline internals, the patent application, internal session continuity, business plan, and competitive analysis are **not** in this agency-pack mirror. They become available after NDA execution.

## Open questions a partner agency would naturally ask

The following are pre-answered for a first conversation; deeper detail is post-NDA.

**Q: What's done vs. what's left to ship?**
A: ~85% to App Store quality. Remaining work spans App Store submission iteration, design polish to senior-design-firm standard, growth marketing infrastructure, ongoing support tooling. Detailed scope discussed post-NDA.

**Q: What's the partner's role?**
A: Design polish + App Store submission + post-launch debug + marketing + ongoing maintenance for the duration. Product direction, IP, and database stay with Lucentra AI Ltd.

**Q: How is the engagement structured commercially?**
A: Open — revenue share or equity considered, structured to minimise or remove upfront cash. Specific terms negotiated post-NDA based on engagement scope and walk-away clauses both ways.

**Q: How big is the company?**
A: One founder full-time (non-technical, directs Claude Code). One part-time co-founder (operations). All engineering is AI-assisted; the codebase is documented end-to-end. The agency would not be onboarding a team — they would be onboarding a single founder and a well-documented codebase.

**Q: What's the longest-running risk for the agency?**
A: Founder dependency. Mitigated by ~6,700 lines of versioned operating documentation that lets another AI-assisted operator (or another agency) take over without context loss. Available post-NDA.

---

**Document version:** 1.0 (drafted 2026-05-11).
**Owner:** Lucentra AI Ltd · company number 17174304 · England and Wales.
**Status:** First-contact light overview. Agency-agnostic. Distribute under NDA only.


## Sessions 86–87 update (2026-06-12) — The Concierge Suite (Pro+): the companion ACTS

The persona now acts on the user's behalf with the user's tap as the only
authorisation: researched **Handoff Cards** (→ user clicks Pay; identity-only
autofill, payment fields denylisted), **email drafts placed in the user's REAL
Drafts folder**, **calendar events written directly** on spoken confirmation,
and **real phone calls in the persona's own cloned, legally-disclosed voice**
("Hi, I'm Chloe, [user]'s personal AI assistant…") — safety rails proven by
executable tests (no payments/contracts, no emergency numbers, read-back),
deterministic transcripts, replies relayed back into chat, billed at provider
cost × 2 from prepaid credit (£10/£20 packs). Proven live 2026-06-12 on a real
call. Feature count 87 → 93 at Pro+; no competitor occupies this intersection.
