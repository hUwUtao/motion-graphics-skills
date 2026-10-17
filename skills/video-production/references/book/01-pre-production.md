<!-- Book page 01 | Pre-Production | Source: motion_and_video_production_manual.md -->

## 1. Pre-Production

### 1.1 Brief, Objective, and Audience Specification

Definition: A structured, machine-readable contract defining the single communication objective, target viewer constraints, platform geometry, and measurable success thresholds before any scene authoring begins.
Why:

- Emotion: Aligns every downstream visual and auditory cue toward a single target affective state rather than contradictory tonal signals.
- Attention: Constrains information density to match the viewing environment's typical gaze commitment (e.g., feed scroll vs. theater seating).
- Production value: Eliminates mid-production style drift and incoherent asset assembly that expose amateur planning.
- Clarity: Enforces a single primary message proposition per deliverable so the user's audience retains the core takeaway.
- Cost: Prevents expensive late-stage re-bakes of 3D lighting, simulations, and voiceover recordings caused by undefined deliverables.
  Rules:

1. State the core message in `≤ 15 words` containing exactly one primary verb and one target outcome `[OPINION]`.
2. Specify delivery aspect ratio (`16:9`, `9:16`, `1:1`, `4:5`, or `2.39:1`), master resolution (`1920×1080` or `3840×2160`), and exact frame rate (`23.976`, `24`, `25`, `29.97`, `30`, or `60 fps`) per [ITU-R BT.709](https://www.google.com/search?q=https%3A%2F%2Fwww.itu.int%2Frec%2Fr-rec-bt.709) and [ITU-R BT.2020](https://www.google.com/search?q=https%3A%2F%2Fwww.itu.int%2Frec%2Fr-rec-bt.2020-2-201510-i%2Fen) before laying out any planar or 3D element.
3. Define the primary viewing distance and screen diagonal: mobile hand-held (`30–40 cm`, `15 cm` diagonal, viewing angle `~20°`), desktop monitor (`50–70 cm`, `60 cm` diagonal, viewing angle `~45°`), or living-room/cinema (`2.0–3.5×` picture height per [ITU-R BT.2100](https://www.google.com/search?q=https%3A%2F%2Fwww.itu.int%2Frec%2Fr-rec-bt.2100)).
4. Lock the target emotional valence (`[-1.0, +1.0]`) and arousal (`[0.0, 1.0]`) coordinates for each structural act of the sequence `[OPINION]`.
   Event mapping: Scene root metadata block declaring `duration_total`, `fps`, `aspect_ratio`, `color_space_working`, `color_space_output`, `audio_target_lufs`, and global sequence markers (`act_1_start`, `climax_cue`, `cta_cue`).
   Raster/bake note: N/A — Pre-production specification operates at the scene metadata and pipeline configuration layer prior to GPU rasterization.
   Cultural notes: East Asian commercial briefs frequently prioritize high-context relational mood and brand harmony before product utility, whereas North American and Northern European direct-response briefs prioritize explicit problem-solution hooks within the first `3.0 seconds` `[OPINION]`.
   Failure modes: Dual competing objectives in one brief → split visual hierarchy where neither message registers; unspecified viewing device → typography and fine shader detail become illegible when a desktop-authored `16:9` master is viewed on a mobile screen.
   Checklist: [ ] Single `≤ 15-word` objective defined [ ] Aspect ratio, resolution, and frame rate locked [ ] Target viewing environment and sound-on/sound-off ratio specified [ ] Target valence/arousal trajectory declared
   Sources: [ITU-R BT.709](https://www.google.com/search?q=https%3A%2F%2Fwww.itu.int%2Frec%2Fr-rec-bt.709); [ITU-R BT.2020](https://www.google.com/search?q=https%3A%2F%2Fwww.itu.int%2Frec%2Fr-rec-bt.2020-2-201510-i%2Fen); [ITU-R BT.2100](https://www.google.com/search?q=https%3A%2F%2Fwww.itu.int%2Frec%2Fr-rec-bt.2100); [Block, The Visual Story](https://www.google.com/search?q=https%3A%2F%2Fwww.routledge.com%2FThe-Visual-Story-Creating-the-Visual-Structure-of-Film-TV-and-Digital-Media%2FBlock%2Fp%2Fbook%2F9781138014152).

### 1.2 Script, Copy, and Reading-Rate Budgeting

Definition: The time-coded verbal and typographic text of a production, budgeted in words per minute (WPM) and characters per second (CPS) against visual action windows.
Why:

- Emotion: Controls vocal breathing room and dramatic pauses that allow emotional beats to land.
- Attention: Prevents verbal-visual interference (dual-coding overload) where simultaneous dense speech and dense on-screen text cause viewer drop-off.
- Production value: Well-paced copy sounds deliberate and authoritative rather than rushed or time-compressed.
- Clarity: Ensures spoken voiceover and on-screen kinetic/caption text remain within human phonological processing limits.
- Cost: Locking word counts before animation prevents re-timing entire event sequences when voiceover recordings overrun the timeline.
  Rules:

1. Budget spoken voiceover at `130–150 WPM` (`2.1–2.5 words/second`) for conversational/educational clarity, `110–125 WPM` for dramatic/cinematic gravitas, and never exceed `170 WPM` (`2.8 words/second`) even in high-energy promotional spots `[UNVERIFIED]`.
2. Budget on-screen display copy (non-caption titles and callouts) at `≤ 12–15 CPS` (`≤ 180 WPM`) and `≤ 7–10 words` per visual card so the viewer can read the text and still inspect the visual subject ([Netflix Timed Text Style Guide / Partner Help](https://www.google.com/search?q=https%3A%2F%2Fstudiopartner.netflix.net%2Fstudio%2Fdelivery-specifications-and-requirements-external)).
3. Allocate mandatory silent breathing holds of `12–24 frames` (`0.5–1.0 s`) between major topical sentences to allow cognitive consolidation ([Chion, Audio-Vision](https://www.google.com/search?q=https%3A%2F%2Fbooks.google.com%2Fbooks%2Fabout%2FAudio_vision.html%3Fid%3Dis_HyxAyMkMC)).
4. Never display on-screen text that differs semantically from simultaneous spoken voiceover; either match key anchor words verbatim or place text during vocal pauses `[OPINION]`.
   Event mapping: Sequence of `audio_vo_cue` events (`start`, `duration`, `transcript`, `phoneme_markers`) paired with `text_display_event` cues whose `duration ≥ max(1.5s, char_count / 14.0)`.
   Raster/bake note: N/A — Script and copy budgeting occurs at the temporal sequencing layer before geometry or shader evaluation.
   Cultural notes: Fast-cut social feeds (TikTok, Reels, Shorts) tolerate `155–165 WPM` with zero inter-sentence pause, whereas broadcast documentary and European cinema standards favor `115–130 WPM` with `1.0–2.0 s` atmospheric pauses `[OPINION]`.
   Failure modes: Writing `200+ WPM` copy for a fixed `30-second` slot → voiceover sounds breathless and pitch-shifted, leaving zero frames for visual reaction; mismatching spoken words and simultaneous screen text → viewer reads neither and loses comprehension.
   Checklist: [ ] Voiceover word count within `110–150 WPM` budget [ ] On-screen display text `≤ 15 CPS` [ ] Minimum `0.5 s` pause between major clauses [ ] Zero semantic contradiction between simultaneous VO and screen text
   Sources: [Chion, Audio-Vision](https://www.google.com/search?q=https%3A%2F%2Fbooks.google.com%2Fbooks%2Fabout%2FAudio_vision.html%3Fid%3Dis_HyxAyMkMC); [Netflix Partner Help Center](https://www.google.com/search?q=https%3A%2F%2Fstudiopartner.netflix.net%2Fstudio%2Fdelivery-specifications-and-requirements-external).

### 1.3 Moodboard, Style Frames, and Visual Anchors

Definition: Curated visual reference matrices (moodboards) and full-resolution rendered key frames (style frames) that lock the exact lighting, color palette, typography, texture, and post-processing look of each sequence prior to animation.
Why:

- Emotion: Tests and verifies the exact affective tone of color, light, and texture combinations on a static frame before committing to motion.
- Attention: Validates focal hierarchy and luminance contrast ratios at the exact delivery aspect ratio.
- Production value: Establishes a bespoke art-directed signature (e.g., Swiss typographic precision vs. tactile stop-motion clay) rather than generic default shaders.
- Clarity: Gives planner/author users and artist/director users an unambiguous visual target for every scene.
- Cost: Catching shader, palette, or typographic flaws on 4 static frames costs `< 5%` of fixing them across `1,800` animated frames.
  Rules:

1. Produce at least `1` Hero Style Frame per distinct narrative scene (or `1` every `10–15 seconds` of runtime) rendered at `100%` final delivery resolution through the exact target raster shader and color transform pipeline ([Block, The Visual Story](https://www.google.com/search?q=https%3A%2F%2Fwww.routledge.com%2FThe-Visual-Story-Creating-the-Visual-Structure-of-Film-TV-and-Digital-Media%2FBlock%2Fp%2Fbook%2F9781138014152)).
2. Verify every Style Frame in three diagnostic views: (a) Full color, (b) Grayscale luminance only (`Y = 0.2126R + 0.7152G + 0.0722B` per [ITU-R BT.709](https://www.google.com/search?q=https%3A%2F%2Fwww.itu.int%2Frec%2Fr-rec-bt.709)) to confirm focal hierarchy survives without hue, and (c) Downscaled thumbnail at `10%` resolution (`192×108 px` or `108×192 px`) to confirm silhouette readability ([Birn, Digital Lighting and Rendering](https://www.google.com/search?q=https%3A%2F%2F3drender.com%2Flight%2Findex.html)).
3. Extract explicit numeric tokens from approved Style Frames: exact OKLCH palette swatches, key-to-fill light intensity ratios, camera focal length (`mm`), depth-of-field aperture (`f-stop`), and post-process bloom/grain intensities.
   Event mapping: Static snapshot of the declarative scene graph evaluated at a single hero timestamp `t_hero` with all lighting, material, and post-processing channels active at reference intensity.
   Raster/bake note: Style frames must be rendered using the exact target GPU raster pipeline and baked lightmap/probe architecture rather than an offline path tracer, so material response and shadow softness match final production capability.
   Cultural notes: Bauhaus and Swiss International Style frames rely on asymmetric grid tension, flat high-contrast planes, and objective grotesque typography ([Müller-Brockmann, Grid Systems in Graphic Design](https://www.google.com/search?q=https%3A%2F%2Fwww.thriftbooks.com%2Fw%2Fgrid-systems-in-graphic-design%2F393087%2F)); Memphis and Neo-Brutalist frames employ clashing high-chroma primaries, thick black outlines (`3–6 px`), and geometric pattern fills.
   Failure modes: Creating moodboards only from third-party path-traced films without testing in the target raster pipeline → final output falls short of approved look; skipping grayscale thumbnail check → hero subject blends into mid-tone background (`ΔL < 0.15` in OKLab).
   Checklist: [ ] `≥ 1` style frame per scene at native delivery resolution [ ] Passes BT.709 grayscale luminance hierarchy check [ ] Passes `10%` thumbnail silhouette check [ ] Numeric palette, lens, and shader tokens extracted
   Sources: [ITU-R BT.709](https://www.google.com/search?q=https%3A%2F%2Fwww.itu.int%2Frec%2Fr-rec-bt.709); [Block, The Visual Story](https://www.google.com/search?q=https%3A%2F%2Fwww.routledge.com%2FThe-Visual-Story-Creating-the-Visual-Structure-of-Film-TV-and-Digital-Media%2FBlock%2Fp%2Fbook%2F9781138014152); [Birn, Digital Lighting and Rendering](https://www.google.com/search?q=https%3A%2F%2F3drender.com%2Flight%2Findex.html); [Müller-Brockmann, Grid Systems in Graphic Design](https://www.google.com/search?q=https%3A%2F%2Fwww.thriftbooks.com%2Fw%2Fgrid-systems-in-graphic-design%2F393087%2F).

### 1.4 Storyboard, Animatic, Shot List, Asset List, and Schedule

Definition: The sequential blueprint translating script and style frames into timed shot panels (storyboard), a frame-accurate temp-audio video edit (animatic), and a dependency-ordered inventory of all required 2D/3D assets, bakes, and events.
Why:

- Emotion: Validates macro-pacing, comedic or dramatic timing, and audio-visual sync before spending effort on fine splining or simulation bakes.
- Attention: Reveals dead zones where visual state remains static for too long (`> 4.0–5.0 s` without motivated internal motion or cut).
- Production value: Ensures seamless screen-direction continuity and intentional camera progression across cuts.
- Clarity: Verifies that every narrative beat is visually legible in sequence at real-time playback speed.
- Cost: Prevents building or baking high-resolution assets for shots that get trimmed or cut during editorial pacing review.
  Rules:

1. Draw or block a new storyboard panel for every cut AND for every major intra-shot camera move or compositional shift (minimum `2–3 panels` per moving shot: start frame, midpoint, end frame) ([Mascelli, The Five C's of Cinematography](https://www.google.com/search?q=https%3A%2F%2Fwww.silmanjamespress.com%2Fshop%2Ffilmmaking-directing%2Fthe-five-cs-of-cinematography%2F)).
2. Assemble the **Animatic** (or 3D layout **Previs**) locked to the scratch/final voiceover and temp music beat grid at the exact master frame rate, establishing every shot's exact `frame_in`, `frame_out`, and `duration_frames` ([Williams, The Animator's Survival Kit](https://www.google.com/search?q=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FThe_Animator%2527s_Survival_Kit)).
3. Add a `12–24 frame` (`0.5–1.0 s`) head and tail handle budget to every baked 3D simulation or camera cache in the Shot List to allow editorial trim adjustments without re-baking `[OPINION]`.
4. Classify every item in the Asset List by screen-coverage tier: **Hero** (`> 25%` screen height; high-poly mesh `20k–100k tris`, `2048×2048` or `4096×4096` textures), **Secondary** (`8–25%` screen height; `2k–15k tris`, `1024×1024` textures), or **Background/Prop** (`< 8%` screen height; `< 2k tris` or planar billboard card, `256×256`–`512×512` textures) `[OPINION]`.
   Event mapping: Top-level sequence manifest (`shots[]`) where each shot entry defines `shot_id`, `start_frame`, `duration_frames`, `camera_id`, `active_asset_ids[]`, and coarse blocking events (`transform_event` with stepped/hold interpolation for animatic phase, upgraded to eased curves in production).
   Raster/bake note: Use low-sample viewport rasterization (flat/matcap shading + screen-space ambient occlusion) to render 3D Previs animatics at `< 16 ms/frame` before committing to lightmap or simulation bakes.
   Cultural notes: Japanese television anime production boards (_ekonte_) explicitly annotate frame counts down to the exact exposure sheet (_timesheets_ on 1s, 2s, or 3s) alongside camera pan speed in millimeters per frame, whereas Western commercial boards emphasize key emotional style frames `[OPINION]`.
   Failure modes: Skipping the timed animatic and animating directly from static boards → shots run `30–50%` too long or too short for the voiceover; building `4K`-textured meshes for background props occupying `4%` of frame height → wasted VRAM and texture mipmap aliasing.
   Checklist: [ ] Every shot has start/mid/end storyboard panels [ ] Frame-accurate animatic locked to audio track [ ] Asset list tiered into Hero / Secondary / Background budgets [ ] `12–24 frame` head/tail handles included on all baked shot ranges
   Sources: [Mascelli, The Five C's of Cinematography](https://www.google.com/search?q=https%3A%2F%2Fwww.silmanjamespress.com%2Fshop%2Ffilmmaking-directing%2Fthe-five-cs-of-cinematography%2F); [Williams, The Animator's Survival Kit](https://www.google.com/search?q=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FThe_Animator%2527s_Survival_Kit); [OpenUSD Documentation](https://www.google.com/search?q=https%3A%2F%2Fopenusd.org%2Frelease%2Fintro.html).
