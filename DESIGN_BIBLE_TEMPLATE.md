# Visual Design Bible Template
## For Multi-Faction Games with AI-Assisted Asset Pipelines

Version: 1.0 | Reusable across projects

---

## How to Use This Template

This template produces a visual design bible that serves two audiences:
1. **Humans** — creative direction, design decisions, faction identity
2. **AI pipelines** — structured prompt composition, style enforcement, validation checklists

Fill every section. Sections marked [CREATIVE DECISION] require original design work — these cannot be derived from lore alone. Sections marked [EXTRACT FROM CANON] can be populated from existing game design documents.

---

## SECTION 0: PROJECT META

```yaml
project_name:
version:
last_updated:
art_style: [photorealistic | stylized-painterly | cel-shaded | pixel-art | anime]
target_scale: [minimum readable sprite size, e.g. "64x64px"]
rendering_approach: [outline style, shadow treatment, lighting model]
tone_keywords: [3-5 emotional words, e.g. "gritty, scrappy, earned, lived-in, tense"]
anti_tone: [what this game is NOT, e.g. "not grimdark, not hopeful-bright, not anime"]
reference_comps: [published games/media with similar visual feel]
```

### Generation Infrastructure

```yaml
checkpoint: [locked SDXL checkpoint for all generations]
style_prefix: |
  [30-40 word fixed prompt prefix used on EVERY generation.
   Defines rendering style, not content. Example:
   "2d game character concept art, painterly cel-shaded coloring,
   dark outlines, muted palette, soft upper-left lighting,
   textured paper background, by [style reference]"]
negative_prompt: |
  [fixed negative prompt, same vocabulary domain as positives]
generation_params:
  cfg: [5-7]
  steps: [25-30]
  sampler: [dpmpp_2m]
  scheduler: [karras]
  resolution: [1024x1024]
ip_adapter_references: [paths to 1-3 "hero" style reference images]
style_lora: [path to trained style LoRA, if available]
```

---

## SECTION 1: GLOBAL ART PILLARS

### Emotional Contract
[EXTRACT FROM CANON]

What 3-5 feelings must every piece of art in this game deliver?

1. ___
2. ___
3. ___

### This, Not That

| This | Not That | Why |
|------|----------|-----|
| ___ | ___ | ___ |
| ___ | ___ | ___ |
| ___ | ___ | ___ |

### Global Shape Language

Shapes that are SHARED across all factions (not faction-specific):
- UI elements: ___
- Navigation/waypoint markers: ___
- Damage/health indicators: ___

### Global Color Reservations

Colors reserved for GAMEPLAY (never used for faction identity):

| Purpose | Color | Hex |
|---------|-------|-----|
| Health/damage | ___ | ___ |
| Currency/economy | ___ | ___ |
| Shield/defense | ___ | ___ |
| Danger/alert | ___ | ___ |
| Background/void | ___ | ___ |
| Primary text | ___ | ___ |

---

## SECTION 2: FACTION IDENTITY CARDS

Repeat this entire section for each faction/civilization.

### Faction: [NAME]

#### 2.X.1 — Cultural Thesis
[EXTRACT FROM CANON]

- **One sentence:** What does this civilization value above all else?
- **Guiding concept:** [order | growth | honor | flow | survival | ___]
- **Historical driver:** What shaped their aesthetic? (e.g., "nomadic scarcity drove modular design")

#### 2.X.2 — Species Anatomy
[CREATIVE DECISION — cannot be derived from lore alone]

```yaml
species_type: [human | insectoid | reptilian | cephalopod | ___]
body_plan:
  limb_count: [arms, legs, tentacles, wings]
  joint_structure: [standard biped | digitigrade | multi-jointed | boneless]
  head_to_body_ratio: [e.g., "1:6 like human" or "1:8 elongated"]
  center_of_gravity: [low/hunched | centered/upright | top-heavy]
  size_vs_human: [smaller | same | larger | much larger]

unique_features:
  - [e.g., "antennae that track movement"]
  - [e.g., "chromatophores that shift color with emotion"]
  - [e.g., "bony crest plates on face and shoulders"]

expression_system: [facial | postural | chromatic | crest/antenna | pheromone (invisible)]

movement_notes: |
  [How does this species walk, run, fight, sit?
   Affects animation and pose design.]

interaction_notes: |
  [How do they hold objects? Shake hands? Gesture?
   Affects weapon and tool design.]
```

#### 2.X.3 — Shape Language
[CREATIVE DECISION]

```yaml
primary_shape: [circles | squares | triangles | organic curves | crystalline | angular slabs]
secondary_shape: [___]
forbidden_shapes: [shapes this faction NEVER uses]
```

**Shape application chart:**

| Domain | How the shape appears |
|--------|----------------------|
| Clothing seams/cut | ___ |
| Armor plate edges | ___ |
| Weapon profiles | ___ |
| Architecture | ___ |
| Ship hulls | ___ |
| Signage/insignia | ___ |

**Silhouette test:** [Include 3-5 character silhouettes at target sprite scale. If you can't tell the faction from the silhouette, redesign.]

#### 2.X.4 — Color System
[CREATIVE DECISION informed by canon]

```yaml
primary: { color: "___", hex: "#___", usage: "60% of palette" }
secondary: { color: "___", hex: "#___", usage: "30% of palette" }
neutral: { color: "___", hex: "#___", usage: "10% base/metal/fabric" }
sacred: { color: "___", hex: "#___", usage: "ceremony, leadership only" }
taboo: { color: "___", usage: "this faction avoids or despises this color" }
warning: { color: "___", hex: "#___", usage: "danger, hostility signals" }
```

**Status color progression:**

| Rank | Primary intensity | Secondary presence | Sacred access |
|------|-------------------|-------------------|---------------|
| Lowest | Muted/faded | Absent | No |
| Mid | Standard | Accent only | No |
| Senior | Saturated | Full secondary | Ceremonial only |
| Leader | Deep/rich | Equal presence | Full access |

#### 2.X.5 — Material Vocabulary
[CREATIVE DECISION informed by canon trade goods]

Name 3-5 materials this faction uses. Include: what it looks like, how it's made, what it says about the culture.

| Material Name | Appearance | Construction | Cultural Signal |
|---------------|------------|-------------|-----------------|
| ___ | ___ | ___ | ___ |
| ___ | ___ | ___ | ___ |
| ___ | ___ | ___ | ___ |

**Construction method:** Does this faction's gear look [stitched | welded | grown | printed | scavenged | forged | secreted]?

**Wear/aging:** [pristine | maintained | weathered | battle-scarred | jury-rigged]

#### 2.X.6 — Clothing Construction System
[CREATIVE DECISION]

**Layer system:**

| Layer | What it is | Material | Notes |
|-------|-----------|----------|-------|
| Base (skin-contact) | ___ | ___ | ___ |
| Functional (role gear) | ___ | ___ | ___ |
| Identity (faction markers) | ___ | ___ | ___ |
| Accessory (personal/rank) | ___ | ___ | ___ |

**Draping/fit rules:** How does cloth/armor interact with this species' anatomy?
- [e.g., "armor plates attach to exoskeleton segments, not draped over"]
- [e.g., "robes flow around tentacles, fastened with magnetic clasps"]

**Rank-to-clothing progression:**

| Rank | Silhouette change | Material upgrade | Color shift | Accessory |
|------|-------------------|-----------------|-------------|-----------|
| Lowest | ___ | ___ | ___ | ___ |
| Mid | ___ | ___ | ___ | ___ |
| Senior | ___ | ___ | ___ | ___ |
| Leader | ___ | ___ | ___ | ___ |

#### 2.X.7 — Equipment Design Language
[CREATIVE DECISION]

**Weapons:**
- Shape rule: [how faction shape language applies to weapons]
- Material rule: [what materials, finish, wear level]
- Signature weapon type: [e.g., "curved blades" or "energy gauntlets" or "bio-acid spitters"]
- How weapons are carried: [holstered | mag-locked | sheathed | integrated into body]

**Tools/devices:**
- Civilian tech aesthetic: ___
- Military tech aesthetic: ___

**Vehicles/ships:**
- Hull shape: [follows faction shape language]
- Engine style: ___
- Livery/markings: ___
- State of repair: ___

#### 2.X.8 — Architecture and Environment
[CREATIVE DECISION informed by canon station descriptions]

```yaml
building_shapes: [follows faction shape language]
materials: [what structures are made of]
lighting: [warm/cool, bright/dim, colored/neutral, source type]
state_of_repair: [pristine | maintained | weathered | ruins]
signature_space: |
  [Describe the ONE room/area that most embodies this faction's identity.
   E.g., "The Debt Ledger hall — a martial arena where debts are displayed publicly."]
```

#### 2.X.9 — Prompt Fragment Library
[DERIVED from all above sections]

These are locked prompt fragments that get composed into SDXL prompts. One fragment per category.

```yaml
species_fragment: |
  [e.g., "tall reptilian alien with scaled green skin, prominent brow ridges,
   digitigrade legs, muscular heavy build"]

clothing_fragment_by_rank:
  lowest: |
    [e.g., "wearing basic leather training harness with single house badge"]
  mid: |
    [e.g., "wearing layered scale-mail armor with crimson house sash"]
  senior: |
    [e.g., "wearing ornate ceremonial plate armor with gold trim and house crest"]
  leader: |
    [e.g., "wearing master-forged ancestral armor with sacred crimson cape and dual house crests"]

equipment_fragment: |
  [e.g., "energy blade sheathed at hip, honor tokens on belt"]

environment_fragment: |
  [e.g., "standing in a stone-floored training yard with weapon racks on walls"]

mood_fragment: |
  [e.g., "stern martial bearing, disciplined posture, direct eye contact"]
```

---

## SECTION 3: CROSS-FACTION DESIGN RULES

### The Layer Cake System

When a character belongs to or works with a faction that isn't their species' origin:

| Allegiance level | Origin faction % | Adopted faction % | Example |
|-----------------|-------------------|-------------------|---------|
| Recent recruit | 80% | 20% (accent only) | Origin clothing + adopted badge |
| Integrated member | 50% | 50% | Mixed clothing, adopted colors dominant |
| Full convert | 20% | 80% | Adopted clothing + one origin personal item |
| Defector | 70% origin (worn/damaged) | 30% adopted (new) | Visual tension = narrative tension |

### Mercenary / Neutral Characters
- Desaturated palette, no clean faction primary
- Mixed materials from multiple factions
- Deliberately "visually homeless"
- Equipment is pragmatic, not ceremonial

### Mixed-Species Crews
- Each member wears their own species' clothing construction
- Shared crew identity through ONE common element (e.g., ship patch, color band, insignia)
- The common element should be small enough that faction identity reads first, crew identity reads second

---

## SECTION 4: MASTER COMPARISON SHEETS

These are the final validation pages. Every character must pass these tests.

### 4.1 — Silhouette Lineup
All faction representatives side by side as black silhouettes at target sprite scale.
**Test:** Can you tell which faction each belongs to from silhouette alone?

### 4.2 — Color Lineup
All faction representatives side by side in full color at target sprite scale.
**Test:** Do the palettes read as distinct? Do any two factions look too similar?

### 4.3 — Same Role, Different Faction
The same role (e.g., "soldier" or "merchant") rendered for each faction.
**Test:** Does the role read the same while the faction reads differently?

### 4.4 — Rank Progression Strip
One faction shown at all rank tiers side by side.
**Test:** Can you tell rank from silhouette at target sprite scale?

### 4.5 — Gameplay Scale Test
All characters at actual gameplay resolution (e.g., 64x64px).
**Test:** Are all characters readable? Can you identify faction AND role?

---

## SECTION 5: VALIDATION CHECKLIST

Before accepting any generated concept art, verify:

- [ ] **Faction identity:** Character reads as the correct civilization at a glance
- [ ] **Color compliance:** Primary/secondary/neutral ratios match faction spec
- [ ] **Material compliance:** Surface textures match faction material vocabulary
- [ ] **Silhouette compliance:** Shape language matches faction spec (no cross-faction shapes)
- [ ] **Rank compliance:** Status markers match the character's rank tier
- [ ] **Species compliance:** Anatomy matches the species definition (limb count, proportions, features)
- [ ] **Mood compliance:** Expression/posture matches faction tone
- [ ] **Gameplay scale test:** Character is readable at target sprite resolution
- [ ] **Cross-faction rule:** If mixed-faction, layer cake percentages are correct
- [ ] **No style drift:** Matches the style prefix and IP-Adapter reference (same game feel)

Any failure triggers prompt adjustment and regeneration, not acceptance with caveats.

---

## APPENDIX A: PROMPT COMPOSITION FORMULA

Every generated image prompt follows this structure:

```
[STYLE PREFIX — never changes, from Section 0]
[SPECIES FRAGMENT — from 2.X.9]
[CLOTHING FRAGMENT — from 2.X.9, selected by rank]
[EQUIPMENT FRAGMENT — from 2.X.9, if character is armed]
[POSE — standard set: idle | armed | sitting | walking | combat]
[BACKGROUND — always "isolated on plain white background" for concept art]
[MOOD FRAGMENT — from 2.X.9]
```

Negative prompt: [fixed from Section 0, never changes]

The composer CONCATENATES these fragments. It does not improvise. Every visual element traces back to a bible entry.

---

## APPENDIX B: GENERATION INFRASTRUCTURE CHECKLIST

Before generating any batch:

- [ ] Checkpoint locked (one model, never switch mid-project)
- [ ] Style prefix tested on 1 character per faction (visual coherence confirmed)
- [ ] IP-Adapter reference images selected (1-3 hero images)
- [ ] Generation parameters locked (CFG, steps, sampler, resolution)
- [ ] Negative prompt finalized
- [ ] Style LoRA trained (optional but recommended for 95%+ consistency)
- [ ] Pose templates created (ControlNet, optional)
- [ ] One test character per faction generated and validated against checklist
