# YouTube Automation

A modular, provider-based pipeline for producing and publishing YouTube content.

## Pipeline

1. Generate a content brief from a topic.
2. Create a script, title, description, tags, and thumbnail prompt.
3. Generate audio and subtitles from the script.
4. Render a video from local images/video clips.
5. Upload the video through the YouTube Data API.

## Setup

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
cp .env.example .env
```

Optional environment variables:

- `OPENAI_API_KEY`: script and metadata generation
- `ELEVENLABS_API_KEY`: voice synthesis
- `YOUTUBE_CLIENT_SECRETS_FILE`: OAuth client JSON
- `YOUTUBE_TOKEN_FILE`: OAuth token storage

## Usage

```bash
python -m ytautomation.cli generate --topic "Why cats sleep so much"
python -m ytautomation.cli render --brief output/brief.json --audio output/audio.mp3 --output output/video.mp4
python -m ytautomation.cli upload --video output/video.mp4 --brief output/brief.json
```

See `docs/architecture.md` for the provider interfaces and production checklist.
