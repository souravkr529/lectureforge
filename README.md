# Lecture Forge by Sourav

This project is designed to generate videos using animations, text-to-speech, and other features.

## GitHub Repository

[GitHub Repository Link](https://github.com/souravkr529/lectureforge)

# LectureForge

Turn any topic into a narrated, animated explainer video.

LectureForge combines LLM script writing, OpenAI TTS, Manim code generation, render-time auto-repair, and ffmpeg assembly to turn a plain prompt into a polished lesson video.

## Demo

![LectureForge Demo](demo/lectureforge-demo.gif)

- Sample output: [demo/lectureforge-demo.mp4](demo/lectureforge-demo.mp4)
- Prompt used: `Explain my students regarding Tokenizer in LLM`

## Why It Looks Better Than Typical AI Video Demos

- It does not generate pixels directly. It generates structured animation code, then renders with Manim.
- Each scene is planned as narration plus a matching animation description.
- Audio duration is fed back into scene generation so motion can match the voiceover.
- Failed renders are sent back into an auto-fix loop with the real compiler error.
- Scene continuity is preserved by passing previous-scene context into the next scene.

## Pipeline

`Topic -> Script JSON -> TTS -> Scene Code -> Manim Render -> Auto Repair -> Final MP4`

## Features

- Prompt-to-video workflow with Flask API + frontend
- Claude or OpenAI for scene planning and Manim code generation
- OpenAI TTS for narration
- Multi-scene video stitching with ffmpeg
- Self-healing render loop for broken Manim scenes
- Downloadable MP4 output from the browser

## Tech Stack

- Python
- Flask
- OpenAI API
- Anthropic API
- Manim Community Edition
- ffmpeg / ffprobe

## Quickstart

```bash
git clone https://github.com/souravkr529/lectureforge.git
cd lectureforge
python -m pip install -e .
copy .env.example .env
python src/main.py
```

Open `http://127.0.0.1:5000`

## Environment Variables

```env
CLAUDE_API_KEY=...
OPENAI_API_KEY=...
CLAUDE_MODEL=claude-sonnet-4-6
OPENAI_MODEL=gpt-4.1
TTS_MODEL=tts-1
VOICE=alloy
```

## How It Works

1. The LLM breaks your topic into 6-8 short teaching scenes.
2. Each scene gets a short narration plus a specific animation concept.
3. TTS generates voiceover and scene-level audio duration.
4. Another LLM writes Manim code for each scene using the narration, animation brief, prior context, and timing.
5. If a scene fails to render, the compiler error is passed back to the model for repair.
6. Rendered clips are concatenated and merged with the final narration track.

## Project Structure

```text
src/
  main.py              Flask app and API routes
  video_generator.py   Orchestration pipeline
  animations.py        Scene script generation
  manim_generator.py   Manim code generation and repair
  tts_generator.py     Narration synthesis
  concat_video.py      Render, concat, and merge helpers
demo/
  lectureforge-demo.mp4
  lectureforge-poster.png
```

## Notes

- `manim`, `ffmpeg`, and `ffprobe` must be installed and accessible from your Python environment.
- Generated runtime artifacts in `content/` and `media/` are ignored from git.
- This repo ships with a real generated sample video so people can evaluate output quality immediately.

## License

MIT
