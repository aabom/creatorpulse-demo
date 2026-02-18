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

## Why CreatorPulse?

### The Problem

Running a faceless YouTube channel today means juggling 5–8 separate tools: ChatGPT for scripts, ElevenLabs for voiceover, Pexels for footage, Canva for thumbnails, CapCut for editing, TubeBuddy for SEO. Each tool has its own subscription, its own learning curve, and its own export-import dance. A single 8-minute video takes 4–6 hours of manual work across all of them.

### The Solution

CreatorPulse replaces the entire toolchain with one subscription. You type a prompt, approve each step, and get a published video on your channel. No API keys to manage, no accounts to juggle, no files to shuttle between apps. We handle all the AI services behind the scenes — you just focus on your content ideas.

### What Sets Us Apart

**You stay in control.** Unlike fully automated generators that spit out cookie-cutter content, CreatorPulse gives you an approval gate at every step. Edit the script, swap a voice, change a visual — then move forward. It's AI-assisted, not AI-replaced.

**Built for long-form.** Most competitors focus on 60-second Shorts. CreatorPulse is designed for the 8–15 minute faceless videos that actually build audiences and qualify for full ad monetization.

**Audience intelligence built in.** Connect your YouTube channel and CreatorPulse scans your analytics — demographics, watch patterns, peak hours, top-performing topics — to tailor every script and thumbnail to *your* audience, not a generic template.

**A/B testing from day one.** Every video ships with two thumbnail variants. YouTube's Test & Compare feature picks the winner automatically. Over time, the system learns what visual styles drive clicks for your specific niche.

**Self-improving feedback loop.** After publishing, CreatorPulse tracks performance for 7 days and feeds the results back into future generations. Your 10th video is smarter than your 1st.

### How It Works for the Customer

1. **Subscribe** — pick a plan (Starter, Creator, Pro, or Agency)
2. **Connect YouTube** — one-time Google OAuth login to link your channel
3. **Create** — type a prompt, approve each pipeline step
4. **Publish** — video goes live on your channel with full metadata and A/B thumbnails
5. **Grow** — performance tracking feeds insights into your next video

No API keys. No separate subscriptions. No technical setup.

### 🔧 Backend

| | What | Why |
|---|---|---|
| ⚙️ | **.NET 8 / C#** | Strongly typed, first-class Azure integration, and the entire team works in one language across API, pipeline, and frontend |
| 🌐 | **ASP.NET Core Web API** | REST endpoints with built-in DI, middleware pipeline, and auto-generated Swagger docs |
| 🖥️ | **Blazor Server** | Fullstack C# — no separate JavaScript framework. Server-side rendering with real-time UI updates over SignalR |
| 📡 | **SignalR** | Pushes pipeline status changes live to the browser. Steps go from Pending → Running → Completed without polling or page refresh |
| ⛓️ | **Azure Durable Functions** | The orchestration engine. Chains all 8 pipeline steps and natively supports `WaitForExternalEvent` — the pipeline literally pauses until the user approves, with zero custom queue infrastructure |
| 🗃️ | **Entity Framework Core** | ORM with LINQ queries, migrations, and strongly typed models against PostgreSQL |

### 💾 Database & Storage

| | What | Why |
|---|---|---|
| 🐘 | **PostgreSQL 16** | JSONB columns for flexible data (script sections, SEO metadata, audience profiles) at a fraction of the cost of SQL Server. Runs locally via Docker, Azure Flexible Server in production |
| ☁️ | **Azure Blob Storage** | Stores all generated media — voiceover MP3s, video segments, thumbnails, final MP4. Pay-per-GB pricing scales with actual usage |
| 🧊 | **Azurite** | Local Blob Storage emulator. Full Azure Storage API compatibility without touching a cloud account during development |
| 🐳 | **Docker** | PostgreSQL and Azurite run in containers. No installers, no PATH config. `docker rm -f` to nuke everything and start fresh |

### 🤖 AI & External Services

| | Service | Role |
|---|---|---|
| 🧠 | **Claude API** (Anthropic) | Script generation and SEO metadata. Best-in-class for long, structured text with specific tone and formatting requirements |
| 🎙️ | **ElevenLabs** | Neural voiceover with emotion control and multiple voice profiles. Natural-sounding narration without hiring voice actors |
| 🎨 | **DALL-E** (OpenAI) | Thumbnail generation and AI B-roll images. Simple API, $0.04/image |
| 🎬 | **Pexels API** | Stock video matched to script sections. No rate limits, no cost |
| 🔧 | **FFmpeg** | Video assembly — stitches voiceover, video segments, burned-in subtitles, and background music into final MP4. Industry standard, programmable via CLI |
| 📺 | **YouTube Data API v3** | Publishing, metadata upload, and A/B thumbnail testing via OAuth against the creator's own channel |
