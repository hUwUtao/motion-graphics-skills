<!-- Book page 03 | Typography | Source: motion_and_video_production_manual.md -->

## 3. Typography

### 3.1 Classification, Pairing, and Licensing Verification

Definition: The structural selection and contrast-pairing of typefaces across Vox-ATypI classifications (Humanist, Transitional, Modern/Didone, Slab Serif, Grotesque/Neo-Grotesque, Geometric, Display, Monospace) with verified broadcast/embedding rights.
Why:

- Emotion: Typeface morphology carries immediate affective tone before a single word is decoded (e.g., Geometric/Grotesque = objective modernity; Didone = high-fashion elegance; Humanist = warmth; Monospace = technical precision) ([Bringhurst, The Elements of Typographic Style](https://www.google.com/search?q=https%3A%2F%2Fwww.thriftbooks.com%2Fw%2Fthe-elements-of-typographic-style_robert-bringhurst%2F278779%2F)).
- Attention: High structural contrast between headline and body classifications creates instant visual differentiation between information tiers.
- Production value: Pairing two nearly identical typefaces from the same classification (e.g., two Neo-Grotesques) reads as an accidental font substitution mistake.
- Clarity: High x-height (`≥ 0.52` of cap height) and open apertures preserve character differentiation under motion blur and video compression.
- Cost: Selecting variable fonts or a single superfamily with 4–6 weights reduces asset memory footprint and licensing overhead.
  Rules:

1. Limit any production to a maximum of `2` typeface families (or `3` only when a dedicated `Monospace` family is required for tabular numerals/timecode) ([Bringhurst, The Elements of Typographic Style](https://www.google.com/search?q=https%3A%2F%2Fwww.thriftbooks.com%2Fw%2Fthe-elements-of-typographic-style_robert-bringhurst%2F278779%2F)).
2. Enforce the **Concordance-or-Contrast Rule**: either use a single superfamily across varying weights/widths (e.g., Light vs. Bold Condensed) OR pair two classifications with unmistakable structural contrast (e.g., High-Contrast Display Serif headline + Neo-Grotesque Sans body); never pair two distinct families from the same sub-classification ([Bringhurst, The Elements of Typographic Style](https://www.google.com/search?q=https%3A%2F%2Fwww.thriftbooks.com%2Fw%2Fthe-elements-of-typographic-style_robert-bringhurst%2F278779%2F)).
3. Avoid extreme hairline strokes (`stroke width < 1.5 px` at delivery resolution), such as unmodified Didone hairlines on body text, because 4:2:0 chroma subsampling and temporal inter-frame compression cause thin serifs to shimmer and vanish `[OPINION]`.
4. Use `tabular-nums` (`tnum` OpenType feature) for all animated counters, HUD readouts, timers, and financial figures so character widths remain constant (`Δwidth = 0 px`) frame-to-frame, preventing horizontal jitter ([Bringhurst, The Elements of Typographic Style](https://www.google.com/search?q=https%3A%2F%2Fwww.thriftbooks.com%2Fw%2Fthe-elements-of-typographic-style_robert-bringhurst%2F278779%2F)).
   Event mapping: Static asset declaration in scene header (`font_family_primary`, `font_family_secondary`, `opentype_features: ["tnum", "kern", "liga"]`) bound to text planar elements.
   Raster/bake note: Render dynamic or scaling text using Multi-channel Signed Distance Fields (MSDF) in the fragment shader or pre-tessellated high-density planar meshes so glyph edges remain razor-sharp across camera zoom events without raster bitmap pixelation.
   Cultural notes: Central European modernist motion design favors Neo-Grotesques (Helvetica, Univers, Aktiv Grotesk); luxury fashion and editorial title design favors high-contrast Didones (Bodoni, Didot) at large display scales (`≥ 10%` frame height); CJK (Chinese, Japanese, Korean) motion typography requires matching weight metrics between Latin glyphs and ideographic Mincho/Gothic character sets.
   Failure modes: Using proportional numerals (`pnum`) on an animated number counter → the entire word/line jitters left and right on every frame as `1` (`narrow`) swaps with `8` (`wide`); using thin hairline fonts (`< 1.5 px` stroke) over moving video → strokes break up into mosquito noise under H.264/H.265 encoding.
   Checklist: [ ] `≤ 2` typeface families (plus optional Monospace for data) [ ] Clear classification contrast or single-superfamily concordance [ ] Minimum stroke width `≥ 1.5 px` at target resolution [ ] `tabular-nums` (`tnum`) active on all animated numbers
   Sources: [Bringhurst, The Elements of Typographic Style](https://www.google.com/search?q=https%3A%2F%2Fwww.thriftbooks.com%2Fw%2Fthe-elements-of-typographic-style_robert-bringhurst%2F278779%2F).

### 3.2 Size vs. Delivery Resolution, Legibility, Tracking, and Leading

Definition: The quantitative scaling of cap height as a percentage of frame height, combined with scale-dependent adjustments to letter-spacing (tracking) and line-spacing (leading).
Why:

- Emotion: Tight, monumental display type commands urgency and authority; generous leading and open tracking evoke calm luxury and airy poise.
- Attention: Ensures glyphs exceed the human visual acuity threshold at the target viewing distance so the eye decodes words as whole shapes (_bouma_) rather than letter-by-letter.
- Production value: Scale-compensated tracking (tightening large headlines, opening small caps/captions) is a hallmark of high-craft typography ([Bringhurst, The Elements of Typographic Style](https://www.google.com/search?q=https%3A%2F%2Fwww.thriftbooks.com%2Fw%2Fthe-elements-of-typographic-style_robert-bringhurst%2F278779%2F)).
- Clarity: Prevents ascender/descender collisions across lines and glyph merging under compression.
- Cost: Deterministic percentage-of-frame-height sizing rules allow automatic responsive scaling across `4K`, `1080p`, and `720p` outputs.
  Rules:

1. Specify all type sizes as a percentage of **Frame Height ($H$)** rather than arbitrary points:
   - **Minimum Legible Floor (Legal/Fine Print/HUD metadata)**: Cap height `≥ 2.2% H` (`≥ 24 px` at `1080p`; `≥ 48 px` at `4K`).
   - **Body / Subtitle / Lower-Third Copy**: Cap height `3.5%–5.0% H` (`38–54 px` at `1080p`).
   - **Subheadings / Section Callouts**: Cap height `5.5%–8.5% H` (`60–92 px` at `1080p`).
   - **Hero Display Titles**: Cap height `10.0%–25.0% H` (`108–270 px` at `1080p`) `[OPINION]`.
2. Apply **Inverse Scale Tracking**:
   - Hero Display (`> 10% H`): tighten tracking to `-0.03 em` to `-0.01 em` (`-3%` to `-1%`).
   - Body / Subtitles (`3.5%–5.0% H`): set tracking to `0.00 em` to `+0.02 em`.
   - All-Caps / Small-Caps Labels (`< 4.0% H`): open tracking to `+0.06 em` to `+0.15 em` (`+6%` to `+15%`) ([Bringhurst, The Elements of Typographic Style](https://www.google.com/search?q=https%3A%2F%2Fwww.thriftbooks.com%2Fw%2Fthe-elements-of-typographic-style_robert-bringhurst%2F278779%2F)).
3. Apply **Scale-Dependent Leading (Line Height)**:
   - Body / Multi-line Subtitles: `1.25×–1.45×` font size (`125%–145%`).
   - Mixed-case Display Headlines: `1.00×–1.15×` font size.
   - All-Caps Stacked Headlines (no descenders): `0.85×–0.98×` font size ([Bringhurst, The Elements of Typographic Style](https://www.google.com/search?q=https%3A%2F%2Fwww.thriftbooks.com%2Fw%2Fthe-elements-of-typographic-style_robert-bringhurst%2F278779%2F)).
4. Constrain line measure (column width) to `30–45 characters per line` (`5–8 words`) for motion graphics body blocks, and `≤ 42 characters per line` (`≤ 2 lines`) for timed subtitles ([Netflix Timed Text Style Guide / Partner Help](https://www.google.com/search?q=https%3A%2F%2Fstudiopartner.netflix.net%2Fstudio%2Fdelivery-specifications-and-requirements-external); [Bringhurst, The Elements of Typographic Style](https://www.google.com/search?q=https%3A%2F%2Fwww.thriftbooks.com%2Fw%2Fthe-elements-of-typographic-style_robert-bringhurst%2F278779%2F)).
   Event mapping: Text element properties `cap_height_norm` (in `[0.022, 0.30]`), `tracking_em` (in `[-0.04, +0.20]`), `leading_ratio` (in `[0.85, 1.50]`), and `max_chars_per_line` (`≤ 45`).
   Raster/bake note: When animating `tracking_em` continuously over time, evaluate glyph positions in floating-point sub-pixel space (`subpixel_positioning = true`) with MSDF/linear texture filtering; snapping animated glyphs to integer pixel coordinates causes severe stepping/shimmering artifacts.
   Cultural notes: Movie trailer end-pages ("billing blocks") use ultra-condensed display type with vertical scale transformation, whereas luxury brand spots often use small all-caps type (`3.0% H`) tracked out to `+0.20 em`–`+0.30 em` at the center of the frame `[OPINION]`.
   Failure modes: Leaving default `0 em` tracking and `1.2×` leading on a massive `20% H` all-caps headline → letters look disconnected and lines float apart; setting all-caps labels at `0 em` tracking → words clump into unreadable rectangular blocks.
   Checklist: [ ] All text cap heights `≥ 2.2%` of frame height [ ] Display type tightened (`-0.03` to `-0.01 em`); all-caps opened (`+0.06` to `+0.15 em`) [ ] Leading set to `1.25–1.45×` for body and `0.85–1.15×` for headlines [ ] Line length `≤ 45 characters` (`≤ 42` for captions) [ ] Sub-pixel positioning enabled for animated type
   Sources: [Bringhurst, The Elements of Typographic Style](https://www.google.com/search?q=https%3A%2F%2Fwww.thriftbooks.com%2Fw%2Fthe-elements-of-typographic-style_robert-bringhurst%2F278779%2F); [Netflix Partner Help Center](https://www.google.com/search?q=https%3A%2F%2Fstudiopartner.netflix.net%2Fstudio%2Fdelivery-specifications-and-requirements-external).

### 3.3 Kinetic Typography and On-Screen Reading Time

Definition: The temporal choreography of text entry, emphasis, transformation, and exit events synchronized to vocal cadence, musical rhythm, or narrative beats.
Why:

- Emotion: Translates vocal prosody (pitch, volume, stress, hesitation) directly into spatial scale, velocity, and weight changes.
- Attention: Sequential word or phrase reveals pace the viewer's eye across the screen and prevent premature reading ahead of the speaker.
- Production value: Hierarchical per-word or per-line staggered animation with masked baselines looks bespoke, whereas unmasked linear opacity fades or per-character rainbow bounces look like amateur presets.
- Clarity: Enforces a stationary reading hold window so motion never compromises comprehension.
- Cost: Reusable event-driven text-unit sequencers (`by_line`, `by_word`, `by_glyph`) generate complex kinetic sequences from declarative timing rules without manual keyframing.
  Rules:

1. Enforce the **Stationary Reading Hold Formula**: after the entrance animation completes (`≥ 90%` settled), hold the text legible for:
   $$T_{\text{hold}} = \max\left(1.5\text{ s},\; 0.3\text{ s} + \frac{N_{\text{words}}}{3.0\text{ words/s}}\right) + 0.4\text{ s} \times N_{\text{other\_moving\_focal\_elements}}$$
   before triggering the exit event `[UNVERIFIED]`.
2. Choose the **Granularity Unit** deliberately:
   - **By-Line** (`stagger = 3–6 frames` at `24–30 fps`): standard for editorial titles, quotes, and multi-line statements.
   - **By-Word** (`stagger = 2–4 frames` or locked to spoken syllable transients): standard for voiceover-synced kinetic typography.
   - **By-Character / Glyph** (`stagger = 1–2 frames`): reserve strictly for short `1–3 word` hero titles (`≤ 18 characters total`); never apply per-character stagger to body sentences (`> 25 characters`), which creates a distracting "typewriter caterpillar" effect `[OPINION]`.
3. Prefer **Masked Baseline Translation** (`Y-offset` from `+100%` line height to `0%` clipped by an invisible horizontal bounding mask per line, `duration = 10–18 frames`, `cubic-out` easing) over simple opacity fades; start opacity at `100%` as the glyph crosses the mask boundary `[OPINION]`.
4. Never animate more than `2` transform channels simultaneously on readable text (e.g., `Y-position + opacity` is clean; `X-position + Y-position + Z-rotation + scale + skew` simultaneously destroys legibility).
   Event mapping: `text_sequence_event(target_text_id, unit="word"|"line"|"char", stagger_frames=3, duration_frames=14, channel=["translate_y", "mask_clip"], easing="cubic_out", hold_duration_s=T_hold)`.
   Raster/bake note: Evaluate kinetic text masks using analytic clip planes or stencil buffers in the raster pass so angled or multi-line baseline reveals maintain crisp anti-aliased edges without extra off-screen render target allocations.
   Cultural notes: Saul Bass and Kyle Cooper title sequences pioneered kinetic typography as psychological prologue; modern short-form vertical video uses center-locked `1–3 word` rapid-replacement kinetic captions (high-retention rapid-word-replacement style) synced to every spoken word with active-word color highlighting (`OKLCH ΔC ≥ +0.12`).
   Failure modes: Starting the exit animation immediately when the entrance ease finishes (`T_hold = 0 s`) → the text is only legible for `3–4 frames` at the apex; applying elastic/bounce per-character animations to a `15-word` paragraph → nauseating visual noise and zero reading comprehension.
   Checklist: [ ] Stationary hold time $T_{\text{hold}}$ satisfies word-count + distraction formula [ ] Per-character animation restricted to `≤ 18 characters` [ ] Line/word staggers set to `2–6 frames` [ ] Maximum `2` simultaneous animated transform channels on readable copy
   Sources: [Bringhurst, The Elements of Typographic Style](https://www.google.com/search?q=https%3A%2F%2Fwww.thriftbooks.com%2Fw%2Fthe-elements-of-typographic-style_robert-bringhurst%2F278779%2F); [Chion, Audio-Vision](https://www.google.com/search?q=https%3A%2F%2Fbooks.google.com%2Fbooks%2Fabout%2FAudio_vision.html%3Fid%3Dis_HyxAyMkMC); [Lottie v1.0 Specification](https://www.google.com/search?q=https%3A%2F%2Flottie.github.io%2Flottie-spec%2F1.0%2F).
