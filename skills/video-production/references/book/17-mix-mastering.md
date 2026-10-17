<!-- Book page 17 | Mix & Mastering | Source: motion_and_video_production_manual.md -->

## 17. Mix & Mastering

### 17.1 Dialogue/VO Intelligibility, Spectral Slotting, Ducking/Sidechain, EQ, and Compression

Definition: The dynamic and spectral balancing of Dialogue/Voiceover (DX), Music (MX), and Sound Effects (SFX) buses so vocal intelligibility remains effortless across all playback systems ([ITU-R BS.1770](https://www.google.com/search?q=https%3A%2F%2Fwww.itu.int%2Frec%2FR-REC-BS.1770); [Netflix Sound Mix Specifications](https://www.google.com/search?q=https%3A%2F%2Fstudiopartner.netflix.net%2Fstudio%2Fbranded-sound-mix-spec-and-best-practices)).
Why:

- Emotion: Warm, intimate vocal compression and smooth look-ahead music ducking keep the human voice emotionally present and authoritative.
- Attention: The human brain prioritizes speech above all other sounds; if music masks the `1–4 kHz` consonant band, the viewer expends cognitive effort straining to hear and abandons the video.
- Production value: Dynamic spectral sidechain ducking (carving only the `800 Hz – 4 kHz` vocal presence pocket out of the music while leaving sub-bass and stereo air intact) sounds infinitely more polished than crude full-band volume fader drops.
- Clarity: Guarantees `100%` consonant articulation (`s`, `t`, `k`, `p`, `f`) even on tiny smartphone mono speakers.
- Cost: Standardized bus templates (DX, MX, SFX, Master) with deterministic EQ, compression, and look-ahead sidechain parameters automate broadcast-ready mixing.
  Rules:

1. **Dialogue / Voiceover (DX) Bus Processing Chain**:
   - **High-Pass Filter (HPF)**: Apply an `18–24 dB/octave` Butterworth high-pass filter at **`75–90 Hz`** (male/deep voice) or **`95–115 Hz`** (female/higher voice) to remove plosive rumble and HVAC noise.
   - **Subtractive Mud Cut**: Cut `-2.0 to -4.0 dB` ($Q = 1.5\text{–}2.5$) in the **`220–350 Hz`** boxy/muddy chest resonance zone.
   - **Consonant Intelligibility Presence Boost**: Boost `+1.5 to +3.0 dB` ($Q = 1.0\text{–}1.8$) at **`2.5–4.5 kHz`** (where human ear sensitivity peaks per Fletcher-Munson equal-loudness contours).
   - **De-Essing**: Attenuate harsh sibilance (`5.5–8.5 kHz`) dynamically by `-3 to -6 dB` when sibilant peaks exceed threshold.
   - **Serial Two-Stage Vocal Compression**: (a) Fast Peak Catcher (`Ratio = 4:1`, `Attack = 2–5 ms`, `Release = 40–60 ms`, reducing peaks by `2–4 dB`) followed by (b) Smooth Leveler (`Ratio = 2.5:1`, `Attack = 15–30 ms`, `Release = 120–200 ms`, `3–5 dB` gain reduction) so dynamic range stays within a tight **`4–8 LU`** window.
2. **Music (MX) Ducking & Spectral Slotting (Look-Ahead Sidechain)**:
   - Maintain an average **Dialogue-to-Music Loudness Ratio of `+8 to +14 LU`** while the narrator is speaking (e.g., if VO sits at `-16 LUFS`, duck the music bed to `-24 to -30 LUFS`).
   - Use **Look-Ahead Sidechain Ducking**: ramp music attenuation down **`150–250 ms` (`4–6 frames`) BEFORE** the first spoken syllable (`Attack = 150 ms`), hold through inter-word gaps `< 0.6 s` (`Hold = 400 ms` to prevent nauseating up-and-down pumping between words), and recover smoothly over **`600–1,000 ms`** (`Release = 800 ms`, `sine/cubic` curve) after the sentence ends `[OPINION]`.
   - Combine broadband ducking (`-4 to -6 dB`) with **Dynamic Spectral EQ Ducking (`-4 to -6 dB` bell cut at `1.0–4.0 kHz`, $Q = 0.8$)** triggered by the DX bus so the music's bass groove (`60–150 Hz`) and high shimmer (`10 kHz+`) remain rich while the vocal pocket is completely clear.
3. **Mono Compatibility & Small-Speaker Translation Check**:
   - Sum the master stereo mix to **Mono (`L + R`)** and apply a simulated phone band-pass filter (`300 Hz – 10 kHz`): verify that phase correlation stays strictly positive (`correlation ∈ [+0.3, +1.0]`, never `< 0.0`) and that sub-bass elements (`< 90 Hz`) include upper-harmonic saturation (`120–240 Hz` overtones) so bass lines and impacts remain audible on laptop/phone speakers.
     Event mapping: Audio bus DSP graph `mix_graph_config(dx_hpf_hz=85, dx_comp_gr_db=5.0, mx_duck_lookahead_ms=180, mx_duck_broadband_db=-5.0, mx_duck_spectral_1k_4k_db=-5.0, mx_duck_hold_ms=400, mx_duck_release_ms=800)`.
     Raster/bake note: N/A — Audio DSP operates on floating-point `32-bit` PCM sample streams prior to final deliverable muxing.
     Cultural notes: Theatrical cinema mixes allow wide dynamic range (`LRA = 10–18 LU`) where whispers and explosions differ by `20+ dB`; mobile and social video mixes require aggressive dynamic compression (`LRA = 4–7 LU`) because viewers listen in noisy subways, cafes, or at low volume `[OPINION]`.
     Failure modes: Setting sidechain ducking release to `50 ms` with `0 ms` hold → the music violently pumps up and down between every single word the narrator speaks; leaving acoustic guitars, synth leads, or brass blaring at `1.5–3.5 kHz` at `-16 LUFS` under a `-16 LUFS` voiceover → speech becomes completely unintelligible.
     Checklist: [ ] DX high-passed at `80–100 Hz` and compressed within `4–8 LU` dynamic range [ ] Music sits `8–14 LU` below active speech via broadband + `1–4 kHz` spectral ducking [ ] Sidechain ducking uses `150–250 ms` look-ahead, `400 ms` hold, and `600–1000 ms` release (zero word-to-word pumping) [ ] Stereo phase correlation `≥ +0.3` and mono `300 Hz–10 kHz` small-speaker check passed
     Sources: [ITU-R BS.1770-5](https://www.google.com/search?q=https%3A%2F%2Fwww.itu.int%2Frec%2FR-REC-BS.1770); [EBU R 128](https://www.google.com/search?q=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FEBU_R_128); [Netflix Sound Mix Specifications and Best Practices](https://www.google.com/search?q=https%3A%2F%2Fstudiopartner.netflix.net%2Fstudio%2Fbranded-sound-mix-spec-and-best-practices).

### 17.2 Loudness Standards (LUFS, True Peak, LRA) and Deliverable Stems

Definition: The K-weighted integrated loudness normalization (`LUFS` / `LKFS`), 4×-oversampled inter-sample True Peak ceiling (`dBTP`), Loudness Range (`LRA` in `LU`), and separated multi-track stem packaging mandated by international broadcast and streaming specifications ([ITU-R BS.1770](https://www.google.com/search?q=https%3A%2F%2Fwww.itu.int%2Frec%2FR-REC-BS.1770); [EBU R 128](https://www.google.com/search?q=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FEBU_R_128)).
Why:

- Emotion: Delivering at the exact platform target loudness preserves the intended punch of transients without triggering harsh, flattened platform limiting or downward turning.
- Attention: Prevents the viewer from having to reach for their volume buttons when transitioning into or out of the user's video.
- Production value: Adhering to `-1.0 to -2.0 dBTP` True Peak ceilings prevents inter-sample DAC clipping distortion when PCM audio is transcoded to lossy `AAC` or `Opus` streams.
- Clarity: Delivers clean separated `DX`, `MX`, `SFX`, and `M&E` (Music & Effects) stems so localization into foreign languages requires zero re-mixing.
- Cost: Automated loudness normalization and brickwall true-peak limiting in the final master bounce guarantees zero QC rejections from broadcasters or ad networks.
  Rules:

1. Master and verify all final mixes against the **Target Platform Loudness & True Peak Specification** measured per [ITU-R BS.1770-4/5](https://www.google.com/search?q=https%3A%2F%2Fwww.itu.int%2Frec%2FR-REC-BS.1770) and [EBU Tech 3341 / 3342](https://www.google.com/search?q=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FEBU_R_128):

| Delivery Platform / Standard                                                                                                                                                    | Integrated Loudness Target (`LUFS` / `LKFS`)                | Max Short-Term (`3 s`)   | Maximum True Peak (`dBTP`, 4× oversampled)                | Loudness Range (`LRA` in `LU`)            |
| :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---------------------------------------------------------- | :----------------------- | :-------------------------------------------------------- | :---------------------------------------- |
| **European Broadcast ([EBU R 128](https://www.google.com/search?q=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FEBU_R_128))**                                                         | **`-23.0 LUFS`** (`±0.5 LU`, or `±1.0 LU` for live)         | `-18 LUFS` (commercials) | **`-1.0 dBTP`**                                           | `5–15 LU`                                 |
| **US / North American Broadcast (ATSC A/85)**                                                                                                                                   | **`-24.0 LKFS`** (`±2.0 LU` anchor / program)               | `-18 LKFS`               | **`-2.0 dBTP`**                                           | `6–15 LU`                                 |
| **Netflix / Prestige Streaming ([Netflix Spec](https://www.google.com/search?q=https%3A%2F%2Fstudiopartner.netflix.net%2Fstudio%2Fbranded-sound-mix-spec-and-best-practices))** | **`-27.0 LKFS`** (`±2.0 LU` dialogue-gated per BS.1770-1/3) | —                        | **`-2.0 dBTP`**                                           | `8–18 LU`                                 |
| **YouTube / Web Video / Social ([YouTube Spec](https://support.google.com/youtube/answer/1722171?hl=en))**                                                                      | **`-14.0 LUFS`** (`±1.0 LU`, range `-14 to -16 LUFS`)       | `-10 LUFS`               | **`-1.0 to -1.5 dBTP`** (prevents AAC transcode clipping) | **`4–8 LU`**                              |
| **TikTok / Instagram Reels / Mobile Feed**                                                                                                                                      | **`-14.0 to -16.0 LUFS`**                                   | `-11 LUFS`               | **`-1.0 to -1.5 dBTP`**                                   | **`3–6 LU`** (tight mobile dynamic range) |

2. **Why `-1.0 to -2.0 dBTP` Headroom is Mandatory for Lossy Codecs**: Even if a `48 kHz` PCM waveform peaks at `-0.1 dBFS`, reconstructing the continuous analog wave between samples (`True Peak`) and passing it through psychoacoustic lossy encoders (`AAC` at `128–256 kbps` or `Opus`) shifts phase and adds **`+0.6 to +1.2 dB`** of peak overshoot. Setting the brickwall True Peak limiter (`4×` polyphase FIR oversampling) to **`-1.5 dBTP`** for web/social (and **`-2.0 dBTP`** for broadcast/Netflix) guarantees zero crackle after platform re-encoding ([ITU-R BS.1770](https://www.google.com/search?q=https%3A%2F%2Fwww.itu.int%2Frec%2FR-REC-BS.1770); [Netflix Sound Mix Specs](https://www.google.com/search?q=https%3A%2F%2Fstudiopartner.netflix.net%2Fstudio%2Fbranded-sound-mix-spec-and-best-practices)).
3. **Mandatory Deliverable Stem Package**:
   - Export all audio masters at **`48 kHz` sample rate, `24-bit` linear PCM (`.wav`)** perfectly sample-locked (`0 sample offset`, exact same duration) to the video master ([Netflix Sound Mix Specs](https://www.google.com/search?q=https%3A%2F%2Fstudiopartner.netflix.net%2Fstudio%2Fbranded-sound-mix-spec-and-best-practices)):
     1. `Full_Mix` (Composite Master at target LUFS).
     2. `M&E_Mix` (Music + Sound Effects + Foley with all master bus processing preserved, minus Dialogue/VO—for international dubbing).
     3. `DX_Stem` (Isolated processed Dialogue/Voiceover stem).
     4. `MX_Stem` (Isolated Music stem).
     5. `SFX_Stem` (Isolated Sound Effects & Ambience stem).
   - Verify **Stem Reconstruction Identity**: summing `DX_Stem + MX_Stem + SFX_Stem` at `0.0 dB` unity gain must match `Full_Mix` within `±0.5 LU` (achieved by triggering any master-bus limiter sidechain from the Full Mix while bouncing individual stems).
     Event mapping: Master audio export pipeline `audio_master_export(sample_rate_hz=48000, bit_depth=24, target_lufs=-14.0, true_peak_ceiling_dbtp=-1.5, lra_max_lu=7.0, export_stems=["Full_Mix", "MnE", "DX", "MX", "SFX"])`.
     Raster/bake note: N/A — Audio mastering and stem rendering execute in the offline audio mix pass prior to container muxing.
     Cultural notes: During the 2000s "Loudness War", television commercials crushed mixes to `-8 LUFS` to scream over `-24 LUFS` programs, prompting mandatory legal enforcement of EBU R128 (Europe) and the CALM Act / ATSC A/85 (US), followed by `-14 LUFS` normalization across YouTube and streaming platforms.
     Failure modes: Exporting a YouTube/TikTok video at `-24 LUFS` (broadcast level) → sounds `10 dB` quieter (`half as loud`) than every other video on the mobile feed because YouTube turns loud videos _down_ to `-14 LUFS` but does **not** turn quiet videos _up_ above `0 dB` gain; exporting a hot `-6 LUFS` mix peaking at `0.0 dBFS` → platform turns it down by `-8 dB` while AAC encoding clips every transient into crunchy distortion.
     Checklist: [ ] Integrated loudness matches target (`-14 LUFS` web/social; `-23 LUFS` EBU R128; `-24 LKFS` ATSC; `-27 LKFS` Netflix) [ ] True Peak ceiling capped at `-1.0 to -2.0 dBTP` via `4×` oversampled limiter [ ] Loudness Range (`LRA`) kept within `4–8 LU` for web/mobile or `8–18 LU` for cinema/streaming [ ] `48 kHz / 24-bit` synchronous stems (`Full`, `M&E`, `DX`, `MX`, `SFX`) exported and phase-verified
     Sources: [ITU-R BS.1770-5](https://www.google.com/search?q=https%3A%2F%2Fwww.itu.int%2Frec%2FR-REC-BS.1770); [EBU R 128 Specification](https://www.google.com/search?q=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FEBU_R_128); [Netflix Sound Mix Specifications](https://www.google.com/search?q=https%3A%2F%2Fstudiopartner.netflix.net%2Fstudio%2Fbranded-sound-mix-spec-and-best-practices); [YouTube Recommended Upload Settings](https://support.google.com/youtube/answer/1722171?hl=en).
