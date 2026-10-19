# Asset sources

## Research content and recordings

Paper: **Adversarial Text-to-Speech Synthesis Against Forensic Deepfake Detection**, Jiayan Cui, Davide Salvi, Paolo Bestagini and Stefano Tubaro, Politecnico di Milano. Method descriptions were checked against the manuscript supplied by the author. Publication date, venue and DOI are omitted because the supplied manuscript does not establish them.

The 60 WAV files come from the author's existing [Audio Samples collection](https://h0yjmbl9to9.feishu.cn/docx/FH7mdd1dco6xDkxFlhPchve8nyh), accessed on 2026-10-19. There are six speaker references and 54 synthesized samples: six speakers × three prompts × three vocoders. Column mapping follows the source collection: reference, V, VR, VRT. The source filenames and SHA-256 values are preserved in `bigvgan-spl/samples.json` in the deployed repository (`site/samples.json` in the local authoring directory).

The source identifies Gorou and Yae Miko as characters from **Genshin Impact** by **miHoYo**. These examples and references are presented with that attribution. The font license does not extend to the audio recordings or other research materials; no new blanket license for those materials is asserted here.

Prompt excerpts are reconstructed from attachment filenames and are not verified full transcripts. Speaker references have different text from the synthesized prompts. The source introduction has inconsistent row numbering; the site uses the explicit speaker labels in the actual table.

## Typography

Manrope, weights 400, 600, 700 and 800, retrieved from Google Fonts. The font is distributed under the SIL Open Font License 1.1; the full notice is in `bigvgan-spl/assets/fonts/OFL.txt` (`site/assets/fonts/OFL.txt` locally).

- [Google Fonts Manrope source and license](https://github.com/google/fonts/tree/main/ofl/manrope)

## Artwork

The site icon is an original SVG. The hero illustration and interactive waveform displays are drawn from the imported audio waveform peaks. No stock imagery or synthetic speech is used.
