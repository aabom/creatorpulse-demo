# ⚡ CreatorPulse — Prompt to Publish

Interactive demo of the CreatorPulse video generation pipeline. Type a prompt, walk through each production step, and publish to YouTube — all from one interface.

**[Live Demo →](https://aabom.github.io/creatorpulse-demo/)**

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

The production version is built with .NET 8, Blazor Server, Azure Durable Functions, PostgreSQL, and SignalR.

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
