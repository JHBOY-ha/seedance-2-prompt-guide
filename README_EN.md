# Seedance 2.0 Prompt Guide

A skill for crafting high-quality prompts for **Seedance 2.0** (即梦), ByteDance's multimodal AI video generation model.

## Installation

```bash
npx skills add JHBOY-ha/seedance-2-prompt-guide
```

## What it does

When invoked, this skill turns the agent into a Seedance 2.0 prompt engineer. It guides the full prompt creation workflow:

- **Analyzes camera choreography** — before finalizing any prompt, maps out each shot's movement trajectory, subject positions, and timing to catch conflicts early
- **Writes structured prompts** — supports both natural-language 6-step format (simple scenes) and timestamped storyboard format (8s+ or complex scenes)
- **Handles multimodal references** — generates correct `@` syntax for image, video, and audio inputs with explicit role assignments (first frame, character reference, camera reference, etc.)
- **Covers 16 scene types** — characters, product showcases, action sequences, sci-fi effects, music sync edits, dialogue, space exploration, and more
- **Executes via CLI** — when asked to generate, calls the `dreamina` CLI with the correct flags for `image2video` or `multimodal2video`

## When it triggers

- Creating or optimizing Seedance / Jimeng (即梦) video prompts
- Working with ByteDance video model prompts
- Using the `dreamina` CLI for video generation

---

## Prompt Formats

### Format 1: Natural Language 6-Step (simple scenes)

```
[Subject], [Action], in [Environment], camera [Movement], style [Visual style], avoid [Constraints]
```

Best length: **60–100 words**

| Step | Element | Example |
|------|---------|---------|
| Subject | Specific appearance details | "30-year-old woman, navy blazer, dark hair loosely pinned up" |
| Action | Specific verb + quantified intensity | "slowly turns, slight head bow, corners of mouth raised" |
| Environment | Light + mood + time | "dusk, golden hour light, city street in a gentle breeze" |
| Camera | **One main shot instruction only** | "slow push-in shot" |
| Style | Specific visual aesthetic | "35mm film grain, Kodak tones, cinematic widescreen" |
| Constraints | Exclude unwanted effects | "avoid shake, avoid body distortion, avoid flickering" |

### Format 2: Timestamped Storyboard (8s+ or complex scenes)

```
[Style] visual style, duration, aspect ratio, overall mood

[Timeline]
0-Xs: [shot type] + [content] + [action] + [effects]
Xs-Ys: [shot type] + [content] + [action]
...

[Sound] music style + sfx + dialogue/narration

[References] @asset-name  role description
```

Standard 15-second rhythm:
- **0–3s** Scene establishment
- **3–6s** Development / conflict
- **6–10s** Climax / emotional peak
- **10–13s** Turning point
- **13–15s** Resolution / freeze frame

---

## @ Reference Syntax

### How to cite assets

```
@image1    @image2    @video1    @audio1
```

### Role assignments (always required)

| Role | Example |
|------|---------|
| First frame | `@image1 as first frame` |
| Last frame | `@image2 as last frame` |
| Character appearance | `reference @image1 for character appearance` |
| Scene / background | `scene reference @image3` |
| Camera movement | `reference @video1 camera movement` |
| Action choreography | `reference @video1 action choreography` |
| Effects / transitions | `fully reference @video1 effects and transitions` |
| Rhythm / beat sync | `video rhythm reference @video1` |
| Voiceover tone | `voiceover tone reference @video1` |
| Background music | `BGM reference @audio1` |
| Costume | `wearing costume from @image2` |
| Product appearance | `product detail reference @image3` |

Recommended allocation: **3–5 images, 1–2 videos, 1 audio**

---

## Camera Vocabulary

### Basic movements

| Term | Description |
|------|-------------|
| Push-in / slow push | Camera approaches subject — emotional focus |
| Pull-out | Camera retreats — reveals space |
| Pan left / right | Horizontal rotation — scene scanning |
| Tilt up / down | Vertical rotation |
| Tracking shot | Camera follows moving subject |
| Orbit shot | Camera circles subject — great for product showcases |
| Static shot | Completely still — emphasizes action |
| Handheld shake | Simulates natural movement — documentary feel |
| Rise / lower | Vertical travel — perspective shift |
| One-shot (oner) | Continuous shot without cuts |

### Advanced movements

| Term | Description |
|------|-------------|
| Dolly zoom (Hitchcock) | Push + zoom — vertigo effect |
| Fisheye lens | Ultra-wide distortion |
| Low-angle up-shot | Low camera looking up — heroic feel |
| Bird's-eye / overhead | Looking straight down |
| First-person POV | From character's eye line |
| Whip pan | Extreme-speed horizontal pan with motion blur |
| Robotic arm follow | Multi-angle flexible tracking |

### Shot sizes

| Term | Description |
|------|-------------|
| Extreme close-up | Eyes, lips, or single detail only |
| Face close-up | Full face fills frame |
| Medium close | Head and shoulders |
| Medium shot | Waist and above |
| Full shot | Complete body |
| Wide / establishing | Full environment |

**Key rule: use only one main camera instruction. Layer secondary motion with modifiers:**

- ✅ "slow push-in shot, slight upward drift"
- ❌ "push-in + pull-out + orbit" (conflicting instructions)

---

## 16 Scene Types

| # | Scene type | Core technique |
|---|-----------|----------------|
| 1 | Character consistency | Anchor with reference image + `@image1` as subject |
| 2 | Camera movement replication | `reference @video1 for all camera effects` |
| 3 | Creative effect replication | Swap characters while preserving effects from reference video |
| 4 | Video extension (forward / backward) | `extend @video1 by Xs` — set duration to extension length only |
| 5 | Video editing | Targeted element changes while preserving most of original |
| 6 | Music beat sync | Images + `@video` rhythm reference for precise beat cuts |
| 7 | Dialogue & voice performance | Full dialogue script with emotion annotations |
| 8 | One-shot (oner) | `continuous tracking shot, no cuts` |
| 9 | E-commerce / product showcase | 360° rotation, exploded view, material close-ups |
| 10 | Science education | Timeline-annotated anatomy or process animations |
| 11 | AI short drama / manga adaptation | Panel-by-panel comic adaptation with SFX |
| 12 | Video fusion / continuation | Particle transition between multiple video clips |
| 13 | Space exploration | Immersive environment walkthrough in architectural sequence |
| 14 | Character battle | Dual-character action choreography with impact effects |
| 15 | War / high-speed chase | Handheld documentary style or extreme tracking |
| 16 | Mock documentary / plot twist | Everyday setup + abrupt narrative reversal |

---

## Style Keywords

### Lighting (highest single-element leverage)

| Type | Keywords |
|------|---------|
| Natural | golden hour, soft diffused light, blue hour, backlight, morning mist |
| Artificial | neon reflection, rim light, Rembrandt lighting, studio lighting, side light |
| Special | volumetric light, Tyndall effect, silhouette, backlit outline |
| Mood | hazy mist, deep shadows, high contrast |
| Color temp | warm tones / cool tones |

### Color grading

| Style | Keywords |
|-------|---------|
| Cinematic | `35mm film grain, Kodak tones`, `anamorphic lens flare`, `2.35:1 widescreen` |
| High saturation | `high-saturation neon tones, warm-cool contrast`, `cyberpunk palette` |
| Desaturated | `desaturated, grey-cold tones`, `ink wash style` |
| Texture | `film grain`, `commercial-grade detail`, `MV treatment`, `oil painting style` |

---

## Common Failure Fixes

| Problem | Cause | Fix |
|---------|-------|-----|
| Scene too static | No motion details | Add specific action verbs and camera instructions |
| Flat lighting | No light source description | Add light type + texture keywords |
| Character distortion | Description too complex | Simplify scene, focus on single subject |
| Shake / flicker | Missing negative constraints | Add "avoid shake, avoid flicker, avoid temporal jumps" |
| Chaotic camera | Multiple conflicting instructions | Keep only one primary camera instruction |
| Extension quality decay | More than 3 consecutive extensions | Re-export as new starting point |
| Assets unassigned | `@` reference without role | Label every `@` reference with its function |
| Content overload | Too many scenes in 4–5s | Plan pacing proportional to duration |

### High-risk keywords (avoid)

| Word | Problem | Alternative |
|------|---------|-------------|
| `fast` (bare) | Triggers chaotic motion | "running quickly" / specify exact speed |
| `cinematic` (alone) | Too vague | "35mm film feel, widescreen composition" |
| `epic`, `amazing` | Filler — no effect | Replace with specific visual description |
| Realistic human faces | Auto-blocked by moderation | Use AI-generated portraits or anime style |

---

## System Constraints

| Input type | Max count | Formats | Size limit |
|-----------|-----------|---------|-----------|
| Images | ≤ 9 | jpeg, png, webp, bmp, tiff, gif | < 30 MB each |
| Videos | ≤ 3 | mp4, mov | < 50 MB each, total 2–15s |
| Audio | ≤ 3 | mp3, wav | < 15 MB each, ≤ 15s total |
| **Total files** | **≤ 12** | — | — |

Output: **4–15 seconds**, up to 720p, with auto-generated sound.

> Realistic human face assets (photos/video) are blocked by the platform's content filter. Use AI-generated portraits or animated styles instead.

---

## CLI Usage

> The CLI is only called when the user explicitly asks to **generate / run / execute**. For prompt-only requests, output the prompt text directly.

```bash
# Image-to-video (single image)
dreamina image2video \
  --image ./character.jpg \
  --prompt "character slowly turns and smiles, gentle breeze in hair, slow push-in, golden hour light, cinematic grade, avoid shake" \
  --model_version seedance2.0 \
  --duration 8 \
  --poll 60

# Multimodal (character + scene + music)
dreamina multimodal2video \
  --image ./character.jpg \
  --image ./scene.jpg \
  --audio ./bgm.mp3 \
  --prompt "character slowly walks toward distance, camera follows smoothly, scene tones match background, avoid shake" \
  --model_version seedance2.0 \
  --duration 10 \
  --ratio 16:9 \
  --poll 60
```

### Key parameters

| Parameter | Values |
|-----------|--------|
| `--duration` | 4–15 (seconds) |
| `--ratio` | `16:9` / `9:16` / `1:1` / `4:3` / `3:4` / `21:9` |
| `--model_version` | `seedance2.0` (quality) / `seedance2.0fast` (speed) |
| `--poll` | Polling timeout in seconds (60 recommended) |

**Before running:** check credits with `dreamina user_credit`. If you get `AigcComplianceConfirmationRequired`, complete authorization on the Jimeng web interface first.

---

## Output format

Prompts are output as compact, blank-line-free text ready to paste directly into the Jimeng web interface or pass to the CLI.

## Skill structure

```
seedance-2-prompt-guide/
└── SKILL.md    # Full prompt guide: formulas, camera vocabulary,
                # scene templates, @ reference syntax, CLI usage
```

## Related

- **dreamina** skill — handles Dreamina CLI account setup, credits, and async task management
