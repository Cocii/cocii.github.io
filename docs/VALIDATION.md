# Website validation, 2026-10-19

## Assets

Verified all 60 original WAV files with the Python standard-library WAV decoder: positive frame counts, matching manifest duration/sample rate/channel count, and SHA-256 matches. All 60 audio hashes are distinct. Synthesized clips are 22,050 Hz; four speaker references are 24,000 Hz and two are 48,000 Hz. Total WAV size: 23,183,320 bytes. No resampling or normalization was applied.

All 64 binary deployment assets (60 WAVs and four fonts) were uploaded using GitHub's blob API and their returned Git blob SHA-1 values were checked against hashes computed from the local bytes.

## Browser checks

Tested in the Codex in-app browser, using the actual audio files:

- Successful playback and advancing media time.
- V to VR switching preserved an observed position of 3.4 seconds; V paused and VR continued from that position.
- Only VRT played after rapid V → VR → VRT switching.
- Reference playback paused synthesized playback.
- Changing speaker or prompt reset all four current players to paused at zero with correct source paths.
- Disabling position lock let the next method start at its own position.
- Waveform click seeking worked at the desktop viewport; keyboard End moved playback to 8.66 seconds. Pointer-coordinate checks at the emulated mobile viewport were inconclusive because of browser automation coordinate scaling, so no mobile touch-drag claim is made.
- A deliberately unavailable audio file, served from a fresh local origin, produced an actionable error. Restoring the file and selecting Play recovered playback with no reload required. The original file was restored before deployment.
- A download link returned the expected WAV file.
- Screenshots inspected at the default desktop viewport and 390 × 844 mobile viewport. Mobile document width and scroll width both measured 390 px.
- `node --check site/app.js` passed.

## Review and regression fixes

An independent review identified two playback/accessibility bugs. The real playback handlers were exercised in a Node VM with delayed media events. Tests reproduced the loss of a queued position during V → VR → VRT switching and a missing live error announcement after playback had started. Both tests failed before their respective fixes, then passed. A third test checks independent positions with position lock disabled. Run `node --test scripts/position-lock.test.cjs`.

At 320px the speaker grid originally forced the workspace wider than its clipped boundary: the rightmost button reached 330.25px while the workspace ended at302px. Below360px the grid now uses two columns. After correction, all speaker buttons end at or before291px, the comparison panel ends at301px, and the workspace ends at302px. Document width and scroll width both remain320px. Touch targets were enlarged for playback, references, selects and the position-lock label.

The initial GitHub Pages deployment succeeded in [workflow run39266005604](https://github.com/Cocii/cocii.github.io/actions/runs/39266005604). The public HTTPS page rendered and actual playback was verified there. Subsequent pushes run JavaScript syntax and playback regression checks before deployment.

The focused follow-up review found no remaining blocking correctness issues and independently ran the three passing regression tests. These checks are media integrity checks, direct browser smoke tests and focused timing regressions, not model evaluation or an exhaustive device compatibility certification.
