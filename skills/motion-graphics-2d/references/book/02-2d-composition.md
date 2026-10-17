<!-- Book page 02 | 2D Composition | Source: motion_and_video_production_manual.md -->

## 2. 2D Composition

### 2.1 Grids, Alignment Systems, and Visual Hierarchy

Definition: The division of the `+X/+Y` image plane into modular spatial columns, rows, margins, and gutters that govern element placement and establish a strict 3-level reading order.
Why:

- Emotion: Conveys structural order, institutional authority, and calm confidence; deliberate grid-breaking injects localized rebellion or surprise.
- Attention: Reduces saccadic search time by aligning edge transients along shared vertical and horizontal axes.
- Production value: Shared alignment axes and proportional gutters are the primary visual divider between professional Swiss-grade design and amateur layout ([Müller-Brockmann, Grid Systems in Graphic Design](https://www.google.com/search?q=https%3A%2F%2Fwww.thriftbooks.com%2Fw%2Fgrid-systems-in-graphic-design%2F393087%2F)).
- Clarity: Visually groups related information via spatial proximity and separates distinct data tiers.
- Cost: Parametric grid snapping eliminates manual per-element coordinate guesswork across aspect-ratio adaptations.
  Rules:

1. Construct a modular grid of `12 columns × 8 rows` for `16:9` frames (or `6 columns × 12 rows` for `9:16` vertical frames) with outer margins set to `5%–8%` of the shortest frame dimension and inter-column gutters set to `1.5%–2.5%` of frame width ([Müller-Brockmann, Grid Systems in Graphic Design](https://www.google.com/search?q=https%3A%2F%2Fwww.thriftbooks.com%2Fw%2Fgrid-systems-in-graphic-design%2F393087%2F)).
2. Enforce a maximum of `3` distinct visual hierarchy levels on screen simultaneously (Primary Focal Anchor, Secondary Supporting Context, Tertiary Metadata/Caption), separated by a minimum scale ratio of `1.414:1` ($\sqrt{2}$) or `1.618:1` ($\phi$) between levels ([Bringhurst, The Elements of Typographic Style](https://www.google.com/search?q=https%3A%2F%2Fwww.thriftbooks.com%2Fw%2Fthe-elements-of-typographic-style_robert-bringhurst%2F278779%2F)).
3. Maintain a macro-to-micro whitespace ratio of `≥ 2.5:1`: the distance between separate content groups must be at least `2.5×` the internal padding or line spacing within a group ([Müller-Brockmann, Grid Systems in Graphic Design](https://www.google.com/search?q=https%3A%2F%2Fwww.thriftbooks.com%2Fw%2Fgrid-systems-in-graphic-design%2F393087%2F)).
4. Restrict simultaneous text alignment axes to at most `2` per frame (e.g., all elements left-aligned to Column 2 and Column 7); never mix centered, left-justified, and right-justified text blocks within the same visual band.
   Event mapping: Declarative layout coordinates expressed in normalized grid-cell units `(col_start, col_span, row_start, row_span)` resolved to world `+X/+Y` planar coordinates at scene compilation.
   Raster/bake note: N/A — 2D grid coordinates resolve deterministically in vertex transformation prior to rasterization.
   Cultural notes: The Swiss International Style (Josef Müller-Brockmann, Karl Gerstner) mandates strict mathematical grid adherence and flush-left ragged-right sans-serif type; East Asian editorial layouts (Japanese _tategaki_ / modular magazines) frequently combine dense multi-axis cellular grids with vertical and horizontal typographic flow ([Müller-Brockmann, Grid Systems in Graphic Design](https://www.google.com/search?q=https%3A%2F%2Fwww.thriftbooks.com%2Fw%2Fgrid-systems-in-graphic-design%2F393087%2F)).
   Failure modes: Near-miss alignment (elements offset by `2–8 px` from a shared axis without clearly breaking the grid) → reads as an accidental layout error; equal spacing between all elements → flat hierarchy where the viewer does not know where to look first.
   Checklist: [ ] Modular column/row grid defined with `5%–8%` outer margins [ ] Maximum 3 hierarchy levels with `≥ 1.414:1` scale separation [ ] Macro-to-micro whitespace ratio `≥ 2.5:1` [ ] Zero near-miss (`2–8 px`) alignment offsets
   Sources: [Müller-Brockmann, Grid Systems in Graphic Design](https://www.google.com/search?q=https%3A%2F%2Fwww.thriftbooks.com%2Fw%2Fgrid-systems-in-graphic-design%2F393087%2F); [Bringhurst, The Elements of Typographic Style](https://www.google.com/search?q=https%3A%2F%2Fwww.thriftbooks.com%2Fw%2Fthe-elements-of-typographic-style_robert-bringhurst%2F278779%2F).

### 2.2 Framing, Rule of Thirds, Golden Ratio, Negative Space, and Balance

Definition: The proportional distribution of positive visual mass and open negative space across the frame to control equilibrium, tension, and focal gaze weight.
Why:

- Emotion: Symmetrical central framing evokes monumental stability, authority, or clinical detachment; asymmetric off-center framing with expansive negative space evokes dynamism, isolation, or contemplation ([Block, The Visual Story](https://www.google.com/search?q=https%3A%2F%2Fwww.routledge.com%2FThe-Visual-Story-Creating-the-Visual-Structure-of-Film-TV-and-Digital-Media%2FBlock%2Fp%2Fbook%2F9781138014152)).
- Attention: Places primary subjects at high-salience intersection nodes (`1/3` or `1/φ`) where natural eye-scanning patterns converge.
- Production value: Intentional negative space (`≥ 35%` of frame area) prevents the cluttered, "fill-every-pixel" look common in amateur motion graphics.
- Clarity: Separates the figure from the ground so silhouettes and motion trajectories read instantaneously.
- Cost: High negative-space compositions require fewer background assets and reduce fragment shader overdraw.
  Rules:

1. Place primary focal anchors within `±3%` of either the **Rule of Thirds** intersections (`X ∈ {0.333, 0.667}`, `Y ∈ {0.333, 0.667}`) or the **Golden Ratio (Phi Grid)** intersections (`X ∈ {0.382, 0.618}`, `Y ∈ {0.382, 0.618}`), reserving exact dead-center (`0.500, 0.500`) strictly for formal symmetry, tunnel/portal shots, or rapid short-form caption lockups ([Block, The Visual Story](https://www.google.com/search?q=https%3A%2F%2Fwww.routledge.com%2FThe-Visual-Story-Creating-the-Visual-Structure-of-Film-TV-and-Digital-Media%2FBlock%2Fp%2Fbook%2F9781138014152); [Mascelli, The Five C's of Cinematography](https://www.google.com/search?q=https%3A%2F%2Fwww.silmanjamespress.com%2Fshop%2Ffilmmaking-directing%2Fthe-five-cs-of-cinematography%2F)).
2. Preserve a minimum of `35%–50%` of total frame area as **Negative Space** (uncluttered background with local luminance variance `σ_L < 0.05` in OKLab) in standard narrative/editorial frames, and `≥ 65%` in luxury/minimalist brand frames `[OPINION]`.
3. Balance asymmetric compositions using the visual fulcrum law: a small, high-contrast/high-chroma/moving element at distance $d_1$ from frame center balances a larger, low-contrast/static element at distance $d_2$ when $\text{Area}_1 \times \text{Contrast}_1 \times d_1 \approx \text{Area}_2 \times \text{Contrast}_2 \times d_2$ ([Block, The Visual Story](https://www.google.com/search?q=https%3A%2F%2Fwww.routledge.com%2FThe-Visual-Story-Creating-the-Visual-Structure-of-Film-TV-and-Digital-Media%2FBlock%2Fp%2Fbook%2F9781138014152)).
4. Provide **Lead Room (Nose/Motion Room)**: allocate `60%–65%` of horizontal free space _in front_ of a moving or looking subject's vector, unless intentionally cramping the subject against the frame edge (`< 15%` lead room) to signify psychological trapping or imminent collision ([Mascelli, The Five C's of Cinematography](https://www.google.com/search?q=https%3A%2F%2Fwww.silmanjamespress.com%2Fshop%2Ffilmmaking-directing%2Fthe-five-cs-of-cinematography%2F)).
   Event mapping: Planar element or camera framing offset event setting normalized screen-space anchor `(u, v)` to `(0.382, 0.618)` or `(0.333, 0.667)` with a lead-room offset vector proportional to subject velocity `v_subject`.
   Raster/bake note: N/A — Framing and spatial balance are geometric layout properties evaluated prior to pixel shading.
   Cultural notes: Classical Chinese and Japanese ink-wash aesthetics (_ma_ / emptiness) treat negative space as an active, substantive medium rather than an absence; Western maximalist retail/arcade graphics frequently compress negative space below `20%` to simulate sensory abundance `[OPINION]`.
   Failure modes: Placing a profile or moving subject looking/moving toward the nearest frame edge without narrative justification ("short-siding") → creates accidental claustrophobia; tangential contact where a subject's edge barely kisses the frame border or another object's contour → flattens depth and creates visual irritation.
   Checklist: [ ] Focal anchor at `1/3`, `1/φ`, or deliberate `0.5` symmetry [ ] Negative space occupies `≥ 35%` of frame area [ ] Asymmetric visual weight balanced across center fulcrum [ ] `60%–65%` lead room in direction of gaze/motion [ ] Zero accidental tangents with frame edges
   Sources: [Block, The Visual Story](https://www.google.com/search?q=https%3A%2F%2Fwww.routledge.com%2FThe-Visual-Story-Creating-the-Visual-Structure-of-Film-TV-and-Digital-Media%2FBlock%2Fp%2Fbook%2F9781138014152); [Mascelli, The Five C's of Cinematography](https://www.google.com/search?q=https%3A%2F%2Fwww.silmanjamespress.com%2Fshop%2Ffilmmaking-directing%2Fthe-five-cs-of-cinematography%2F).

### 2.3 Safe Areas, Storyboarding Continuity, Cuts, Edits, and 2D Effects

Definition: The protective boundary margins inside the active raster and the cross-shot screen-location continuity rules that prevent essential graphic elements from being clipped by displays or lost by the viewer's eye across 2D cuts.
Why:

- Emotion: Preserves compositional poise across cuts so the viewer stays immersed in the narrative flow.
- Attention: Minimizes the eye's re-acquisition distance (`Δpos` across a cut) so gaze locks onto the incoming focal point within `100–150 ms` ([Murch, In the Blink of an Eye](https://www.google.com/search?q=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FIn_the_Blink_of_an_Eye_%28Murch_book%29)).
- Production value: Prevents logos, lower thirds, and kinetic titles from colliding with television bezels or social platform UI overlays.
- Clarity: Guarantees 100% visibility of critical text and icons across broadcast and mobile viewports.
- Cost: Authoring within universal safe zones allows a single master render to pass multi-platform QC without re-layout.
  Rules:

1. For `16:9` broadcast/streaming deliverables, keep all critical action inside the **Action Safe Area** (`93%` width × `93%` height, i.e., `3.5%` margin on all four edges) and all legible text/logos inside the **Title Safe Area** (`90%` width × `90%` height, i.e., `5.0%` margin on all four edges) per [SMPTE ST 2046-1](https://www.google.com/search?q=https%3A%2F%2Fwww.smpte.org%2Fhubfs%2FSMPTE%2520Standards%2520Quarterly%2520Report%2520September%25202024%2520%281%29.pdf%3FhsLang%3Den) (or the legacy EBU/broadcast `80%` width × `90%` height title safe when targeting older CRT/overscan distribution).
2. For `9:16` vertical social deliverables (`1080×1920`), enforce asymmetric **Platform UI Safe Zones**: keep top `12%` (`230 px`), bottom `22%–25%` (`420–480 px`), and right `15%` (`160 px`) clear of essential text or faces to prevent occlusion by status bars, captions/descriptions, and engagement buttons ([TikTok In-Feed Ad Specs](https://www.google.com/search?q=https%3A%2F%2Fads.tiktok.com%2Fresources%2Fhelp%2Farticle%2Ftiktok-auction-in-feed-ads%3Flang%3Den); [Meta/Instagram Reels Specs](https://www.google.com/search?q=https%3A%2F%2Fwww.facebook.com%2Fbusiness%2Fhelp%2F1038071743007909)).
3. Maintain **Gaze Anchor Continuity** across fast 2D cuts (`shot duration < 48 frames` at `24 fps`): place the incoming shot's primary focal point within a radius of `≤ 15%` of frame width from the outgoing shot's final focal point ([Murch, In the Blink of an Eye](https://www.google.com/search?q=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FIn_the_Blink_of_an_Eye_%28Murch_book%29)).
4. Limit 2D drop shadows and layer glows on graphic elements to motivated depth separation: drop shadow opacity `12%–28%`, blur radius `1.5%–4.0%` of element height, and vertical offset `0.5%–1.5%` of element height `[OPINION]`.
   Event mapping: Scene-level bounding constraint validator clipping or flagging any `text_element` or `hero_planar_element` whose world-to-NDC bounding box exceeds `[x_min_safe, x_max_safe] × [y_min_safe, y_max_safe]`.
   Raster/bake note: 2D layer effects (drop shadow, inner glow, stroke bevel) should be evaluated as separable 2-pass Gaussian/distance-field fragment shaders on the element's planar quad rather than multi-sampling geometry in 3D space.
   Cultural notes: East Asian variety television and live-stream graphics intentionally populate the outer perimeter with persistent multi-colored _telop_ reaction banners while keeping the center `60%` clear for action; Western cinema and prestige streaming strictly forbid persistent perimeter banners `[OPINION]`.
   Failure modes: Placing subtitles or CTA buttons in the bottom `15%` of a `9:16` vertical video → completely covered by platform username and caption UI; jumping the focal point from far top-left to far bottom-right across a `15-frame` cut → viewer misses the incoming subject entirely.
   Checklist: [ ] `16:9` graphics inside `90%` SMPTE ST 2046-1 Title Safe [ ] `9:16` graphics clear of top `12%`, bottom `25%`, and right `15%` UI zones [ ] Gaze anchor jumps `≤ 15%` frame width on fast cuts (`< 2 s`) [ ] 2D drop shadows stay within `12%–28%` opacity
   Sources: [SMPTE ST 2046-1](https://www.google.com/search?q=https%3A%2F%2Fwww.smpte.org%2Fhubfs%2FSMPTE%2520Standards%2520Quarterly%2520Report%2520September%25202024%2520%281%29.pdf%3FhsLang%3Den); [Murch, In the Blink of an Eye](https://www.google.com/search?q=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FIn_the_Blink_of_an_Eye_%28Murch_book%29); [TikTok In-Feed Ad Specs](https://www.google.com/search?q=https%3A%2F%2Fads.tiktok.com%2Fresources%2Fhelp%2Farticle%2Ftiktok-auction-in-feed-ads%3Flang%3Den); [Meta/Instagram Reels Specs](https://www.google.com/search?q=https%3A%2F%2Fwww.facebook.com%2Fbusiness%2Fhelp%2F1038071743007909).
