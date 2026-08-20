---
name: cat-crayon-handdrawn-i2i
description: Transform a user-supplied real cat photograph into a square low-realism hand-drawn crayon illustration with a locked sparse flat stroke style while strictly preserving the specific cat's visible silhouette, pose, orientation, proportions, clearly visible coat-pattern topology, clothing, accessories, occlusion, and anatomical ambiguity. Use for image-to-image crayon style conversion of cat photos into naive childlike hand-drawn editorial illustrations on a white background, especially when visible markings must not be omitted, hidden anatomy must never be invented or completed, and photorealistic drift must be rejected. Support an exact `极简模式` trigger for intentionally reducing visible marking groups; otherwise default to Identity Detail Fidelity Mode.
---

# Cat Crayon Hand-Drawn I2I

Create an image-to-image illustration of the specific cat in the supplied photograph. Treat the cat photo as the only factual source. Use `assets/fixed-stroke-reference.png` as the primary and locked material reference for broad flat crayon marks, irregular paper gaps, low realism, and non-volumetric fill. Use `assets/cat-style-reference.png` only for cat-specific contour looseness, restrained facial simplification, marking abstraction, and preservation of an irregular photographed pose. Use `assets/style-reference.png` only for the broader visual language: white background, flat saturated color organization, loose simplified contours, and editorial doodle energy. Never copy subject facts, pose, composition, furniture, colors, markings, anatomy, proportions, expression, or accessories from any style reference.

Use the `imagegen` skill and built-in image generation tool. Generate the image by default; stop at prompt-only only when the user explicitly asks.

## Input roles

- **Cat photo:** primary identity and factual reference. It alone determines anatomy, silhouette, pose, direction, markings, clothing, and accessories.
- **Bundled fixed stroke reference (`assets/fixed-stroke-reference.png`):** primary material and stroke reference only. Lock its broad flat crayon construction, irregular incomplete fill, visible paper gaps, blunt broken edges, low realism, and absence of modeled volume. Never copy its gray cat, pose, anatomy, chair, palette, markings, expression, proportions, or composition.
- **Bundled cat style reference (`assets/cat-style-reference.png`):** secondary cat-specific style reference only. Learn contour looseness, facial restraint, marking abstraction, and loose execution. Never copy its cat identity, pose, orientation, anatomy, coat colors, markings, expression, proportions, furniture, support line, or accessories. Do not let its denser texture override the fixed stroke reference.
- **Bundled general style reference (`assets/style-reference.png`):** supporting style reference only. Learn its white-paper editorial visual language, flat saturated color organization, loose simplified contour, and naive crayon finish. Never copy its orange-tabby identity, orange palette, large round green eyes, lying or draped pose, anatomy, proportions, stripes, paws, tail, expression, or composition.
- **Additional user style reference:** supporting style reference only unless the user explicitly assigns another role.

If no cat photo is supplied, ask for one. Do not mistake the bundled style-reference cat for the target or use it to supply missing subject facts.

When all relevant images have local paths, pass them through `referenced_image_paths` in this order: cat photo first, `assets/fixed-stroke-reference.png` second, `assets/cat-style-reference.png` third, and `assets/style-reference.png` fourth. Label each role explicitly in the prompt and state that the fixed stroke reference outranks the other style references for material decisions. If the cat exists only as a conversation image, keep it as the factual image-generation reference and express the locked material language explicitly; never omit the cat merely to include style assets.

## Evidence card

Inspect the cat photo before composing. Record only visible evidence:

1. outer silhouette and occupied area;
2. body direction and head direction separately;
3. pose, weight distribution, and strongest body curve;
4. visible head angle, eye direction, and ear directions;
5. visible limbs, paws, tail, and their exact positions;
6. major coat colors and a complete map of clearly visible marking groups;
7. visible clothing or accessories and the anatomy they cover;
8. every uncertain or occluded region;
9. a visible-form continuity map recording which source-visible masses touch, overlap, occlude, or continue into one another, and which separations are genuine background gaps.

Select the strongest 5–8 identity anchors. Favor pose and silhouette over facial detail or ideal anatomy.

For ambiguous poses, describe visible contour masses spatially rather than assigning anatomical identities. Prefer descriptions such as `three overlapping upward dark shapes with unequal lengths` over labels such as `left hind leg` or `right front paw`. The evidence card must not turn visual uncertainty into anatomy through its wording.

### Build the Pattern Map

Treat clearly visible coat patterns as identity structure, not disposable fur texture. Before prompting, map each visible marking group by:

- body region and relation to a contour, joint, eye, ear, or tail segment;
- approximate count or grouping;
- direction, curvature, spacing, length, and width;
- tonal contrast and color relationship;
- interruptions, asymmetry, and partial visibility caused by pose or overlap.

Separate **micro-texture** from **pattern topology**:

- Micro-texture includes individual hairs, fine mottling, shine, and tiny tonal noise; simplify or omit it.
- Pattern topology includes visible stripes, patches, rings, masks, forehead marks, leg bands, tail bands, and large color boundaries; preserve it.

Do not delete a clearly visible marking merely because the style is minimal. Simplify its edge and fill while preserving its region, direction, relative count, and visual rhythm.

## Non-invention contract

Apply these rules before all aesthetic choices:

- Preserve the visible outer silhouette. Do not make the cat more complete, conventional, cute, symmetric, or anatomically readable.
- Lock left and right. Never mirror the image. Preserve body direction and head direction independently.
- Preserve tucked paws, curled bodies, hidden limbs, covered anatomy, partial crops, overlaps, and awkward shapes exactly as visible.
- Treat every region hidden by clothing, fabric, body overlap, crop, fur mass, or camera angle as unknown.
- Never add an unseen paw, paw pad, leg, foot, tail, facial feature, body part, accessory, marking, or color region.
- Never omit a clearly visible identity marking or merge separate marking groups into a generic solid body mass.
- Never turn an ambiguous mass into a named anatomical part. Preserve it as an undefined flat silhouette.
- Never increase anatomical clarity beyond the photo. Simplify, obscure, merge, or leave blank when uncertain.
- When complete anatomy conflicts with a faithful incomplete silhouette, always choose the faithful incomplete silhouette.
- Do not correct the pose or unfold, extend, separate, or reposition hidden anatomy.

Use this decision rule verbatim in the generation prompt:

`Do not invent or complete hidden anatomy. When uncertain, preserve the incomplete ambiguous silhouette rather than producing a complete anatomical interpretation. Preserve every clearly visible coat-pattern group; simplify its material texture, not its topology.`

## Visible-form continuity contract

Preserve incompleteness without fragmenting the visible subject.

- Treat every source-visible contact, tangent, overlap, and occlusion between the head, neck, body, clothing, limbs, paws, tail, and inseparable objects as identity structure.
- Keep forms that touch or overlap in the photo visually touching or overlapping in the illustration. Do not separate them with invented background-white gaps.
- Keep genuinely separate source forms separate. Do not bridge them by inventing a limb, body region, garment section, or other hidden connector.
- When the anatomical attachment is ambiguous but the visible masses touch, preserve their visible contact while leaving the attachment unnamed and unresolved.
- Allow a limb or body mass to remain cropped, covered, or anatomically incomplete while keeping the visible subject readable as one physically coherent composition.
- Use paper-white gaps as irregular crayon texture inside colored forms. Do not let paper gaps sever the outer silhouette, break a source-visible contact, or turn a connected subject into floating color islands.

Use this continuity rule verbatim in the generation prompt:

`Preserve incomplete anatomy, but keep the visible subject composition continuous. Every form that touches, overlaps, or occludes another form in the source must retain that visible relationship. Paper-white texture may break pigment inside a form, but must not split the subject into floating color islands.`

## Identity rendering

Preserve the strongest visible identity anchors:

- overall build and proportions;
- original pose and action;
- body and head directions;
- head angle, eye direction, and ear directions;
- primary body curves;
- visible limb and tail placement only;
- major coat colors and representative stripes or patches;
- visible clothing and accessories.

Simplify visible facial features into small symbolic marks. Retain visible identity cues, but keep hidden features hidden. Render eyes as dots or short curved strokes and the nose as a tiny mark. Preserve sleepy, imperfect, or asymmetric expressions. Do not beautify, enlarge eyes, add highlights, or make the face more expressive.

Compress fur material into broad flat color blocks with blunt, broken crayon edges while preserving all clearly visible marking groups from the Pattern Map. Translate each group into an uneven flat mark while retaining its approximate placement, direction, count family, spacing, and contrast. Keep about 25–30% visible paper white within the combined interiors of major colored forms, distributed as irregular small-to-medium gaps and incomplete coverage rather than uniform white noise. Keep this paper exposure internal to the visible forms; never use it to break a source-visible contact or create a floating fragment. Do not use directional short strokes that follow fur growth, contour curvature, anatomy, or lighting. Do not draw individual hairs or invent stripes.

Do not pursue maximum minimalism. Use the minimum visual information needed to preserve the specific cat's pose, expression, markings, overlapping forms, and remembered presence. Prefer a lively recognizable result that still obeys the fixed stroke lock; never recover identity by adding realistic fur texture, directional hatching, highlights, shadows, gradients, or anatomical volume.

Style simplification must not reduce identity readability. Do not flatten beyond the point where head angle becomes generic, gaze direction becomes unclear, limb rhythm becomes diagrammatic, coat variation becomes a dead uniform fill, or the cat reads as a mascot rather than the photographed individual. Express necessary orientation and overlap with flat adjacent value shapes or broken contour changes, never with gradients, directional fur strokes, highlights, shadows, or modeled volume. Do not impose a fixed number of color blocks; use as many broad flat areas as identity fidelity requires.

## Fixed stroke and material lock

Treat `assets/fixed-stroke-reference.png` as the default material authority for every generation.

- Keep realism low: the result must read immediately as a naive crayon drawing, not a photograph rendered with a crayon filter.
- Build color with broad, blunt, overlapping crayon passes and irregular broken fills. Favor simple flat masses over many small strokes.
- Target about 25–30% visible paper white inside the combined major colored forms. Judge this visually, not as an exact pixel measurement.
- Distribute paper gaps irregularly. Use a mix of short scratches, small islands, and occasional larger incomplete patches; avoid evenly speckled noise.
- Keep value steps discrete and flat. Use no smooth shading, gradient, highlight, cast shadow, reflected light, rim light, or three-dimensional volume modeling.
- Never use dense directional short marks to imitate fur, follow muscle curvature, describe lighting, or wrap around the body.
- Render pattern groups as broken flat shapes rather than realistic hairs. Pattern direction may follow the source topology, but the internal crayon grain must remain non-directional and sparse.
- Preserve loose, visibly handmade edges. Avoid polished digital blending, realistic soft transitions, and high-frequency detail.

If identity fidelity and the material lock appear to conflict, preserve identity through silhouette, pose, flat marking topology, and discrete value boundaries. Never solve the conflict by increasing realism.

Default to **Identity Detail Fidelity Mode**. In this mode:

- preserve every clearly readable marking group, including lower-contrast groups that help identify the cat;
- simplify surface texture within each group without deleting, relocating, or homogenizing it;
- let the illustration remain visually minimal through flat material, white space, and loose execution rather than through identity-detail removal.

Switch to **Minimal Mode** only when the user's request contains the exact trigger:

```text
极简模式
```

In Minimal Mode, retain the most identifying marking groups and reduce subordinate low-contrast groups. Never reduce pose, silhouette, direction, visible anatomy, or high-confidence face and tail markings.

## Style and composition

- Use a 1:1 square canvas with a pure white or subtly warm-white paper background.
- Keep only the cat and any object inseparable from its action.
- Let the subject occupy about 45–70% of the canvas with generous negative space.
- Remove floors, sofas, furniture, beds, windows, walls, toys, scratching boards, plants, and all unrelated scene elements.
- Use naive hand-drawn contour, wax-crayon or oil-pastel grain, flat high-saturation blocks, loose childlike proportions, minimal facial marks, and editorial doodle illustration.
- Apply the fixed stroke and material lock: low realism, broad broken fills, and about 25–30% visible paper white within colored forms.
- Keep lighting flat. Use no realistic shadow, gradient, directional fur hatching, volume rendering, glossy finish, or environmental depth.
- Add no text, logo, signature, border, or watermark unless explicitly requested.

Aim for a specific-cat hand-drawn crayon illustration, not a mascot or character design.

## Prompt compiler

Compile a concise prompt in this order:

1. Label the cat photo as the only factual and identity source. Label the fixed stroke reference as the primary material authority, the cat reference as secondary cat-specific style only, and the general reference as broader visual language only.
2. State the 5–8 visible identity anchors and strict left/right pose lock.
3. State every occluded or ambiguous region and prohibit completion of each one. Transcribe the visible-form continuity map, requiring every source-visible contact, overlap, and occlusion to remain continuous without inventing hidden connectors.
4. State the selected detail mode. Default to Identity Detail Fidelity Mode unless the exact `极简模式` trigger is present.
5. Transcribe the Pattern Map into explicit visible marking groups; require preservation of their approximate placement, direction, grouping, spacing, and contrast.
6. Specify visible face cues, coat blocks, clothing, and accessories without adding facts.
7. Specify the 1:1 white-paper composition and removal of the environment.
8. State the fixed material lock explicitly: low realism, broad blunt broken crayon fills, irregular 25–30% internal paper white, no directional fur strokes, and no volume modeling.
9. Specify the remaining naive crayon or oil-pastel visual language.
10. End with the non-invention contract, the visible-form continuity rule, a no-omission rule for visible markings, and negative constraints.

Keep the compiled prompt concise. Use positive preservation language before prohibitions, avoid repeating the same negative constraint, and do not overload the prompt with numeric style rules. For ambiguous poses, describe contour relationships without naming uncertain limbs.

Do not expose the full prompt unless the user asks.

## Negative constraints

Always prohibit: photorealistic cat, photo-like rendering, crayon-filtered photograph, realistic fur, individual hair strands, dense directional fur strokes, contour-following hatching, anatomy-following hatching, realistic shading, highlight, reflected light, smooth tonal transition, three-dimensional volume modeling, realistic anatomy, complete paws, visible paw pads not present in the source, invented legs, invented tail, extra body parts, corrected or changed pose, mirrored orientation, floating body fragments, disconnected color islands, invented white gaps that sever source-visible contacts, beautified face, enhanced cuteness, cute mascot, kawaii cat, cartoon character, Disney style, Pixar style, anime cat, manga cat, 3D render, glossy digital painting, smooth vector illustration, realistic lighting, shadows, gradients, detailed background, copied reference-cat identity, copied orange palette, copied large round green eyes, copied lying pose, copied anatomy, copied stripes, copied paws, copied tail, copied expression, copied composition, watermark.

## Quality gate and candidate selection

Inspect the result at normal and thumbnail scale. Separate failures into two classes.

### Hard identity failures

- mirrored orientation or changed body/head direction;
- substantially changed pose, action, silhouette, or visible limb rhythm;
- invented or omitted paws, pads, legs, tail, facial features, clothing, accessories, or other anatomy;
- hidden or ambiguous anatomy made more legible than the source;
- a head, neck, body, garment, limb, paw, tail, or inseparable object that touches or overlaps another visible form in the source becomes detached, floats as an isolated color island, or is severed by an invented white gap;
- clearly visible identity markings omitted, relocated, homogenized, or replaced with invented markings;
- expression, gaze, or head angle changed enough that the result no longer reads as the specific photographed cat;
- copied subject facts, pose, furniture, markings, colors, anatomy, proportions, expression, or composition from any style reference, including the general reference's orange coat, large round green eyes, lying pose, stripes, paws, or tail.

A hard identity failure permits one regeneration.

### Hard style failures

- the result reads as a photograph rendered through a crayon or pastel filter rather than a naive flat drawing;
- dense short strokes follow fur growth, anatomy, body curvature, or lighting direction;
- highlights, shadows, gradients, smooth tonal transitions, or modeled three-dimensional volume appear on the cat;
- high-frequency fur or material detail competes with the broad flat marking topology;
- the major colored forms are filled too continuously to retain the intended standard-airy paper exposure, with visibly far less than about 25% internal paper white;
- paper gaps appear mainly as uniform digital speckle instead of irregular broken crayon coverage;
- the output materially departs from the broad, blunt, low-realism stroke language of `assets/fixed-stroke-reference.png`.

A hard style failure permits one targeted style/material regeneration after identity, pose, anatomy, markings, and expression pass.

### Soft style deviations

- modest variation around the 25–30% paper-white target while the result remains visibly standard-airy;
- small local differences in crayon gap shape, edge looseness, or pass width that still match the fixed stroke language;
- imperfect subject scale or surrounding canvas negative space;
- other stylistic differences that do not damage identity, pose, expression, markings, or anatomical ambiguity.

Do not discard or regenerate a result solely because of a soft style deviation. Identity fidelity, pose vitality, expression, recognizability, and compliance with the hard material lock take priority over minor polish.

If regeneration is necessary, target exactly one failure category: anatomy/pose, missing markings, facial identity, style/material, or background/layout. Repeat the successful identity invariants briefly, but do not rewrite the entire subject description, introduce new numeric style constraints, or change multiple categories at once. For a hard style failure, repeat the fixed 25–30% paper-white target because it is an established material invariant, not a new constraint.

When correcting anatomy, pose, missing markings, or identity detail, regenerate from the original cat photo plus all three bundled style references. Do not use a deficient draft as an image reference because it can reinforce identity errors. When the first draft passes identity, pose, anatomy, markings, and expression but fails style/material, use it as an additional preservation reference for the style-only correction while keeping the original cat photo as factual authority and `assets/fixed-stroke-reference.png` as material authority.

After regeneration, retain both candidates and compare them. Never assume the newer candidate is better. Reject any candidate with a hard identity or hard style failure, then select among passing candidates in this order:

1. pose, silhouette, orientation, and anatomical ambiguity;
2. specific-cat recognizability, expression, gaze, and head angle;
3. visible marking fidelity and useful coat-value relationships;
4. absence of invented subject facts;
5. compliance with the fixed low-realism stroke language and 25–30% internal paper-white target;
6. background and composition polish.

If the first draft scores higher overall and passes both hard-failure gates, return the first draft. A candidate may never win by using photographic fur texture, directional short strokes, or volume modeling to increase recognizability.

## Output

Return the generated image and a brief Chinese note naming the preserved pose, silhouette, and identity anchors. State that the cat photo was the only factual reference; the fixed stroke image was the primary material reference; and the cat-specific and general images were secondary style references only. Do not reveal the full prompt unless requested.
