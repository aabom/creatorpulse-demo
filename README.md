# ⚡ CreatorPulse — Prompt to Publish

Interactive demo of the CreatorPulse video generation pipeline. Type a prompt, walk through each production step, and publish to YouTube — all from one interface.

**[Live Demo →](https://yourusername.github.io/creatorpulse-demo/)**

## What This Shows

CreatorPulse is an AI-powered SaaS platform that turns a single text prompt into a fully produced, published YouTube video. This is a frontend prototype demonstrating the 8-step pipeline flow:

1. **Script** — AI-generated voiceover script with hook, sections, and CTA
2. **SEO & Meta** — Title variants, description, and tags optimized for your audience
3. **Voiceover** — ElevenLabs neural voice selection with emotion control
4. **Visuals** — Stock footage and AI images matched to script segments
5. **Thumbnails** — Two A/B variants designed for click-through rate
6. **Assembly** — FFmpeg render combining video, audio, subtitles, and music
7. **Review** — Preview the final video with a full publish summary
8. **Publish** — Upload to YouTube with metadata and A/B thumbnail testing

Each step includes an approval gate so the creator stays in control of the output.

## Tech Stack

This demo is a single `index.html` file with zero build steps:

- **React 18** via CDN
- **Babel** for in-browser JSX compilation
- **DM Sans** + **JetBrains Mono** from Google Fonts
- Pure inline CSS — no framework, no Tailwind

The production version is built with .NET 8, Blazor Server, Azure Durable Functions, PostgreSQL, and SignalR.

## Run Locally

Just open the file:

```bash
# Clone
git clone https://github.com/yourusername/creatorpulse-demo.git
cd creatorpulse-demo

# Open in browser
open index.html        # macOS
start index.html       # Windows
xdg-open index.html    # Linux
```

No server, no dependencies, no install.

## Deploy to GitHub Pages

1. Push `index.html` to the `main` branch
2. Go to **Settings → Pages**
3. Set source to **Deploy from a branch → main / root**
4. Site goes live at `https://yourusername.github.io/creatorpulse-demo/`

## Cost Model

The real pipeline produces an 8-minute video for roughly **$2.80**:

| Service | Cost |
|---|---|
| Script generation (Claude API) | ~$0.05 |
| Voiceover (ElevenLabs) | ~$2.40 |
| Stock footage (Pexels) | Free |
| AI thumbnails (DALL-E) | ~$0.20 |
| FFmpeg rendering | ~$0.15 |
| **Total per video** | **~$2.80** |

## License

MIT
