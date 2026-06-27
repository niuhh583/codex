---
name: prompt-reverse
description: Reverse-engineer reusable AI generation prompts from reference images, videos, screenshots, finished designs, posters, product photos, or user descriptions. Use when the user asks for 反推提示词, 提示词倒推, 图片反推, 视频反推, prompt reverse, image-to-prompt, video-to-prompt, prompt recreation, style extraction, or wants to reproduce a visual result in Nano Banana Pro, Gemini image generation, Midjourney, Stable Diffusion, Flux, DALL-E, 即梦, 可灵, Seedance, Runway, Pika, or 米线 AI.
metadata:
  short-description: Reverse visuals into reusable prompts, including Nano Banana Pro reference-locked prompts
---

# Prompt Reverse

Use this skill to turn a reference visual or finished result into reusable prompts for AI image, video, or design generation.

Default to Chinese unless the user asks otherwise. For Nano Banana Pro / Gemini image generation, provide an English production prompt plus a Chinese working draft.

Inspired by 米线 AI's prompt reverse tool:
https://www.aimixian.cn/tools/prompt-reverse

## Core Workflow

1. Identify the input type.
   - Image, screenshot, product photo, poster, UI, character, scene, video, or text-only description.
   - If the visual file is unavailable, ask the user to upload it or provide a concise description.

2. Identify the target model or platform.
   - If the user mentions Nano Banana Pro, Gemini, or wants high-fidelity recreation from a reference image, use the Nano Banana Pro workflow below.
   - If no model is named, produce a general prompt and include model-specific notes only when useful.

3. Analyze the reference.
   - Subject: who or what appears, visible traits, pose, expression, product features.
   - Scene: environment, background, props, spatial layout.
   - Composition: camera angle, crop, focal length feel, framing, foreground/midground/background layers.
   - Scale and placement: subject size in frame, position, crop, occlusion, negative space.
   - Style: medium, genre, rendering style, era, art direction, brand mood.
   - Lighting and color: light source, contrast, palette, shadows, atmosphere.
   - Texture and detail: materials, surface finish, grain, depth of field, motion blur.
   - Imperfection: blur, haze, dust, compression, dirt, broken edges, asymmetry, partial visibility.
   - Text: exact visible wording, typography style, placement, and whether the target model can render text reliably.
   - Output constraints: aspect ratio, resolution, duration, shot length, platform, model, and intended use.

4. Produce a reusable prompt set.
   - Provide a concise primary prompt first.
   - Add an expanded production prompt when the user needs higher fidelity.
   - Add model-specific variants only when useful or requested.
   - Include negative prompts and parameter suggestions for models that use them.

5. Preserve intent, not private identity.
   - If the input contains a real person, describe visible non-sensitive traits and styling. Do not infer protected attributes.
   - Do not claim exact identity unless the user states it or it is obvious public context.
   - For copyrighted characters or brands, phrase as style/attributes when the user wants an original alternative.

## Nano Banana Pro / Gemini Workflow

Use this workflow whenever the user asks for Nano Banana Pro prompts, Gemini image prompts, reference-image recreation, or complains that generated images drift from the reference.

### Core Principle

Describe not only what appears in the image, but what must not change. Nano Banana Pro often beautifies, completes, symmetrizes, posterizes, or redesigns a scene when given only descriptive keywords. Put reference-locking and anti-drift constraints before visual details.

### Target Modes

- `保守复刻`: preserve the reference as closely as possible.
- `创意变体`: keep composition/style but change subject, environment, or story.
- `编辑修正`: diagnose a failed generation and tighten the next prompt.

### Nano Banana Prompt Order

1. Reference lock.
   - State that the uploaded reference image is the strict visual and composition target.
   - Lock camera angle, crop, subject scale, placement, lighting direction, atmosphere, and imperfect visual quality.
2. Composition constraints.
   - Specify subject position, size, crop relationship, foreground/midground/background, and what must remain incomplete or partially hidden.
3. Subject description.
   - Describe only key visible traits. Avoid extra details that may trigger redesign.
4. Environment description.
   - Describe space, architecture, props, terrain, weathering, and background.
5. Imperfection layer.
   - Add blur, haze, dust, occlusion, cracks, broken edges, dirty lens, compression softness, asymmetry, or partial crop when present in the reference.
6. Lighting and color.
   - Lock source direction, highlight/shadow behavior, palette, and contrast.
7. Strict avoid.
   - Name the model's likely drift risks, not just generic bad-quality terms.

### Reference-Locked Template

```text
Use the reference image as the strict visual and composition target. Preserve the original camera angle, crop, subject scale, subject placement, lighting direction, atmosphere, and imperfect visual quality. Do not redesign, beautify, symmetrize, complete, or posterize the scene.

Create a [aspect ratio] [medium/style] image of [core scene]. The composition must match the reference: [subject position], [subject size], [crop relationship], [camera angle], [foreground/midground/background relationship]. The scene should feel [imperfect/ruined/chaotic/natural/cinematic screenshot], not like [likely drift direction].

[Subject description: key visible traits only]
[Environment description: space, materials, props, background]
[Imperfection layer: haze, dust, occlusion, cracks, weathering, blur, compression]
[Lighting and color: direction, intensity, shadows, palette]

Strictly avoid: [specific drift risks], clean polished surfaces, symmetrical composition, centered poster layout, over-detailed redesign, modern elements, text, logo, watermark, cartoon style, low-detail rendering.
```

### Common Anti-Drift Constraints

For cinematic battle screenshots:

```text
Do not turn the frame into a clear hero poster. Do not make the characters fully readable. Keep the image soft, smoky, dirty, cropped, motion-blurred, and imperfect like a captured live-action movie frame.
```

For foreground fencing, window frames, or debris:

```text
The foreground obstruction should be sparse, irregular, heavily out of focus, and partial. It must not become a clean full-frame pattern or readable grid.
```

For ancient ruins and giant statues:

```text
Do not complete the architecture into a perfect circular courtyard. Do not center the statue like a museum display. Keep the ruin irregular, cropped, partially collapsed, and visually incomplete. The subject should feel embedded, sunken, and partially hidden by the environment.
```

For wrong genre drift:

```text
Do not reinterpret the subject as [wrong genre]. Preserve the reference's actual subject type: [correct subject].
```

For interior window or backlit figure scenes:

```text
Preserve the interior framing: dark foreground beams and broken structural edges should frame the image, stay partially blurred, and remain darker than the exterior. The character should be small, backlit, seen from behind, and not turned into a front-facing portrait.
```

For epic desert fossil / biomechanical dinosaur ruins:

```text
Match the desert reference atmosphere first: blue sky, large sunlit clouds, pale golden dunes, dry grass, distant mountains, warm daylight, and open cinematic scale. Keep the scene photorealistic and live-action, not painterly, animated, or children's-book-like.
```

```text
The fossil must feel monumental: a colossal dinosaur skeleton or fossilized biomechanical titan stretching across the landscape like a mountain ridge. Use huge thick ribs like architectural arches, massive vertebrae, sweeping tail arcs, and dominant silhouettes across the horizon. Avoid thin delicate ribs, small ordinary animal bones, clean museum skeletons, and close-up partial rib cages.
```

```text
For mechanical feeling, use restrained surface-level biomechanical language only: segmented armor-like bone plates, worn geometric seams, shallow etched mechanical grooves, recessed vents, dark joint cavities, and dust-filled circular inlays fused into the fossil surface. Do not expose gears, cables, shiny robot parts, neon glow, or a fully mechanical creature.
```

```text
Keep the composition clean and epic: one dominant giant fossil mass, a few distant large bone silhouettes for scale, sparse dry grass, sand ripples, heat haze, and minimal foreground clutter. Avoid many tiny debris pieces, scattered small bones, noisy vegetation, or messy fragments.
```

### Failed Generation Diagnosis

When the user shows a generated image and says it is still different, begin with `偏差判断`:

- Too polished: add "do not beautify, complete, clean up, or symmetrize".
- Too poster-like: add "not a hero poster, not a centered promotional composition".
- Foreground object too strong: say it should be sparse, partial, blurred, and not cover the whole frame.
- Subject too large/small: lock exact frame area, placement, and crop.
- Wrong genre: forbid the mistaken genre explicitly.
- Too clean or complete: require broken, cropped, incomplete, partially hidden, dirty, weathered, or asymmetrical elements.
- Too cartoon/painterly: remove terms like "concept art" or "painterly"; require "photorealistic live-action cinematic VFX", real desert haze, real material scale, physically believable shadows, and documentary-grade environment realism.
- Fossil lacks scale: require "monumental scale", "fossilized mountain ridge", "huge thick ribs like architectural arches", and "dominant silhouette across the horizon".
- Mechanical detail overpowers the fossil: limit machinery to surface engravings and embedded seams; forbid exposed gears, cables, robot limbs, shiny metal, and neon glow.
- Desert scene feels cluttered: require sparse dunes, clean readable silhouettes, few large forms, minimal small fragments, and no noisy foreground debris.

### Nano Banana Style Guidance

- Prefer full sentences over comma-only tags.
- Use `Strictly avoid:` instead of short negative keyword piles.
- Avoid Midjourney flags such as `--v`, `--stylize`, or `--chaos` unless the user explicitly needs MJ.
- Mention aspect ratio as plain language, such as `21:9 ultra-wide`, or leave it for API settings.
- If the platform supports image references, tell the user to upload the reference image together with the prompt.

## Output Format

For general prompt reverse:

```markdown
**核心反推提示词**
...

**增强版提示词**
...

**负向提示词**
...

**参数建议**
- 比例:
- 风格强度:
- 参考图权重:
- 质量/清晰度:

**可替换变量**
- 主体:
- 场景:
- 色调:
- 镜头:
```

For Nano Banana Pro:

```markdown
**Nano Banana Pro Prompt**
...

**中文工作稿**
...

**严格避免项总结**
...
```

For a failed generation:

```markdown
**偏差判断**
...

**Nano Banana Pro 修正版 Prompt**
...

**中文修正要点**
...
```

For English-model workflows, include an English prompt after the Chinese one.

## Image Prompt Pattern

Use this order for most image prompts:

```text
主体 + 动作/状态 + 场景 + 构图/镜头 + 光线 + 色彩 + 材质细节 + 风格/媒介 + 情绪氛围 + 画幅/质量约束
```

Example skeleton:

```text
一张[比例]的[作品类型]，[主体]位于[构图位置]，[动作/表情/姿态]，[场景和道具]，[镜头角度和焦段感]，[光线类型]，[主色调]，[材质与细节]，[风格流派/模型偏好]，高清，细节丰富，画面干净
```

## Video Prompt Pattern

For video reverse prompts, separate global style from shot-by-shot instructions.

```markdown
**全局风格**
...

**分镜提示词**
1. 镜头 1: 主体/动作/景别/运镜/时长/转场
2. 镜头 2: ...

**运动与节奏**
...

**负向提示词**
...
```

Describe camera movement with concrete verbs: push in, pull back, pan, tilt, orbit, handheld, dolly, crane, slow motion, time-lapse.

## Model Adaptation

- Nano Banana Pro / Gemini: natural-language director brief; lock reference composition first; use `Strictly avoid` for drift; avoid MJ flags.
- Midjourney: concise comma-separated visual prompt; add `--ar`, `--style`, `--s`, `--chaos` when appropriate.
- Stable Diffusion/Flux: split positive and negative prompts; include LoRA/control/reference guidance only when the user mentions those tools.
- DALL-E/OpenAI image generation: natural language prompt with clear constraints; avoid parameter flags.
- 即梦/可灵/Seedance/Runway/Pika: emphasize shot, motion, subject consistency, lens, duration, and cinematic constraints.
- 米线 AI: use clear Chinese prompts; include reference-image intent, aspect ratio, and whether the goal is generation, edit, or video.

## Quality Checklist

Before finalizing, verify:

- The prompt can recreate the visible subject, scene, style, and composition.
- For Nano Banana Pro, composition and drift constraints appear before style description.
- Subject position, scale, crop, and camera angle are explicit when fidelity matters.
- Important text has been transcribed or flagged as model-sensitive.
- The prompt avoids vague filler such as "高级感" unless paired with concrete visual cues.
- Negative prompts target actual failure modes, not only generic low-quality issues.
- Parameters match the requested platform and output use.

If fidelity matters, offer two versions:

- `保守复刻`: closer to the reference.
- `创意变体`: keeps the style but changes subject, scene, or brand direction.
