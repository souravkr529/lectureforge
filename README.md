<div align="center">
  <h1>🧠 LectureForge: AI-Powered Explainer Video Generator</h1>
  <p><strong>Turn any text prompt into a narrated, animated educational video using LLMs and Manim.</strong></p>
  <p>
    <a href="https://github.com/souravkr529/lectureforge/stargazers"><img src="https://img.shields.io/github/stars/souravkr529/lectureforge" alt="Stars Badge"/></a>
    <a href="https://github.com/souravkr529/lectureforge/network/members"><img src="https://img.shields.io/github/forks/souravkr529/lectureforge" alt="Forks Badge"/></a>
    <a href="https://github.com/souravkr529/lectureforge/issues"><img src="https://img.shields.io/github/issues/souravkr529/lectureforge" alt="Issues Badge"/></a>
    <a href="https://github.com/souravkr529/lectureforge/blob/main/LICENSE"><img src="https://img.shields.io/github/license/souravkr529/lectureforge" alt="License Badge"/></a>
  </p>
</div>

## 📖 About LectureForge

LectureForge is an advanced open-source **AI Video Generator** tailored for educators, developers, and content creators. It seamlessly combines **LLM scriptwriting (OpenAI/Claude)**, **Text-To-Speech (TTS)**, mathematical animations via **Manim**, and a self-healing compiler pipeline to automatically create stunning, polished explainer videos from a single text prompt.

Whether you want to explain *Quantum Computing*, *LLM Tokenizers*, or *Advanced Calculus*, LectureForge structures the topic into logical scenes, generates Python code for high-quality visual animations, syncs it flawlessly with human-like AI voiceovers, and stitches everything into a final MP4.

If you are looking for an open-source alternative to AI video creation platforms specifically tuned for education, STEM, and diagramming—LectureForge is built for you!
## Demo

![LectureForge Demo](demo/lectureforge-demo.gif)

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

---

## 🔍 Keywords & Tags
`#AIVideoGenerator` `#TextToVideo` `#Manim` `#Python` `#OpenAI` `#Claude` `#GenerativeAI` `#EdTech` `#Automation` `#TextToAnimation` `#AutoVideo` `#LLM` `#VideoProcessing`

*Built for GitHub discoverability: AI video generator, text to video open source, topic to video AI, manim animation automation, Python video creation, explainer video generator, educational AI tools, script to video, automated teaching slides, ai generated presentation.*
