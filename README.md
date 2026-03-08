# 🤟 Palmly — Real-Time ASL Translator

**Every hand has a voice.**

Palmly is a browser-based, bidirectional ASL (American Sign Language) translator. No app install required — just open a link.

## Features

| Tab | Direction | How it works |
|-----|-----------|--------------|
| 🖐 Text → Sign | Type or speak → 3D Avatar fingerspells | Web Speech API + Three.js hand model |
| 🤟 Sign → Text | Camera → Detected letters → Words | MediaPipe Hands + gesture classifier |
| 📖 ASL Guide | A–Z reference with interactive 3D poses | Three.js per-letter avatar |

## Tech Stack

- **Three.js r128** — 3D hand model with smooth lerp animation
- **MediaPipe Hands** — real-time hand landmark detection
- **Web Speech API** — voice-to-text input
- **Vanilla JS / HTML / CSS** — zero build step, single file

## Responsive

- **Desktop (≥768px):** Large 3D canvas + right sidebar, footer controls
- **Mobile (<768px):** Tab-based layout, inline avatar

## Live Demo

→ [palmly.vercel.app](https://palmly.vercel.app)

## Local Development

```bash
# Clone and serve (HTTPS required for camera + mic)
git clone https://github.com/YOUR_USERNAME/palmly.git
cd palmly
npx serve .
# or
python3 -m http.server 8080
```

> ⚠️ Camera and microphone APIs require **HTTPS**. Use Vercel, Netlify, or `ngrok` for testing on device.

## Deploy

See [DEPLOY.md](DEPLOY.md) for step-by-step GitHub + Vercel deployment.

## File Structure

```
palmly/
├── index.html      ← entire app (single file)
├── README.md
└── DEPLOY.md
```

## Known Limitations

- J and Z are motion signs — static pose shown only
- A/S/M/N/T/E (closed-fist variants) can be hard to distinguish
- Camera requires HTTPS (works on Vercel, not plain `file://`)
