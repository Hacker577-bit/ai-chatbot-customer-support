# NovaAI - Intelligent Customer Support Chatbot

A premium AI-powered customer support chatbot built with Groq Llama 3.3 70B, featuring natural language understanding, intent recognition, voice input/output, and multi-language support.

## Features

### Core Features
- **Natural Language Understanding** - Powered by Groq Llama 3.3 70B for intelligent response generation
- **Context-Aware Responses** - Full conversation history sent with each API call (12-message sliding window)
- **FAQ Knowledge Base** - 20+ pre-seeded Q&A pairs with fuzzy matching; high-confidence FAQ hits skip the LLM entirely
- **Conversation History** - In-browser localStorage persistence across page reloads with sidebar navigation
- **Intent Recognition** - Client-side classifier maps 9 intent categories (greeting, shipping, refund, billing, account, technical, product, escalation, farewell)
- **Confidence Score** - Composite score from FAQ match strength and intent keyword density, displayed per response

### Upgrade Features
- **Voice Input / Speech-to-Text** - Browser Web Speech API with mic button; auto-sends on voice end
- **Text-to-Speech** - SpeechSynthesis API with selectable voices and adjustable speed
- **Multi-language Support** - 9 languages (EN, ES, FR, DE, AR, ZH, HI, PT, JA); system prompt instructs Groq to respond in selected language; STT/TTS lang code updated dynamically

## Tech Stack

| Layer | Technology |
|-------|-----------|
| UI | Vanilla HTML + CSS (glassmorphism dark theme) |
| LLM | Groq API - Llama 3.3 70B Versatile |
| Voice | Web Speech API (browser-native) |
| Storage | localStorage |
| Hosting | Vercel (serverless) |

## Architecture

```
index.html          - Single-page app (HTML + CSS + JS)
api/chat.js         - Vercel serverless function (Groq proxy)
vercel.json         - Vercel configuration
package.json        - Project metadata
```

## Local Development

```bash
npm install -g vercel
vercel dev
# Open http://localhost:3000
```

## Deployment

This project is automatically deployed to Vercel. The `api/chat.js` serverless function securely proxies requests to the Groq API.

## Models Available

| Model | Use Case |
|-------|----------|
| Llama 3.3 70B Versatile | Best quality (default) |
| Llama 3 8B | Fastest responses |
| Mixtral 8x7B | Balanced quality/speed |
| Gemma 2 9B | Lightweight option |

## Browser Compatibility

- Chrome 33+ (full feature support including STT/TTS)
- Edge 79+ (full feature support)
- Firefox (TTS only, no STT)
- Safari 14.1+ (partial TTS support)
