# 🎬 Veo 3.1 AI Video Prompt Automation
**n8n Workflow – Chat → Optimized Prompt → Video Generation → Drive + YouTube Upload**

---

## 📌 Overview

This workflow converts a simple chat message into a fully optimized Google Veo 3.1 video prompt, generates the video, then:

- Uploads the generated file to Google Drive
- Publishes the video to YouTube

The AI Agent transforms vague user ideas into high-impact cinematic prompts under 150 words, following strict structure and formatting rules.

---

## 🧠 Architecture

```
When Chat Message Received
        ↓
AI Agent (Gemini Chat Model + Memory + Structured Output Parser)
        ↓
Generate Video (Veo 3.1)
        ↓
 ├── Upload File (Google Drive)
 └── Upload Video (YouTube)
```

---

## 🔧 Node Breakdown

### 1️⃣ Trigger — When Chat Message Received

- Accepts user input
- Example:

```
A tiger walking through neon Tokyo at night
```

---

### 2️⃣ AI Agent

**Model:** Google Gemini Chat  
**Memory:** Simple Memory  
**Output Parser:** Structured Output Parser

#### 🎯 System Prompt

```
You are an expert AI video prompt engineer for Google's Veo 3.1. Transform user requests into optimized video generation prompts within 150 words max.

## Essential Elements (Priority Order):
1. Subject
2. Action
3. Style
4. Camera
5. Composition
6. Ambiance
7. Audio

Also generate the title of the video.

## Rules:
- Be concise and specific
- Use vivid adjectives efficiently
- Front-load important details
- Combine related elements
- No filler words
- Maximum impact, minimum words

Output only the optimized prompt and the title.
```

#### 🧾 Structured Output Parser

Schema:

```json
{
  "title": "title of the video",
  "prompt": "prompt for the video"
}
```

This ensures the output is always machine-readable and directly usable by the Veo node.

---

### 3️⃣ Generate a Video — Google Veo 3.1

- Input: `{{$json.prompt}}`
- Generates the final video file
- Returns binary video output

---

### 4️⃣ Upload File — Google Drive

- Stores the generated video file
- Useful for archiving, repurposing, or editing

---

### 5️⃣ Upload a Video — YouTube

- Publishes directly to YouTube
- Title: `{{$json.title}}`
- Description: Can reuse `{{$json.prompt}}`

---

## 🔑 Required Credentials

- Google Gemini API
- Google Drive OAuth
- YouTube Data API v3
- Veo 3.1 access enabled

---

## 📥 Example Input

**User message:**

```
A futuristic samurai fighting robots in the rain
```

**Agent Output:**

```json
{
  "title": "Neon Ronin: Battle in the Rain",
  "prompt": "A lone cybernetic samurai clashes with towering combat robots in a rain soaked neon alley..."
}
```

---

## 🚀 Why This Workflow Is Powerful

- Converts raw ideas into production-grade prompts
- Enforces cinematic structure automatically
- Maintains strict output formatting
- Fully automated publishing pipeline
- No manual editing required

---

## 🛠 Customization Ideas

- Add thumbnail generation agent
- Auto-generate YouTube description + tags
- Multi-language prompt variant generator
- Batch prompt mode
- Auto-post to Instagram Reels or TikTok
- Add analytics feedback loop for prompt refinement

---

## 🎯 Ideal Use Cases

- Faceless YouTube automation
- Short film prototyping
- Ad creative testing
- AI storytelling pipelines
- Creator economy automation systems

---

## 📦 Final Output Flow

```
Chat Idea → Structured Prompt → Veo Video → Drive Archive → YouTube Live
```

Fully automated. Scalable. Agentic.