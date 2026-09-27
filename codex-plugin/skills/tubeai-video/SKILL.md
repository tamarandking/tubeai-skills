---
name: tubeai-video
description: Set up or continue a local YouTube video production project with Remotion. Use Codex workspace and terminal tools to configure the machine, build branded scenes, edit recordings, and render/export video deliverables. Requires a local Codex environment for computer access; TubeAI research is optional.
---

# TubeAI video production in Codex

This skill adapts the existing TubeAI workflow for Codex. It is designed for Codex with the user's local project open and terminal access. A ChatGPT Work conversation without a local workspace cannot install software, access the user's GPU, inspect local footage, or render video; in that case, help with the creative brief and ask the user to open the project in Codex for local production.

## Read the source workflow first

When the repository checkout is available, read `skills/tubeai-video/SKILL.md` in full. Treat its technical recipes as the production specification for setup, project layout, hardware checks, media sourcing, Remotion scenes, voice and transcription, raw-recording edits, timelines, rendering, QA, and troubleshooting.

This skill is the Codex execution overlay:

- Use the current local shell, filesystem, and workspace tools to do the work directly. Do not depend on Claude Code, Claude in Chrome, Claude subagents, `.claude/agents/`, or Claude-specific install commands.
- For reusable project instructions, create/update root `AGENTS.md` with pointers to `GUIDELINES.md` and `PROJECTS.md`. Keep `GUIDELINES.md` as the production source of truth.
- Use the connected TubeAI MCP server only if its tools appear in this session. If the optional server is missing or authentication fails, continue with web research where appropriate and say TubeAI-specific database/workspace features are unavailable.
- Never claim that a command, install, render, transcription, timeline export, or QA check succeeded unless you ran it and inspected the result.

## Local setup

For a new project:

1. Confirm this is a local Codex session and inspect the current folder. Do not overwrite a non-empty folder or install the project into an unrelated repository; ask for a project location when it is not clear.
2. Run the source workflow's hardware check for the actual OS, CPU, memory, GPU/driver, laptop status, and free disk. Use the results to select video encoding, voice/transcription model sizes, and render concurrency. Do not guess hardware.
3. Before installing system packages or downloading large models, show one concise list of the tools and approximate model/disk requirements from the source workflow and obtain the user's approval. Then continue without asking again for the same approval. Respect any OS permission prompts the user must accept.
4. Follow the source workflow's Setup recipe to install Node LTS, FFmpeg, yt-dlp, Deno, Python 3.12, Remotion packages, Playwright Chromium, the isolated Python environment, PyTorch, Qwen3-TTS, CrisperWhisper, and OpenTimelineIO. Keep all `@remotion/*` packages on the same version. Use a dedicated project folder and keep raw recordings out of Remotion's public media folder.
5. Build the project structure, core components/templates/scripts, and channel files described by the source workflow. Preserve its paths and output formats. Replace Claude-only docs/agents with `AGENTS.md`; do not create unusable Claude agent files as a Codex requirement.
6. Ask for channel name/brand assets and a style reference when needed. Do not block independent setup work while waiting for creative details.
7. Run the source workflow's smoke checks: GPU/browser rendering, a short template render and visual QA, a short test transcription and voice line when model downloads are approved, a short yt-dlp test clip, and timeline round-trip validation. Report each result accurately and fix failures where possible.

When continuing an existing project, first read `AGENTS.md`, `GUIDELINES.md`, `PROJECTS.md`, the channel's `CHANNEL.md`, and the video's `BRIEF.md`. Keep branding and user-provided media intact, update project status, and work on the next concrete step.

## Production workflow

- **Ideas and research:** use TubeAI tools when available; otherwise conduct attributed web research when suitable. Keep source links with factual claims and media.
- **Scripts and briefs:** develop the hook, promise, narrative beats, voiceover, scene list, on-screen text, and CTA in the channel's voice.
- **Animated scenes:** build in Remotion, reuse channel animations and shared templates, use brand values from `theme.ts`, and time elements from the video's word timings or insert windows. Preview stills/video before final rendering.
- **Voice and transcripts:** use the local Qwen3-TTS and CrisperWhisper setup only when present and verified. Use a real person's voice clone only with their permission.
- **Recording edits:** preserve the original recording. Cut only clear false starts, flubs, and retakes unless the user asks for tighter pacing. Verify every edit join and create editable Premiere XML, Final Cut FCPXML, and Resolve OTIO timelines as specified in the source workflow.
- **Rendering:** use the project scripts and hardware settings from the source workflow. Keep long jobs in visible progress with short updates. QA output duration, playback, timing, and flash frames before delivery.

## Safety and reporting

- Ask before installing tools, downloading large models, overwriting existing project files, or spending paid-service credits. Never place secrets in project files.
- Keep user-provided source media read-only; do not move or delete it.
- Respect licenses, consent, and access controls. Do not bypass paywalls.
- If the local shell, GPU, network, or a model is unavailable, state the specific limitation and finish any independent creative or code work.
- Deliver exact output paths and describe which editor or next step uses each file.
