<!-- Book page 21 | Review & Iteration | Source: motion_and_video_production_manual.md -->

## 21. Review & Iteration

### 21.1 Quantitative Quality Rubrics, Versioning Conventions, Feedback Protocols, and Definition of Done

Definition: The deterministic inspection gates, semantic asset/render versioning schema, frame-accurate feedback syntax, and binary release checklist that govern collaborative iteration between planner/author users and artist/director users.
Why:

- Emotion: Objective numeric rubrics eliminate vague, frustrating creative friction ("make it pop" → "increase hero-to-background OKLab $\Delta L$ from `0.22` to `0.45`").
- Attention: Frame-indexed review protocols focus iteration strictly on the highest-leverage visual and auditory defects.
- Production value: Structured multi-stage review Gates (`Gate 1: Style Frame`, `Gate 2: Animatic`, `Gate 3: Rough Playblast`, `Gate 4: Final Graded/Mixed Master`) prevent shipping un-caught render glitches, dead holds, or sync offsets.
- Clarity: Translates subjective director intuition into unambiguous, machine-actionable event and shader deltas.
- Cost: Catching a timing error at `Gate 2 (Animatic)` or `Gate 3 (Viewport Playblast)` costs `10×–50×` less compute and authoring time than catching it after `Gate 4` lightmap/simulation bakes.
  Rules:

1. **Four-Gate Progressive Approval Pipeline**:
   - **Gate 1 — Brief, Color Script & Hero Style Frames (`Static`)**: Verify objective (`≤ 15 words`), OKLCH harmony ratios (`60:30:10` / `85:15`), BT.709 grayscale hierarchy ($\Delta L \ge 0.35$), and `10%` thumbnail silhouette read before any animation begins.
   - **Gate 2 — Frame-Locked Animatic / 3D Previs (`Stepped/Coarse Motion + VO/Beat Grid`)**: Verify total runtime, shot durations vs. complexity, WPM/CPS reading budgets, `180°/30°` camera continuity, and hit-point sync (`0f` to `-2f`). **Lock editorial cut timing at Gate 2** before starting heavy simulation bakes.
   - **Gate 3 — Motion & Baking Playblast (`Full Easing + Baked Caches, Flat/Viewport Shading`)**: Verify 12-principle mechanics (squash-and-stretch volume conservation, anticipation, `1–3f` channel overlap, `≤ 15f` ensemble stagger spread, moving holds, zero VAT/RBD interpenetration).
   - **Gate 4 — Final Composited, Graded & Mastered Deliverable (`Full Shader + Post + Mix`)**: Verify linear-light compositing, optical post-effect kitsch ceilings, WCAG contrast/PSE flash safety, LUFS/dBTP audio mastering, and platform safe zones.
2. **Semantic Versioning & Immutable Naming Convention**:
   - Name all scene descriptions, baked caches, and rendered outputs using deterministic semantic tokens:
     `{project_id}_{sequence_id}_{shot_id}_{stage}_v{MAJOR}.{MINOR}_{aspect}_{fps}fps.{ext}`
     (e.g., `projA_seq01_sh030_anim_v02.01_16x9_24fps.mp4`), where `MAJOR` increments on structural/timing changes and `MINOR` increments on shader/polish tweaks. Never overwrite a previous render; never use ambiguous suffixes like `_final_NEW_v2_real.mp4` ([OpenUSD Asset Resolution](https://www.google.com/search?q=https%3A%2F%2Fopenusd.org%2Frelease%2Fintro.html)).
3. **Actionable Feedback Translation Protocol (No Vague Adjectives)**:
   - Every review note must specify: **(1) Exact SMPTE Timecode & Frame Range (`HH:MM:SS:FF` / `f_start–f_end`)**, **(2) Target Element ID**, **(3) Observable Defect Symptom**, and **(4) Quantitative Parameter Delta**:
     - _Forbidden_: `"The title entrance feels sluggish and hard to read."`
     - _Mandatory_: `"Frames 00:02:12–00:03:06 (f60–f78), element title_hero_01: linear ease feels mechanical and luminance contrast is 2.8:1. Change easing to expo_out (0.16, 1.0, 0.3, 1.0), reduce entrance duration from 28f to 14f, and darken background scrim by -0.8 EV to achieve contrast ≥ 7.0:1."`
4. **Quantitative 100-Point Production Rubric (Minimum Passing Score: `85/100`, Zero Critical Failures)**:
   - **Visual Hierarchy & Composition (`20 pts`)**: Focal $\Delta L \ge 0.35$, `≥ 35%` negative space, SMPTE/social safe zones respected, passes `10%` thumbnail check.
   - **Color & Pipeline Fidelity (`20 pts`)**: OKLCH harmony ratios (`60:30:10` / `85:15`), scene-linear compositing, zero 8-bit Mach banding (`TPDF dither active`), NCLC tags embedded.
   - **Kinetic & Animation Craft (`20 pts`)**: Appropriate easing families, anticipation/follow-through present, `1–3f` channel overlap, `≤ 15f` stagger spread, `180°` shutter motion blur.
   - **Editorial & Attention Flow (`20 pts`)**: `Frame 0` active launch, cuts on action (`-2f`) or J/L splits, eye-trace continuity (`≤ 15% W`), reading hold formula satisfied.
   - **Audio, Accessibility & Delivery (`20 pts`)**: Hits on `-1f` to `0f` transient, VO intelligibility (`+8–14 LU` over ducked music), exact target LUFS/dBTP, WCAG contrast `≥ 4.5:1` and PSE flash limit `≤ 3 Hz` passed (_any PSE violation or missing license = automatic `0/100` critical failure_).
     Event mapping: Review manifest `review_feedback_log(version="v02.01", gate=4, rubric_score=92, notes=[{frame_range: [60, 78], target_id: "title_hero_01", channel: "easing", from: "linear", to: "expo_out"}])`.
     Raster/bake note: Render a burned-in **Review Slate & HUD** on `Gate 2` and `Gate 3` review exports (displaying `SMPTE Timecode`, `Global Frame Number`, `Shot ID`, `Version String`, `Camera Focal Length`, and `Active LUT/Color Space` in the outer `3.5%` margin outside Action Safe) so feedback always cites exact frame numbers; disable the HUD on `Gate 4` final delivery.
     Cultural notes: High-volume studio pipelines (studio dailies and synchronous frame-review sessions) enforce frame-numbered burn-ins and non-judgmental, parameter-specific notes focused on how the frame directs the audience's eye `[OPINION]`.
     Failure modes: Rendering `4K` final shaders and baked simulations before locking the edit timing in an animatic → `70%` of rendered frames are thrown away when the voiceover is trimmed; giving feedback in un-quantified adjectives ("make it edgier") → endless guessing loops.
     Checklist: [ ] Passed sequentially through Gate 1 (Style Frame), Gate 2 (Animatic), Gate 3 (Playblast), and Gate 4 (Final Master) [ ] Files versioned semantically (`_vMAJOR.MINOR_`) with burned-in frame/timecode HUD on review builds [ ] All feedback notes converted to `(Frame Range, Element ID, Symptom, Numeric Delta)` [ ] Scores `≥ 85/100` on the Quantitative Production Rubric with zero critical safety/legal failures
     Sources: [OpenUSD Documentation](https://www.google.com/search?q=https%3A%2F%2Fopenusd.org%2Frelease%2Fintro.html); [SMPTE Timecode Standards](https://www.google.com/search?q=https%3A%2F%2Fwww.smpte.org%2Fblog%2Funderstanding-standards-time-code); [Netflix VFX \& Editorial Review Specifications](https://www.google.com/search?q=https%3A%2F%2Fstudiopartner.netflix.net%2Fstudio%2Fbranded-vfx-media-review-delivery-specifications).
