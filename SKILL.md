---
name: short-video-production
description: Produce a complete short-form video through review gates for script, storyboard, narration, timeline, visual style, three style frames, three animated scenes, and the full cut. Use for end-to-end video creation, not a script-only request.
---

# Short-form video production

Produce a reviewable vertical video from a user-provided source or brief. Follow the user's language, target platform, creative direction, and existing tool choices. The nine gates below are the workflow; a prior explicit approval satisfies its gate. Do not advance dependent work past a pending gate unless the user has authorized that advance or batch review.

Start by identifying the source or brief, intended audience/platform, approximate length, language, and available media. Keep approved versions and decisions in the job workspace. Use the [artifact contracts](references/artifact-contracts.md) when creating a new job; adapt filenames to an existing project rather than duplicating its files.

## Nine review gates

1. **Script draft.** Read the supplied material, preserve its source and factual limits, and draft a short video with a clear opening, one main takeaway, understandable progression, and an ending/CTA when appropriate. Show the complete spoken script for review. Do not treat source ingestion or AI generation as fact verification.
2. **Storyboard.** From the approved script, map every spoken beat to scenes/shots, on-screen text, visual action, transitions, and rough pacing. Show the storyboard for review. These are content and composition choices; final palette and typography belong to gate 5.
3. **Narration.** After storyboard approval, produce or collect the complete narration. Use Gemini 3.8 Flash TTS for each scene when that route is selected and available, or accept the user's recording as one continuous take or separate scene takes. Keep originals, document the route and any processing, listen for pronunciation, pacing, clipping, and omissions, then offer the audio for review. Never generate a replica of a person's voice without their authorization.
4. **Timeline.** Measure the approved audio. If it is one continuous recording, mark and extract its scene spans while preserving the original. Set scene boundaries, gaps, and caption intervals from actual sound. Preserve approved script wording; speech recognition may help with timing but does not rewrite captions. Show the timeline and a short synchronization preview or timing sheet for review.
5. **Style concept.** Let the user supply a direction or propose one based on the topic and audience. Specify original visual language, palette, typography, motion, caption treatment, and a platform-aware safe-area plan. Show references as inspiration, not assets to copy. Obtain approval before drawing finished frames.
6. **First three static frames.** Make one representative frame for each of the first three scenes, including key labels, plus a separate safe-area review overlay. Review them at the output resolution; revise until approved.
7. **First three animated scenes.** Animate those scenes with the approved audio and timed captions. Provide individual clips and one continuous preview. Inspect motion, text readability, transitions, audio sync, and safe area; revise until approved.
8. **Full animation.** Extend the approved system to every remaining scene. Render the complete cut, captions, and useful scene previews. Inspect each scene and transition; correct visible defects before requesting final review.
9. **Final approval.** Validate the delivered media and ask the user to watch the complete cut. Record approval of the exact final version, then hand over the video, captions, editable sources, and QA summary. Stop here; publication is a separate request.

At each gate, give the user the actual artifact or preview, a short list of decisions made, and the specific points to review. Record the decision and approved version. If feedback changes an earlier approved artifact, update affected downstream artifacts and revalidate them. Do not repeatedly ask for approval already given.

## Production checks

- Default to 9:16, 1080 × 1920, 30 fps only when the user has not set another format. Let actual narration duration determine the cut; storyboard durations are estimates.
- Keep titles, faces, essential visuals, captions, and CTA clear of likely platform overlays. Safe-area coordinates depend on platform and layout; use a conservative review overlay and check the target platform preview when available. A guide overlay must not appear in the delivered video.
- Keep narration and captions aligned, legible at phone size, and faithful to the approved script. Track selected emphasis and caption styling as project choices rather than universal defaults.
- Before the final gate, inspect representative frames and transitions, confirm file dimensions/frame rate/codec/audio, decode the full output, and check captions against the script. Include any unverified platform preview in the handoff summary.
- Use available production tools or the user's existing stack; do not assume any example project's files, private voice ID, API keys, or local paths exist. Keep secrets out of artifacts and logs.

For the concrete input/output fields and approval record, read [artifact contracts](references/artifact-contracts.md). For review criteria and what to show at each gate, read [review guide](references/review-guide.md) when preparing a handoff.
