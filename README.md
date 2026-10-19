# Adversarial TTS: audio samples

A listening companion for **Adversarial Text-to-Speech Synthesis Against Forensic Deepfake Detection** by Jiayan Cui, Davide Salvi, Paolo Bestagini and Stefano Tubaro, Politecnico di Milano.

**Website:** https://cocii.github.io/bigvgan-spl/

## Listen

Compare V (baseline), VR (RawNet2) and VRT (RawNet2 + TSSD) across six speakers and three prompts. Each speaker also has a separate reference recording with different text. AASIST is held out of vocoder fine-tuning.

The interface supports single-track playback, waveform seeking, optional playback-position matching when switching vocoders, and WAV downloads. It includes responsive layouts, keyboard controls and reduced-motion support.

## Run locally

This is a buildless static website. No package installation or server-side API is needed.

```bash
python3 -m http.server 8765 --bind 127.0.0.1
```

Open `http://127.0.0.1:8765/bigvgan-spl/`.

## Files

- `bigvgan-spl/index.html`: paper introduction, audio workspace and method explanation.
- `bigvgan-spl/style.css`: responsive visual system.
- `bigvgan-spl/app.js`: sample selection, waveform rendering and playback controls.
- `bigvgan-spl/samples.json`: six speakers, three prompt excerpts, sample metadata and waveform peaks.
- `bigvgan-spl/assets/audio/`: 60 original WAV files, preserved without resampling or normalization.
- `bigvgan-spl/assets/fonts/`: self-hosted Manrope fonts and their SIL Open Font License.
- `ASSET_SOURCES.md`: source and attribution details.
- `index.html`: entry-point redirect to the project page.
- `.nojekyll`: static GitHub Pages publishing marker.

## Audio provenance

The recordings come from the author's [original audio samples page](https://h0yjmbl9to9.feishu.cn/docx/FH7mdd1dco6xDkxFlhPchve8nyh). The manifest includes the original filename, SHA-256, exact duration, sample rate, channel count and 96 waveform peaks for every file. All 60 recordings have distinct hashes. Reference clips use their original sample rates; synthesized clips use 22,050 Hz.

Prompt excerpts are derived from the attachment filenames rather than verified full transcripts. Gorou and Yae Miko are identified in the source collection as Genshin Impact character voices by miHoYo. See [ASSET_SOURCES.md](ASSET_SOURCES.md).

## Publishing and maintenance

GitHub Pages publishes the `master` branch from `/ (root)`. The project lives at `/bigvgan-spl/`, leaving room for other projects in this account's Pages repository. Update a recording and its corresponding manifest metadata together.

The experiment code remains in a separate repository and is being prepared for public release. The page intentionally labels that future release as `Code soon`.
