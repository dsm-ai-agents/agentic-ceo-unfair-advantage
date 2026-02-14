# Veo 3.1 → YouTube Auto Publisher (n8n + Gemini)

> Fully automated AI video generation and YouTube publishing system.  
> **User message → Gemini Agent → Optimized Veo Prompt → Video Generation → Status Polling → Download → YouTube Upload**

---

## 1. Problem

Manually crafting video prompts, generating AI videos, downloading files, and uploading to YouTube is slow and repetitive. This workflow converts a simple chat message into a fully generated and published YouTube video — automatically.

---

## 2. System Architecture

```
When Chat Message Received
  → AI Agent (Gemini Chat)
      → Simple Memory
      → Structured Output Parser
  → HTTP: Video Generation Request (Veo 3.1)
  → Wait
  → HTTP: Video Generation Status Check
  → IF (Completed)
      → true:  Download Video → Upload to YouTube / Upload to Drive
      → false: Wait → Re-check Status (loop)
```

The polling loop continues until the video status returns `done: true`.

---

## 3. AI Agent System Prompt

Copy this directly into the **AI Agent** node:

```
You are an expert AI video prompt engineer for Google's Veo 3.1. Transform user requests into optimized video generation prompts within 150 words max.

Essential Elements (Priority Order):
  Subject:     Main focus (person, object, animal, scenery)
  Action:      What's happening (specific verbs)
  Style:       Creative direction (cinematic, sci-fi, cartoon, documentary)
  Camera:      Position (aerial, close-up, eye-level) and motion (dolly, tracking, static, pan)
  Composition: Shot framing (wide shot, medium, close-up)
  Ambiance:    Lighting, color tones, mood, time of day
  Audio:       Dialogue in quotes, sound effects described explicitly, ambient noise

Also generate the title of the video.

Rules:
- Be concise and specific
- Use vivid adjectives efficiently
- Front-load important details
- Combine related elements
- No filler words
- Maximum impact, minimum words

Output only valid JSON in this format:
{
  "title": "title of the video",
  "prompt": "prompt for the video"
}
```

---

## 4. Output Schema

The Structured Output Parser should be configured with the following schema:

```json
{
  "title": "title of the video",
  "prompt": "prompt for the video"
}
```

---

## 5. Veo 3.1 Video Generation

**Endpoint**
```
POST https://generativelanguage.googleapis.com/v1beta/models/veo-3.1:generateVideo
```

**Required inputs:**
- Gemini API Key
- `prompt` — from the AI Agent output
- `title` — from the AI Agent output

The request returns a **job ID** used for status polling.

---

## 6. Status Polling Logic

```
1. Wait 10–20 seconds
2. Check generation status via HTTP request
3. If done = false → Wait again → Re-check
4. If done = true  → Proceed to Download
```

The polling loop is handled by the **Wait → Status Check → IF** node chain.

---

## 7. YouTube Upload

**Requirement:** Enable the **YouTube Data API v3** in Google Cloud Console.

**Authentication:** YouTube uses Google OAuth. The same Google Cloud project used for Gemini can be reused.

**Required OAuth Scope:**
```
https://www.googleapis.com/auth/youtube.upload
```

**Video metadata:**
- **Title** — from AI Agent output
- **Description** — optional (configurable)
- **Visibility** — configurable (`public`, `unlisted`, or `private`)

---

## 8. Required Credentials

| Credential | Description |
|---|---|
| `GEMINI_API_KEY` | For the AI Agent and Veo 3.1 API calls |
| Google OAuth | For YouTube upload and Google Drive |
| YouTube Data API v3 | Must be enabled in Google Cloud Console |

---

## 9. Environment Variables

```env
GEMINI_API_KEY=
GOOGLE_CLIENT_ID=
GOOGLE_CLIENT_SECRET=
```

---

## 10. Setup Instructions

1. Import the workflow JSON into n8n.
2. Configure **Gemini API** credentials in the AI Agent node.
3. Configure **Google OAuth** credentials for YouTube and Drive nodes.
4. Enable **YouTube Data API v3** in your Google Cloud project.
5. Test the workflow with a sample input message.
6. Monitor the polling loop on first run to verify timing.

---

## 11. Sample Input

```
Create a cinematic sci-fi video of a futuristic city at night with flying cars and neon rain.
```

---

## 12. Failure Modes

| Issue | Cause |
|---|---|
| API quota exceeded | Too many generation requests |
| Polling interval too short | Status check fires before video is ready |
| OAuth misconfiguration | Invalid or expired Google credentials |
| Upload timeouts | Large video file or slow network |
| Rate limits | Gemini or YouTube API throttling |

---

## 13. Scalability Notes

This architecture is modular and production-ready. Planned future upgrades include:

- Description generator agent
- Thumbnail generator workflow
- SEO metadata optimizer
- Logging database
- Retry + error handler nodes