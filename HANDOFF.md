# Visual Design Bible — Handoff

## What Exists

### Template (`DESIGN_BIBLE_TEMPLATE.md`)
A reusable, game-agnostic template for building visual design bibles for multi-faction games with AI-assisted asset pipelines. Sections:

- **Section 0: Project Meta** — art style, tone, generation infrastructure (checkpoint, style prefix, params, IP-Adapter, LoRA)
- **Section 1: Global Art Pillars** — emotional contract, "this not that," global color reservations
- **Section 2: Faction Identity Cards** (repeat per faction) — cultural thesis, species anatomy, shape language, color system, material vocabulary, clothing construction, rank/status hierarchy, equipment design, architecture, prompt fragment library
- **Section 3: Cross-Faction Design Rules** — layer cake system for mixed-faction characters, mercenary/neutral rules, mixed-species crew rules
- **Section 4: Master Comparison Sheets** — silhouette lineup, color lineup, same-role-different-faction, rank progression strip, gameplay scale test
- **Section 5: Validation Checklist** — 10-point gate for accepting/rejecting generated concepts
- **Appendix A: Prompt Composition Formula** — style prefix + species + clothing (by rank) + pose + mood. No improvisation.
- **Appendix B: Generation Infrastructure Checklist** — pre-flight checks before any batch

### First Implementation: Star Freight
The template was filled in for Star Freight at `mcp-tool-shop-org/star-freight-ue5/VISUAL_BIBLE.md` (v0.1). Covers 5 civilizations (Terran Compact, Keth Communion, Veshan Principalities, Orryn Drift, Sable Reach) with full anatomy law for 3 alien species.

## What Was Proven

1. **Fragment-composed prompts produce faction-coherent results.** Five characters from five factions, generated using only concatenated bible fragments (no improvisation), look like the same game at 64px on a dark game background. Tested 2026-04-10.

2. **The system catches what free-form prompts miss.** Earlier session generated 36+ concept images with improvised prompts — user rejected all as "people in Halloween costumes." Same characters regenerated with bible fragments passed visual coherence test.

3. **The validation checklist works.** The 12-point gate (faction read, color compliance, shape compliance, species anatomy, material compliance, rank read, clothing system, equipment compliance, wear level, gameplay scale, same-game test) catches drift that pure aesthetic judgment misses.

## What's Missing / Next Steps

### Template Improvements
- **Section 4 (Comparison Sheets)** is spec'd but not implemented — no tooling to auto-generate comparison sheets from a set of concept images
- **IP-Adapter workflow** — the template references IP-Adapter style reference but no ComfyUI workflow has been built yet. This is the single biggest consistency upgrade available.
- **Style LoRA training guide** — the template mentions training a style LoRA on 20-30 approved concepts but doesn't include a step-by-step guide or training config
- **ControlNet pose templates** — the template mentions standardized pose skeletons but none have been created

### Star Freight Bible Gaps
- **Keth 4 arms** — SDXL can't reliably generate 4-armed characters from prompt alone. Needs ControlNet skeleton or IP-Adapter reference image.
- **Orryn tentacle base** — same issue. SDXL defaults to biped legs. Needs structural guidance.
- **Veshan tail** — doesn't always generate. Lower priority since it's often occluded at 64px.
- **DreamShaper XL checkpoint** — bible specifies it but it wasn't available during testing. Currently using JuggernautXL (more photorealistic than desired). Download DreamShaper XL for proper style match.
- **Ancestor tech visual language** — the extinct 6th civilization's technology has no visual design yet. Needed for Sable Reach equipment and story artifacts.
- **Ship exterior design language** — the bible covers character art but ships need their own section with hull shapes, engine styles, livery rules per faction.

### System Architecture
The long-term vision is three layers:
1. **Design Bible** (this repo's template) — defines visual rules per game
2. **Prompt Composer** (not built yet) — tool that reads a bible + character definition and emits a composed prompt. Currently done manually by concatenating fragments.
3. **Consistency Infrastructure** (partially built) — locked checkpoint, fixed params, IP-Adapter, ControlNet, style LoRA. The generation pipeline at `trellis-sprite-pipeline` handles mesh→sprite but doesn't yet enforce bible compliance programmatically.

### For Future Games
The template is designed to work for any multi-faction game. To use it for a new game:
1. Copy `DESIGN_BIBLE_TEMPLATE.md` into the game repo
2. Rename to `VISUAL_BIBLE.md`
3. Fill sections in order: global style lock → species anatomy → faction clothing/equipment → rank progression → prompt fragments
4. Generate 1 test character per faction using only fragments
5. Put them on a game-background lineup at gameplay scale
6. If they look like the same game, the bible is working. If not, the bible has a gap.

## Key Learnings (carry forward)

- **Constraint produces identity.** One primary color, one shape language, one material word per faction. More freedom = more drift.
- **Anatomy before clothing.** Design the body plan first — clothing construction follows from anatomy constraints (4 arms = different harness, no legs = no pants, tail = split cape).
- **Silhouette at gameplay scale is the real test.** Full-size concept art that looks great but is unreadable at 64px is a failed design.
- **Compose, never improvise.** Every prompt element must trace to a bible entry. If the fragment doesn't exist, add it to the library — don't write a one-off.
- **Background is irrelevant.** It gets removed in the sprite pipeline. The style lock is about what survives into the game: line quality, lighting, saturation, surface finish, proportional conventions.

## Research Sources

Three research reports were produced (2026-04-10) that informed the template design:
1. **Game art bible structure** — studied Mass Effect, Destiny, Warframe, Halo, StarCraft published art bibles. Key finding: 5 pillars of faction differentiation (shape language, color discipline, material vocabulary, motif system, proportional identity).
2. **Star Freight visual DNA extraction** — deep-read all game content files, extracted every visual hint per civilization. Key finding: rich atmospheric/cultural canon but zero physical anatomy or clothing specs for alien species.
3. **SDXL consistency techniques** — researched IP-Adapter, style LoRA, ControlNet, checkpoint selection, prompt templates. Key finding: locked checkpoint + fixed style prefix + IP-Adapter reference images gets 80% consistency; style LoRA gets to 95%.

These reports are in the session context but not persisted to disk. The key findings are embedded in the template structure itself.
