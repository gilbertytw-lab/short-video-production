# short-video-production

An open Agent Skill for producing short videos through nine review gates, from script to final cut.

The workflow follows the [Agent Skills specification](https://agentskills.io/specification): script → storyboard → narration → audio-based timeline → style concept → three static frames → three animated scenes → full animation → final approval.

The workflow supports Gemini 3.8 Flash TTS when available or user-recorded narration. It does not depend on a private voice, a particular source video, or a specific rendering project. The first implementation used Remotion and FFmpeg; other renderers can follow the same review gates. Bring a video renderer and media inspection tools appropriate for your workspace; Gemini TTS is optional.

## Install

Clone this repository, then place or symlink the `short-video-production` folder at a location supported by your agent. `SKILL.md` must be at the root of that folder.

| Agent | Personal skill location | Documentation |
|---|---|---|
| Codex | `~/.agents/skills/short-video-production/` | [Build skills](https://learn.chatgpt.com/docs/build-skills) |
| Claude Code | `~/.claude/skills/short-video-production/` | [Claude Code skills](https://code.claude.com/docs/en/skills) |
| Gemini CLI | `~/.gemini/skills/short-video-production/` or `~/.agents/skills/short-video-production/` | [Gemini CLI Agent Skills](https://geminicli.com/docs/cli/skills/) |

The core instructions use the open `SKILL.md` format. `agents/openai.yaml` only supplies optional OpenAI interface metadata. Invocation syntax and media tools vary by agent; the workflow requires a renderer and a way to inspect the output video.

In Codex, invoke it with a request such as:

> Use $short-video-production to turn this article into a 60-second vertical video. Let me approve each of the nine stages. I will record the narration myself.

In Claude Code, invoke `/short-video-production` with the same request. In other compatible agents, ask the agent to use the installed skill.

The skill keeps the project's media and secrets outside this repository. It ends after approval of the complete video; uploading or publishing is a separate task.

## 中文速覽

這個 Skill 依序交付腳本、分鏡、語音、依實際音長建立的時間軸、風格概念、前三幕靜態稿、前三幕動畫、完整動畫與最終審核。每一關都提供實際檔案或預覽，取得核准後再繼續。語音可選 Gemini 3.8 Flash TTS 或使用者自行錄音。

使用範例：

> 使用 $short-video-production，把這篇文章做成 60 秒直式短影音；請逐關讓我審核，我會自行錄旁白。

詳見 [SKILL.md](SKILL.md)、[artifact contracts](references/artifact-contracts.md) 與 [review guide](references/review-guide.md)。
