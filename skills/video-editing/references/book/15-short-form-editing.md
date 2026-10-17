<!-- Book page 15 | Attention & Short-Form Editing | Source: motion_and_video_production_manual.md -->

## 15. Attention & Short-Form Editing

### 15.1 Hook Architecture (0–3 s), Retention Beats, and Pattern Interrupts

Definition: The structural front-loading of visual kinetic novelty, open-loop curiosity propositions, and periodic multi-modal state resets (`every 3.0–6.0 seconds`) engineered to halt feed-scrolling within the first `1.0–3.0 seconds` and prevent habituation drop-off.
Why:

- Emotion: Triggers immediate epistemic curiosity ("open loop"), surprise, or high-arousal fascination before the viewer's thumb completes a swipe gesture.
- Attention: Interrupts automatic predictive coding in the visual and auditory cortex by introducing an unexpected scale, spatial, or sonic delta just as attention begins to decay.
- Production value: Starting on Frame 1 (`t = 0.00 s`) with active kinetic velocity and a clear visual focal contrast separates intentional short-form craft from repurposed broadcast edits that waste `2 seconds` fading in from black.
- Clarity: Establishes the exact stakes, topic, or visual promise within the first `72 frames` (`3.0 s` @ `24 fps` / `90 frames` @ `30 fps`).
- Cost: Restructuring existing scene events to front-load the climax teaser or highest-salience visual frame at `t = 0.0 s` costs zero extra asset creation while multiplying viewer retention.
  Rules:

1. **Zero-Frame Launch (Ban Black/Static Cold Opens)**: Frame `0` (`t = 0.000 s`) must already contain a fully lit, high-contrast focal subject ($\Delta L \ge 0.45$) AND active kinetic velocity (e.g., a camera push, object snap, or scale-in already at peak velocity on Frame `0–4`) plus a simultaneous audio transient or vocal consonant within the first `0–4 frames` (`≤ 130 ms`) `[OPINION]`. Never start a feed deliverable with a fade-from-black, a static logo slate, or an un-animated wide shot.
2. **Three-Part Hook Window (`0.0–3.0 seconds`)**:
   - **Visual Stopping Cue (`0.0–0.8 s`, Frames `0–24` @ `30 fps`)**: High-salience visual anomaly, dramatic scale shift (`ECU` → `WS` or rapid `1.0× → 1.35×` punch-in), or bold kinetic headline (`cap height 7%–12% H`) occupying the center-top reading zone.
   - **Verbal / Conceptual Open Loop (`0.5–2.2 s`)**: A concise `≤ 8-word` spoken + captioned premise that opens a specific cognitive gap (e.g., contrasting expectation vs. reality, or stating the outcome before the mechanism).
   - **First Visual State Change (`1.5–2.8 s`)**: Execute the first camera angle switch, B-roll/diagram overlay, or 3D stage transformation before `t = 3.0 s` to confirm high visual pacing `[OPINION]`.
3. **Retention Beat & Pattern Interrupt Cadence**:
   - Insert a **Micro Pattern Interrupt** every **`3.0–5.0 seconds`** (`90–150 frames` @ `30 fps`): a `15%–25%` digital/optical framing re-crop (punch-in/out), a graphic callout card entrance, a subtle camera angle flip (`≥ 30°`), or an acoustic texture shift (`whoosh` / music drop).
   - Insert a **Macro Structural Reset** every **`12.0–18.0 seconds`**: a full scene palette shift ($\Delta h \ge 60^\circ$ or $\Delta L \ge 0.30$), a shift from talking-head/A-roll to full-screen 3D/2D diagram, or a tempo/rhythm change `[OPINION]`.
   - **Overload Ceiling**: Never trigger pattern interrupts faster than `every 1.2 seconds` (`< 36 frames`) continuously for more than `4 seconds`, which induces sensory fatigue and cognitive detachment.
     Event mapping: `hook_sequence_event(start_frame=0, frame0_velocity_boost=1.5, headline_cue_end=24f, first_cut_frame=54f)` followed by `pattern_interrupt_scheduler(interval_min_s=3.0, interval_max_s=5.0, interrupt_types=["crop_punch_1.2x", "b_roll_insert", "graphic_overlay", "audio_drop"])`.
     Raster/bake note: N/A — Hook and pattern-interrupt scheduling operates on timeline camera/compositor events; when punching in `1.2×` on a raster layer, render the master scene at `1.25×` resolution (or evaluate vector/3D geometry natively via camera FOV narrowing) so punch-ins never soften pixel sharpness.
     Cultural notes: Vertical feed platforms ([TikTok](https://www.google.com/search?q=https%3A%2F%2Fads.tiktok.com%2Fresources%2Fhelp%2Farticle%2Ftiktok-auction-in-feed-ads%3Flang%3Den), [Instagram Reels](https://www.google.com/search?q=https%3A%2F%2Fwww.facebook.com%2Fbusiness%2Fhelp%2F1038071743007909), [YouTube Shorts](https://support.google.com/youtube/answer/1722171?hl=en)) conditioned global audiences to evaluate keep-vs-scroll decisions in `< 1.5 seconds`; however, prestige short-form design studios increasingly use "anti-chaos hooks"—a single arresting, hyper-detailed 3D tactile simulation (e.g., slicing a hyper-realistic glass/gel object) with crisp ASMR Foley rather than frantic jump cuts `[OPINION]`.
     Failure modes: Spending `0.0–2.5 s` on a brand logo intro + "Hey guys, welcome back..." throat-clearing → majority of feed viewers swipe away before the topic is even named; triggering a `1.3×` zoom + airhorn + flashing text every `0.8 seconds` for `30 seconds` → sensory exhaustion and zero brand trust.
     Checklist: [ ] Frame `0` is fully lit with active motion and audio within `≤ 4 frames` (zero fade-from-black) [ ] Visual hook, verbal open loop, and first visual change all complete by `t ≤ 3.0 s` [ ] Micro pattern interrupts scheduled every `3.0–5.0 s` [ ] Macro visual/palette resets scheduled every `12.0–18.0 s` [ ] Zero continuous sub-`1.2 s` flashing/cutting chains exceeding `4 s`
     Sources: [TikTok In-Feed Ad Specifications](https://www.google.com/search?q=https%3A%2F%2Fads.tiktok.com%2Fresources%2Fhelp%2Farticle%2Ftiktok-auction-in-feed-ads%3Flang%3Den); [Meta/Instagram Reels Specifications](https://www.google.com/search?q=https%3A%2F%2Fwww.facebook.com%2Fbusiness%2Fhelp%2F1038071743007909); [YouTube Encoding & Shorts Guidelines](https://support.google.com/youtube/answer/1722171?hl=en); [Murch, In the Blink of an Eye](https://www.google.com/search?q=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FIn_the_Blink_of_an_Eye_%28Murch_book%29).

### 15.2 Aesthetic vs. Attention Cuts, Loop Endings, 9:16 Framing, Caption-First, and Sound-Off Design

Definition: The architectural adaptation of framing, editing, typography, and timeline boundaries for vertical (`9:16`), sound-optional, auto-looping mobile viewports ([TikTok Ad Specs](https://www.google.com/search?q=https%3A%2F%2Fads.tiktok.com%2Fresources%2Fhelp%2Farticle%2Ftiktok-auction-in-feed-ads%3Flang%3Den); [Meta Reels Specs](https://www.google.com/search?q=https%3A%2F%2Fwww.facebook.com%2Fbusiness%2Fhelp%2F1038071743007909)).
Why:

- Emotion: Seamless loop endings create a pleasant cognitive double-take ("where did it restart?"); balancing attention cuts with aesthetic breathing room preserves emotional resonance.
- Attention: Caption-first central hierarchy ensures `100%` retention for sound-off viewers without forcing eye travel between the bottom of the screen and the subject's eyes.
- Production value: Native `9:16` vertical staging (stacking Subject + Graphic vertically along the central `60%` column) looks purposeful, whereas center-cropping a `16:9` horizontal master chops off shoulders, hands, and kinetic typography.
- Clarity: Visual self-sufficiency (sound-off comprehension) guarantees the core argument lands even when muted (`0 dB` volume).
- Cost: Designing modular vertical-first scene layouts (`+Y` stacking) allows automated aspect-ratio re-layout between `9:16`, `4:5`, and `16:9` via declarative anchor rules.
  Rules:

1. **Aesthetic Cuts vs. Attention Cuts Ratio**:
   - **Attention Cuts** (`ASL = 0.8–2.0 s`, zero breath pauses, jump cuts removing every `150 ms` vocal inhalation): use during the Hook (`0–3 s`) and high-density instructional lists.
   - **Aesthetic Cuts** (`ASL = 2.5–5.0 s`, motivated `L/J` cuts, `12–24 frame` musical/visual breathing holds): mandatory whenever emotional weight, luxury brand perception, or complex 3D beauty appreciation is the goal. In hybrid commercial pieces, alternate `2–3` fast Attention Cuts with `1` longer (`2.5–4.0 s`) Aesthetic Hold so the viewer can admire the craft `[OPINION]`.
2. **Seamless Loop Ending Architecture (`t = end → t = 0`)**:
   - **Visual Match Stitch**: Copy the exact camera transform, lighting state, and background geometry of `Frame 0` to `Frame N + 1` so the final `8–16 frames` of the video ease directly into the starting pose of `Frame 0` (or hide the `end → 0` boundary inside a `6-frame` whip pan / foreground mask pass that starts at `t = end - 3f` and finishes at `t = 0 + 3f`).
   - **Grammatical & Musical Bridge**: Write the final spoken clause at `t = end - 1.5 s` as the syntactic setup to the first clause at `t = 0.0 s` (e.g., ending with `"...and that is the exact reason why—"` → looping directly into Frame 0's `"[Hook statement]"`), while cutting the music clip on a tension beat (beat 4 of the bar) that resolves on beat 1 at `Frame 0` `[OPINION]`.
3. **9:16 Vertical Framing & Caption-First Hierarchy**:
   - Stack primary visual zones vertically along the `+Y` axis within the safe central corridor (`X ∈ [0.08, 0.85]`, `Y ∈ [0.14, 0.75]` from top):
     - **Upper-Mid Zone (`Y ∈ [0.18, 0.42]`)**: Primary 3D hero product, diagram, or speaker's eyes/face.
     - **Center-Lower Safe Zone (`Y ∈ [0.48, 0.68]`)**: **Caption-First Dynamic Typography Lockup** (`cap height = 4.5%–6.5% H`, `1–4 words` per burst or `≤ 2 lines`, high-contrast stroke/pill background $\ge 7:1$ contrast), placed immediately below the subject's chin/hands so the viewer reads captions in foveal vision without looking away from the action ([TikTok Ad Specs](https://www.google.com/search?q=https%3A%2F%2Fads.tiktok.com%2Fresources%2Fhelp%2Farticle%2Ftiktok-auction-in-feed-ads%3Flang%3Den)).
4. **The Sound-Off Self-Sufficiency Audit**:
   - Play the entire rendered video with audio muted (`-∞ dB`). Every narrative claim, metric, transition cue, and CTA must be `100%` intelligible via kinetic typography, visual diagrams, and visual hit accents alone.
     Event mapping: `vertical_layout_profile(aspect="9:16", hero_zone_y=[0.18, 0.42], caption_zone_y=[0.48, 0.68], ui_exclude_bottom=0.25, ui_exclude_right=0.15, loop_bridge_frames=8)`.
     Raster/bake note: When rendering a single 3D scene for both `16:9` (`1920×1080`) and `9:16` (`1080×1920`), never simply crop `1080 px` out of the center of the `1920×1080` raster buffer (which reduces horizontal resolution to `607×1080`). Switch the camera sensor gate to vertical `20.25 mm × 36 mm` (or use `Overscan / Vertical Sensor Fit`) and adjust secondary UI/title anchors via the declarative grid layout.
     Cultural notes: East Asian mobile video (Douyin, Xiaohongshu, Line VOOM) frequently layers dual-language or keyword-callout banners at `Y = 0.15` (top title banner) alongside dynamic speech captions at `Y = 0.65`, whereas Western Reels/TikTok favor a single clean dynamic caption lockup `[OPINION]`.
     Failure modes: Letting the music track fade out over `2 seconds` to silence at the end of a short-form video → signals to the viewer that the video is over, triggering an immediate swipe before the loop or CTA; placing key 3D action along the far left and far right edges of a `16:9` frame that will be cropped to `9:16` → action is completely amputated.
     Checklist: [ ] Attention cuts balanced with `2.5–4.0 s` aesthetic holds for hero craft moments [ ] Loop ending matches `Frame N+1` camera/pose/music to `Frame 0` [ ] `9:16` staging stacks Subject (`Y ∈ [0.18, 0.42]`) and Captions (`Y ∈ [0.48, 0.68]`) inside UI-safe zones [ ] Passed `100%` muted Sound-Off Comprehension Audit
     Sources: [TikTok Auction In-Feed Ad Specs](https://www.google.com/search?q=https%3A%2F%2Fads.tiktok.com%2Fresources%2Fhelp%2Farticle%2Ftiktok-auction-in-feed-ads%3Flang%3Den); [Meta/Instagram Reels Specs](https://www.google.com/search?q=https%3A%2F%2Fwww.facebook.com%2Fbusiness%2Fhelp%2F1038071743007909); [YouTube Shorts & Encoding Specs](https://support.google.com/youtube/answer/1722171?hl=en).
