# Visual Design Bible

Reusable template for building visual design bibles for multi-faction games with AI-assisted asset pipelines.

## What This Is

A structured template that defines every visual decision a game needs before generating concept art or sprites. It prevents cross-game drift when using AI image generation (SDXL, Flux, etc.) by locking:

- **Global style** — rendering approach, color saturation, lighting, surface finish
- **Species anatomy** — body plans, proportions, expression systems
- **Faction identity** — shape language, color systems, material vocabulary
- **Clothing construction** — layer systems, draping rules, rank progression
- **Equipment design** — weapon shapes, tool aesthetics, ship profiles
- **Prompt fragments** — pre-written SDXL prompt blocks that compose (never improvise)
- **Validation checklist** — gate that rejects concepts that don't match the bible

## How to Use

1. Copy `DESIGN_BIBLE_TEMPLATE.md` into your game repo
2. Rename to `VISUAL_BIBLE.md`
3. Fill in the sections — start with global style lock, then species anatomy, then faction clothing/equipment
4. Generate one test character per faction using only the prompt fragment library
5. Validate against the checklist
6. If they look like the same game at gameplay scale, the bible is working

## Why This Exists

Without a shared visual contract, AI-generated game characters look like they're from different games. Each prompt invents body logic, costume logic, faction logic, and art style logic simultaneously. That's too much freedom. The bible constrains the generator so every character shares one art direction.
