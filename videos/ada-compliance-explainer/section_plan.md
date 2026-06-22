# ADA Website Compliance Explainer — Section Plan

## Film Direction

**Palette system:** 60-30-10 on the pin-and-paper native paper base. 60% warm paper canvas (`--canvas`/`--surface-paper` family) — the same warm yellow paper from scene 1 to scene 5, no per-scene drift. 30% hairline + repeated canvas layering (no `--surface` tier exists, so cards use `--anchor-cream` surfaces plus `--border-hairline` rules instead of a fake middle gray). 10% accent reserved for the current focal element only: `--brand-accent` (red) marks risk/urgency beats (demand letters, CTA stamp), `--brand-secondary` (gold) marks the resolution/benefit beats (SEO arrow, audit value). Ink is `--ink` (the brand-primary blue) throughout, doubling as print-like ink on paper. Decorative tints (`--deco-1..4`) appear only as sparse single-dot accents on pinned cards, never as backgrounds. No mesh, no dual-radial swell, no gradients as backgrounds — paper grain (`paper-grain-overlay`) is the only atmosphere, present in every scene at low, consistent density.

**Type roles:** Three-voice system per `voice.md`. Display = hero headlines / DOM keywords, Space Grotesk 700, tight negative tracking, sentence case (never uppercase). Mono = eyebrow chrome / source tags / stamps, DM Mono uppercase with wide tracking. Caveat hand-script = marginal scribble-notes (sentence case, conversational, `pp-underline` for emphasis) and step numerals (hand-drawn 1/2/3, never numeral fonts). Body copy on cards stays in Space Grotesk sentence case, never Caveat. Hierarchy stacks size + weight + case + spacing across every scene (hero word 3:1 over supporting copy minimum).

**Motion defaults + budget:** One macro move per scene (slow drift or push, `EASE.entry`/`power2.out` family from `easings.js`), at most 1-2 secondary live elements (the focal pin/card breathing, or one scribble write-on), everything else rests. Default ambient amplitude: Y ±2-3px, scale ±1-2%, rotation ±0.3-0.8°, 2.5-4s cycles — reach for the higher end only on scene 1 (short, single hero, no competitors) and scene 5 (climax stamp slam). Entries use `EASE.entry`/`DUR.med`; emphasis beats (stamps, pins, reveals) use `EASE.emphasis`/`DUR.med` with confident but non-bouncy settle (no `back.out`/elastic/bounce per system rule — paper settles, it doesn't bounce). Exits use `EASE.exit` at ~75% of entry length. Pin/stamp illustrations rotate within the tokenized tilt values (`--tilt-pin -10deg`, `--tilt-stamp -4deg`) on entry and never counter-rotate to 0°.

**Ambient system:** `paper-grain-overlay` is full-bleed and present in every scene at identical low density (background layer, exempt from caption-band rule). No additional ambient texture (no scanlines, no halftone, no architectural grid) — the grain is the only atmosphere, per preset rule.

**Stillness allocation:** `stillness-before-climax` (0.3-0.75s) is scheduled in exactly 2 scenes: Scene 1 (the tear pauses fractionally before the page visibly incompletes — letting "locking them out" land) and Scene 5 (the FREE AUDIT card holds suspended a beat before the pin slams down, ahead of the CTA line landing). No other scene uses this beat.

**Film negative list:** no nav bars/browser chrome/scrollbars (no interface reconstruction is called for by this script), no generic color-block/sphere/ribbon decoration, no floating bokeh, no purple-to-blue AI gradient, no mesh/dual-radial-swell backgrounds, no slide/wipe/zoom-style scene transitions (paper aesthetic forbids them — cross-dissolve only), no `back.out`/elastic/bounce easing anywhere, no pure black/white (ink and paper both use the tokenized off-tones).

**Transition vocabulary (2-3 max, repeated):** `cut-the-curve` is the default break-transition (scene 1→2, scene 4→5) realized within the system as a quiet cross-dissolve (per pin-and-paper's "scene transitions are short cross-dissolves; never slide/wipe/zoom" rule — direction-alternation is suppressed in favor of the preset's dissolve-only vocabulary). `morph` (Tier-A, doesn't count toward the cap) carries the two `continue` seams: scene 2→3 (term card unfolds into icon stack) and scene 3→4 (icons merge into the arrow+magnifying-glass glyph), both using `card-morph-anchor`.

**Visual register mix + asset coverage:** All five scenes are faceless invented graphics (assetCandidates is `[]` throughout) — kinetic typography + hand-drawn diagram glyphs native to the pin-and-paper system (pinned cards, stamps, process steps, scribble notes). Registers used: Scene 1 = diagram (torn wireframe). Scene 2 = typographic term-card (stamp + pinned-card). Scene 3 = diagram/data-viz (three stacked process-step icons). Scene 4 = diagram (merged arrow + magnifying glass glyph) + data-counter accent. Scene 5 = typographic CTA (stamp + pinned-card). At least 3 distinct composition templates are used across the film (Centered, Rule-of-Thirds, Asymmetric) satisfying the "3+ templates across 5 scenes" requirement.

## Scene 1: The Invisible Visitor

**Duration:** 6.04s
**Effects:** [`svg-path-draw`, `scale-swap-transition`]
**Continuity:** break

Someone lands on the page and finds part of it simply isn't there for them. Composition: Centered. A large hand-drawn website wireframe (`pinned-card`, askew tilt) fills ~55% of the frame, pinned by a single `safety-pin` at top-left corner. One quarter of the wireframe block visually tears away (clip-path reveal, write-on direction reversed to a "tear-off") to the right, leaving a jagged paper-edge gap — the absence is the visual subject. Eyebrow chip top-left: `chip` reading "FIELD REPORT 01" in mono uppercase. Depth: background paper grain, midground wireframe card, foreground torn fragment receding with drop opacity. Type: Hero number "1 in 4" rendered in display tier inside the wireframe's empty torn zone — mega/hero scale jump vs. the mono eyebrow chip (7x+ contrast). Scribble-note beneath in Caveat: "someone can't get in" with `pp-underline` on "in." Motion: Macro move: slow paper-settle drift on the whole card. Secondary: the tear executes as a `scale-swap-transition`-style detach (write-on clip-path, `EASE.emphasis`, `DUR.med`), then stillness-before-climax (0.4s hold on the gap) before the hero number snaps in on `EASE.entry`. Pin tilts within tokenized range on entry, no counter-rotation. `svg-path-draw` draws the wireframe linework in; `scale-swap-transition` executes the tear-away. Eye destination: the torn gap pulls the eye into Scene 2's term card via `cut-the-curve` (break, cross-dissolve).

## Scene 2: More Than a Checkbox

**Duration:** 7.51s
**Effects:** [`coordinate-target-zoom`, `counting-dynamic-scale`]
**Continuity:** continue

This isn't a niche legal checkbox — it's a stack of risk most owners never see coming. Composition: Asymmetric 60/40. A single `pinned-card` (the "ADA Compliance" term card) occupies the left 60%, inked in hero display type with negative tracking; right 40% carries a vertical stack of small `stamp` components ("RECEIVED", "DRAFT 04"-style) suggesting a rising stack of demand letters, plus a `stat-counter` ticking upward beside them. Type: Hero word "ADA compliance" — display tier, sentence case per voice rules, anchored left card. Mono eyebrow above: "TERM 02". Caveat scribble-note lower-left: "even well-meaning businesses" with underline on "well-meaning." Motion: Macro: continuous push-in (camera moves toward the term card, simulating the "push through the torn wireframe" transition beat). Secondary: the stamp stack on the right enters with a tight stagger (3-4 items, total ≤500ms), `stat-counter` counts up once and rests via `counting-dynamic-scale`. Term card itself holds still — the one moving macro layer, `coordinate-target-zoom`, carries it. Eye destination (continue seam): the term card carries across and unfolds into Scene 3's icon stack via `card-morph-anchor`.

## Scene 3: What Accessible Looks Like

**Duration:** 6.25s
**Effects:** [`svg-icon-enrichment`, `dynamic-content-sequencing`]
**Continuity:** continue

Compliance isn't abstract — it looks like three concrete, achievable habits. Composition: Rule of Thirds. Three `process-step` components stack vertically along the left third-line, each with a Caveat hand-script numeral (1, 2, 3) and a small line-drawn glyph (arrow / text-lines / block-grid) rendered as `svg-icon-enrichment` icons. Right two-thirds stays open paper with a single supporting scribble-note, keeping the squint-test hierarchy clean: the step column is the obvious primary mass. Type: Each step's label in Space Grotesk heading tier (clear nav / readable text / structured pages), well below hero scale of scene 2 — deliberate scale-down signaling "in practice" detail rather than headline drama. No mono chrome needed here; the script numerals carry the ordering voice. Motion: Macro: gentle vertical parallax drift tying the three steps together as one filmed move. Secondary: each `process-step` icon plays its `svg-icon-enrichment` animation in sequence (rapid succession matching "Clear navigation. Readable text. Well-structured pages."), staggered ≤500ms total via `dynamic-content-sequencing`, then all three settle and hold. Eye destination (continue seam): the stacked icons merge into Scene 4's arrow/magnifying-glass glyph via `card-morph-anchor`.

## Scene 4: Good for Everyone

**Duration:** 6.02s
**Effects:** [`svg-path-draw`, `counting-dynamic-scale`]
**Continuity:** break

Accessibility isn't a tax on the business — it's a multiplier for every visitor and every search result. Composition: Centered (climax-style for the "so what" beat). One large hand-drawn glyph — an upward arrow rising through a magnifying-glass outline — sits centered at ~50% of frame height, drawn via `svg-path-draw`. A `stat-counter` to its lower-right ticks an SEO-style metric upward. Minimal supporting chrome: one mono eyebrow "RESULT 04" top-left. Type: Hero glyph carries the visual weight (no competing headline); a short display-tier line ("better for every visitor") sits beneath it in restrained scale — 3:1 under the glyph's visual footprint. Secondary accent color (`--brand-secondary` gold) marks the arrow stroke as the sole accent moment in the film bound to this "rising" semantic. Motion: Macro: slow dolly-in culminating on the glyph. Secondary: the arrow draws upward via `svg-path-draw` synced to the counter's count-up (`counting-dynamic-scale`), one correlated beat — not two independent animations. Glyph holds with subtle multiplicative breathing (±1-2%) as the sole live element once settled. Eye destination: the rising arrow hands off into Scene 5's CTA stamp via `cut-the-curve` (break, cross-dissolve).

## Scene 5: Know Where You Stand

**Duration:** 6.21s
**Effects:** [`card-morph-anchor`, `press-release-spring`]
**Continuity:** break
**SFX:**
- `impact-bass-1.mp3` at 5.0s — pin-slam landing

Now the visitor isn't locked out — and the business knows exactly where it stands. Composition: Centered (climax/CTA). A `pinned-card` reading "FREE AUDIT" slides in and is fixed in place by a large `safety-pin` with the loudest accent moment in the film: `--brand-accent` red on the stamp border. Beneath/behind it, the now-complete wireframe from Scene 1 (no more tear) sits faint in the background — full-circle callback, depth layer rather than focal. Type: `stamp` component, DM Mono uppercase, "FREE AUDIT" rotated to tokenized stamp tilt. Below it, CTA line in display tier sentence case: "Claim your free ADA audit." Mono attribution line: "BUSINESS DESIGN INNOVATIONS" tracked wide as the closing source tag. Motion: Macro: slow settle-and-hold dolly (camera eases to rest, no further drift after this beat — closing scene per beat-structure "still and breathable"). Secondary: the card slides in then stillness-before-climax (0.5s suspended hold) before the pin slams down (`EASE.emphasis`, confident non-bouncy settle, `press-release-spring`) exactly as the CTA line lands; the completed wireframe behind fades up gently via `card-morph-anchor` to confirm closure. This is the film's end — no further transition.
