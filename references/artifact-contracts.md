# Artifact contracts

These are portable shapes, not a required renderer or directory tree. Reuse an existing project's naming where possible. Store large audio/video outside the skill folder; the skill repository contains instructions only.

| Gate | Suggested artifact | Minimum content |
|---|---|---|
| 1 | `source-notes.md`, `script.md` | Source links or supplied brief; supported claims and uncertainties; full spoken text, language, intended audience, target duration, CTA if any. |
| 2 | `storyboard.md` | Stable scene IDs; exact approved lines assigned to shots; visual subject/action, on-screen text, transition, rough duration. No spoken line omitted. |
| 3 | `audio/original.*` or `audio/scene-XX.*`, `audio-manifest.json` | Approved narration, continuous or per scene; origin (`gemini-tts` or `user-recording`), path, processing such as speed/trim, measured duration, approval version. |
| 4 | `timeline.json`, caption draft, selected scene audio | Scene spans measured from approved audio; extracted scene clips if needed; gap policy; caption text and local start/end; no overlap or negative interval. |
| 5 | `style-direction.md` | Concept, palette, type, original asset approach, motion, caption style, output format, safe-area plan and reference links. |
| 6 | `style-frames/scene-01.png` etc. | First three full-resolution frames plus a review image showing the safe-area overlay. Keep editable source files. |
| 7 | `review/first-three.mp4` | Approved narration, timed captions, scene motion, and transitions; individual scene clips when practical. |
| 8 | `review/full.mp4`, `review/full.srt` | All scenes and final captions, plus useful scene previews. |
| 9 | `review/qa.md`, `review/approvals.md` | Media checks, known limits, file paths, final approval date and exact version or hash. |

## Script and storyboard

Keep the script as spoken text, separate from camera directions. If line breaks identify subtitle units, say so explicitly and keep them after approval. The storyboard should map each scene ID to the exact script span it covers. A shot can contain multiple caption lines; caption line breaks do not force separate TTS calls.

Storyboard row example:

| Scene | Approved narration | Main visual/action | On-screen text | Transition | Rough length |
|---|---|---|---|---|---|
| s01 | Paste exact script lines | Show the central question visually | Short hook | Cut to s02 | Estimate only |

## Audio manifest and timeline

Store the selected audio route and measured duration, for example:

```json
{
  "id": "narration-take-1",
  "source": "user-recording",
  "file": "audio/narration-original.wav",
  "processing": "none",
  "durationSeconds": 48.7
}
```

For a continuous recording, keep this original and document the scene cuts created at gate 4. For per-scene TTS or recordings, list each selected scene take in the manifest.

Use one timeline timebase throughout. `startSeconds` and `endSeconds` below bound audible scene content; `gapAfterSeconds` is separate. Caption times are local to that scene's audio. The renderer may convert these seconds to frames using the chosen fps.

```json
{
  "fps": 30,
  "scenes": [
    {
      "id": "s01",
      "audio": "audio/s01.wav",
      "startSeconds": 0,
      "endSeconds": 4.2,
      "gapAfterSeconds": 0.2,
      "captions": [
        {"text": "Approved script line", "startSeconds": 0.1, "endSeconds": 1.5}
      ]
    }
  ]
}
```

For each scene, check `endSeconds - startSeconds` against the selected audio duration. The next scene starts after the prior end plus its gap. Caption intervals must fit the scene audio, preserve the approved text in order, and be readable on screen. If the audio changes, recalculate the timeline and all affected captions before rendering.

## Approval record

Record gate, status, artifact path/version, date, and user feedback in `review/approvals.md`. A clear statement in the conversation counts as approval; copy its outcome into the record. Use a content hash or versioned filename for the final media so the approved cut can be identified later. A review request is not an approval.
