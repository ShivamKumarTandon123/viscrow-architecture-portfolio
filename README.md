# Viscrow — AI-Powered Healthcare Productivity Suite

**Clinicians lose hours juggling patient conversations, notes, and documentation across scattered tools.** This project is a unified solution: speak during the encounter, get real-time transcription, and AI-generated clinical notes—in one desktop app (Aria), with a central API, microservices, and a marketing site (Viscrow Health).

> **Turn voice into structure.** One place to capture, transcribe, and turn conversations into structured notes.

[TypeScript](https://www.typescriptlang.org/)
[React](https://reactjs.org/)
[Electron](https://www.electronjs.org/)
[Node.js](https://nodejs.org/)
[pnpm](https://pnpm.io/)

---

## 🎯 The problem (and what I built to address it)

Clinicians and healthcare providers lose time switching between patient conversations, note-taking, and documentation. Clinical context gets scattered across tools; billing and scribe workflows stay separate. In this project I contributed to a **unified healthcare product**: real-time clinical transcription, AI-generated notes (AI Scribe), optional medical billing messaging on the landing site, and a native desktop app—backed by a modular API and a polished public-facing site (Viscrow Health).

---

## 📦 What this portfolio repo contains


| Component            | Description                                                                                                                                    |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| **Aria**             | Cross-platform desktop app (macOS, Windows, Linux) — the primary **AI Scribe** for clinical capture, live and prerecorded transcription, and smart notes (patient/encounter-oriented). |
| **Monolith backend** | Central API: auth, sessions, templates, subscriptions, payments, and AI/voice orchestration.                                                   |
| **Microservices**    | userService, deepgramProxy, assemblyAIProxy, inference, subscriptionService, analyticsService, noteTemplatesService, settingsService.          |
| **Landing site**     | Marketing site: home, about, AI Scribe product, solutions, pricing, ROI calculator, medical billing solutions, contact, privacy, terms, usage policy. |
| **Demo / tooling**   | GitHub Actions and minimal demo assets.                                                                                                        |


---

## ✨ Key features (what the product does)

**Desktop app (Aria) — AI Scribe for healthcare**  

- **Sessions** — Create, list, search, and manage recording sessions (e.g. patient encounters); view transcript and AI-generated clinical notes.  
- **Live & prerecorded transcription** — Real-time streaming and upload-based transcription with editable transcripts.  
- **AI notes** — Generate and regenerate structured notes from session content; rich editing (TipTap).  
- **Templates** — Customizable note templates; optional **patient/encounter metadata** (name, DOB, additional notes).  
- **Auth & account** — Sign up, login, 2FA, email verification, password reset; user settings and theme (light/dark).  
- **Subscriptions** — Free tier with session limits; paid upgrade via Stripe.  
- **Packaging** — Installers: macOS (DMG), Windows (NSIS), Linux (AppImage).

**Landing site (Viscrow Health)**  

- **Healthcare positioning** — AI Scribe product, solutions (“Transforming Healthcare Documentation Through AI”), medical billing solutions, ROI calculator.  
- Product and pricing pages, about, contact; privacy, terms, and usage policy; security and compliance-oriented content.  
- Animated hero, stats, testimonials, roadmap; responsive layout.

---

## 🔐 Login and what we show

**Logging in**  
The desktop app uses email/password with optional two-factor authentication. New users can sign up; flows for email verification, forgot password, and reset password are included. Unauthenticated users are redirected to login; once authenticated, they reach the main app.

**After login**  

- **Sidebar** — Navigation: **Home**, **Sessions**, **Templates**, **Settings**, plus Help and (for free-tier users) upgrade/payment.
- **Home** — Greeting with the user’s name; remaining session count for free tier; **New Session** button; and either **Latest Sessions** (cards linking to each session) or an empty state with a prompt to create the first session.
- **Sessions** — Full list and search; each session opens to transcript, AI-generated notes, patient/encounter fields, and recording or upload.
- **Templates** — Manage note templates used when generating session notes.
- **Settings** — User profile, theme (light/dark), and app preferences.

So after login we show a personalized home, quick access to recent sessions, and clear paths to create a session, view all sessions, edit templates, and change settings.

---

## 🖼️ How it works (portfolio showcase)

<!-- Screenshots and GIFs below illustrate the flow I designed and built. Add your own files to docs/screenshots/ or replace the placeholder paths. -->


| Step                         | What to show                                                                   |
| ---------------------------- | ------------------------------------------------------------------------------ |
| **1. Login**                 | Login screen (email/password, or sign-up).                                     |
| **2. Home**                  | After login: greeting, “New Session” button, latest sessions (or empty state). |
| **3. New session**           | Session page with record/upload; optional patient name or date.                |
| **4. Live transcription**    | Real-time transcript appearing while speaking.                                 |
| **5. Transcript & AI notes** | Transcript + AI-generated notes; edit/regenerate.                              |
| **6. Templates or Settings** | Templates list or Settings (profile, theme).                                   |


<!--**Media placeholders** — Replace each placeholder with your own screenshot or GIF. Use the `![](...)` markdown and point to your file (e.g. in `docs/screenshots/`).-->

---

### 1. Login

**[Insert screenshot: Login or sign-up screen here]**
![Login screen](docs/screenshots/01-login.jpg)

### 2. Home after login

**[Insert screenshot or GIF: Home screen with greeting, “New Session” button, and latest sessions here]**
![Home](docs/screenshots/02-home.png)

### 3. Session — recording or upload

**[Insert screenshot or GIF: Session page with record/upload or active recording here]**
![Session](docs/screenshots/03-session.png)

### 4. Live transcription

**[Insert GIF: Live transcription appearing in real time as you speak here]**
![Live transcription](docs/screenshots/04-live-transcription.png)

### 5. Transcript & AI notes

**[Insert screenshot: Transcript and AI-generated notes view (with edit/regenerate) here]**
![Transcript and notes](docs/screenshots/05-transcript-notes.png)

### 6. Templates or Settings

**[Insert screenshot: Templates list or Settings page (profile, theme) here]**
![Templates or Settings](docs/screenshots/06-templates-or-settings.png)

<!--*Add your files to `docs/screenshots/` and use the same names above, or edit the paths in the `![](...)` markdown.*-->

---

## 🎨 Product & UI (hero & landing)

<!-- Optional: single hero image for the top of the README or project page -->
**[Insert: Hero screenshot or GIF of Aria — home with “New Session” and latest sessions]**
![Aria home](docs/screenshots/hero-aria-home.png)

**[Insert: GIF of live transcription or AI note generation in a session]**
![Live transcription demo](docs/screenshots/demo-live-transcription.gif)

**[Insert: Screenshot of the landing site — above-the-fold]**
![Landing page](docs/screenshots/landing-hero.png)

---


## 🏗️ High-level architecture (system I worked with)

```
                    ┌─────────────────────────────────────┐
                    │              End users               │
                    └─────────────────┬───────────────────┘
                                      │
          ┌───────────────────────────┼───────────────────────────┐
          ▼                           ▼                           ▼
┌───────────────────┐     ┌───────────────────┐     ┌───────────────────┐
│  Aria (Electron   │     │  Landing site      │     │  Other / future   │
│  + React + Vite)  │     │  (React + Vite)    │     │  clients          │
└─────────┬─────────┘     └─────────┬─────────┘     └─────────┬─────────┘
          │                          │                         │
          └──────────────────────────┼─────────────────────────┘
                                     ▼
                         ┌───────────────────────┐
                         │  Monolith API         │
                         │  (Express + TypeScript)│
                         └───────────┬───────────┘
                                     │
          ┌──────────────────────────┼──────────────────────────┐
          ▼                          ▼                          ▼
┌───────────────────┐     ┌───────────────────┐     ┌───────────────────┐
│  Microservices    │     │  AI & voice        │     │  Data & payments   │
│  user, inference, │     │  OpenAI, Deepgram, │     │  MongoDB, Stripe,  │
│  deepgram proxy,  │     │  ElevenLabs,       │     │  DynamoDB          │
│  assemblyAI proxy,│     │  LangChain,        │     │                    │
│  subscription,    │     │  AssemblyAI        │     │                    │
│  analytics,       │     │                    │     │                    │
│  note templates,  │     │                    │     │                    │
│  settings         │     │                    │     │                    │
└───────────────────┘     └───────────────────┘     └───────────────────┘
```

---

## 💻 Tech stack (what I used)


| Layer             | Technologies                                                                                                                                                                                                                                                                 |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Desktop app**   | Electron, React 18, Vite, Redux Toolkit, MUI, TipTap, Socket.io client, Luxon, notistack, react-hook-form, jwt-decode, react-markdown, remark-gfm, Emotion                                                                                                                    |
| **Landing**       | React, Vite, MUI, Framer Motion, Chart.js, react-chartjs-2, React Router, tsparticles, react-countup, react-intersection-observer, Redux Toolkit                                                                                                                          |
| **Monolith API**  | TypeScript, Express, LangChain, OpenAI, MongoDB, Socket.io, Stripe, Deepgram, ElevenLabs, AWS SDK (DynamoDB), Zod, bcryptjs, nodemailer, multer, jsonwebtoken, date-fns, uuid                                                                                                                                 |
| **Microservices** | **Node.js:** userService, deepgramProxy, assemblyAIProxy, subscriptionService, analyticsService, noteTemplatesService, settingsService — Express, Mongoose, Stripe, Deepgram SDK, AssemblyAI, Axios, express-validator, multer, ffmpeg. **Python (inference):** Flask, Flask-CORS, Flask-PyMongo, LangChain, OpenAI, PyMongo, PyJWT, Gunicorn, Pydantic. **Tooling:** Docker |
| **Tooling**       | pnpm, TypeScript, ESLint, GitHub Actions                                                                                                                                                                                                                                                                     |


**Tech stack badges**

*Desktop & landing:*  
![Electron](https://img.shields.io/badge/Electron-47848F?style=for-the-badge&logo=electron&logoColor=white) ![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black) ![Vite](https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white) ![Redux](https://img.shields.io/badge/Redux-764ABC?style=for-the-badge&logo=redux&logoColor=white) ![MUI](https://img.shields.io/badge/MUI-007FFF?style=for-the-badge&logo=mui&logoColor=white) ![TipTap](https://img.shields.io/badge/TipTap-000000?style=for-the-badge&logo=tiptap&logoColor=white) ![Socket.io](https://img.shields.io/badge/Socket.io-010101?style=for-the-badge&logo=socket.io&logoColor=white) ![Luxon](https://img.shields.io/badge/Luxon-000000?style=for-the-badge&logo=luxon&logoColor=white) ![Framer Motion](https://img.shields.io/badge/Framer_Motion-0055FF?style=for-the-badge&logo=framer&logoColor=white) ![Chart.js](https://img.shields.io/badge/Chart.js-FF6384?style=for-the-badge&logo=chartdotjs&logoColor=white) ![React Router](https://img.shields.io/badge/React_Router-CA4245?style=for-the-badge&logo=reactrouter&logoColor=white)

*Backend & API:*  
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white) ![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white) ![Express](https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white) ![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=for-the-badge&logo=langchain&logoColor=white) ![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white) ![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white) ![Stripe](https://img.shields.io/badge/Stripe-008CDD?style=for-the-badge&logo=stripe&logoColor=white) ![Deepgram](https://img.shields.io/badge/Deepgram-0A0A0A?style=for-the-badge&logo=deepgram&logoColor=white) ![ElevenLabs](https://img.shields.io/badge/ElevenLabs-000000?style=for-the-badge&logo=elevenlabs&logoColor=white) ![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonaws&logoColor=white) ![Zod](https://img.shields.io/badge/Zod-3E67B1?style=for-the-badge&logo=zod&logoColor=white)

*Microservices & tooling:*  
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white) ![Flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white) ![Mongoose](https://img.shields.io/badge/Mongoose-880000?style=for-the-badge&logo=mongodb&logoColor=white) ![AssemblyAI](https://img.shields.io/badge/AssemblyAI-000000?style=for-the-badge&logo=assemblyai&logoColor=white) ![Axios](https://img.shields.io/badge/Axios-5A29E4?style=for-the-badge&logo=axios&logoColor=white) ![Gunicorn](https://img.shields.io/badge/Gunicorn-499848?style=for-the-badge&logo=gunicorn&logoColor=white) ![Pydantic](https://img.shields.io/badge/Pydantic-E92063?style=for-the-badge&logo=pydantic&logoColor=white) ![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white) ![pnpm](https://img.shields.io/badge/pnpm-F69220?style=for-the-badge&logo=pnpm&logoColor=white) ![ESLint](https://img.shields.io/badge/ESLint-4B32C3?style=for-the-badge&logo=eslint&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)

---

## 🚀 Getting started 

<!--<!-- Instructions below assume you're running from the same repo layout as in this portfolio. -->

### Prerequisites

- **Node.js** (LTS recommended)
- **pnpm** — [Install pnpm](https://pnpm.io/installation)
- **MongoDB** (for monolith and selected microservices)
- **Docker** (optional; for running microservices via Docker Compose)

---

### 1. Monolith backend

From the repo root:

```bash
cd monolith-backend-main-2
pnpm i
pnpm run dev
```

<!-- Server runs by default on the port set in your env (e.g. 5000). Ensure MongoDB is available if the monolith uses it. -->

---

### 2. Microservices (required for full Aria flow)

Aria expects these services: **userService**, **deepgramProxy**, **inference**. Run them via Docker Compose from `microservices-main-2/`.

**One-time setup:** Generate and set up security keys for the user service (see `microservices-main-2/userService/ReadMe.md` for key generation).

Create `microservices-main-2/docker-compose.yaml` with your own values (do not commit real secrets):

```yaml
services:
  user_service:
    build: ./userService
    container_name: user_c
    ports:
      - "8000:8000"
    environment:
      - NODE_ENV=development
      - MONGODB_URI=mongodb://mongodb:27017
      - EMAIL=<your-gmail-for-verification>
      - APP_PASSWORD=<your-gmail-app-password>
      - VERIFICATION_TOKEN_SECRET=<your-secret>
      - CLIENT_URL=http://localhost:3000

  deepgram_proxy:
    build: ./deepgramProxy
    container_name: deepgram_c
    ports:
      - "3001:3001"
    environment:
      - NODE_ENV=development
      - MONGODB_URI=mongodb://mongodb:27017
      - DEEPGRAM_API_KEY=<your-deepgram-api-key>

  inference:
    build: ./inference
    container_name: inference_c
    ports:
      - "8080:8080"
    environment:
      - SECRET_KEY=<your-inference-secret>
      - OPENROUTER_API_KEY=<your-openrouter-api-key>
      - FLASK_ENV=development

  mongodb:
    image: mongo
    container_name: mongodb_c
    ports:
      - "27017:27017"
    volumes:
      - mongodb_data:/data/db

volumes:
  mongodb_data:
```

Then start all services:

```bash
cd microservices-main-2
docker-compose up
```

**Running services individually (without Docker)**

If you prefer not to use Docker, run each service from `microservices-main-2/` as follows.

**1. User Service** (`microservices-main-2/userService/`)

- **Generate keys (one-time):** From `userService/`, create a `certs/` folder and run:
  ```bash
  openssl genrsa -out certs/accessTokenPrivate.key 2048
  openssl rsa -pubout -in certs/accessTokenPrivate.key -out certs/accessTokenPublic.key
  openssl genrsa -out certs/refreshTokenPrivate.key 2048
  openssl rsa -pubout -in certs/refreshTokenPrivate.key -out certs/refreshTokenPublic.key
  ```
  Copy `accessTokenPrivate.key` into the `certs/` folder of every other service that needs it (e.g. deepgramProxy, inference).
- **Environment variables** (e.g. in `.env`):
  ```
  NODE_ENV=development
  PORT=<optional, e.g. 8000>
  MONGODB_URI=<your-mongodb-uri>
  EMAIL=<your-no-reply-gmail>
  APP_PASSWORD=<gmail-app-password>
  VERIFICATION_TOKEN_SECRET=<use-password-generator>
  CLIENT_URL=http://localhost:3000
  ```
- **Run:**
  ```bash
  cd microservices-main-2/userService
  pnpm i
  pnpm run dev
  ```

**2. Inference** (`microservices-main-2/inference/`)

- Put the **access token public key** from the user service in this service’s `certs/` folder.
- **Environment variables:**
  ```
  PORT=8080
  SECRET_KEY=<use-password-generator>
  OPENROUTER_API_KEY=<your-openrouter-api-key>
  FLASK_ENV=development
  ```
- **Run (Python):**
  ```bash
  cd microservices-main-2/inference
  python -m venv .venv
  .venv/Scripts/activate          # Windows; on macOS/Linux use: source .venv/bin/activate
  pip install -r requirements.txt
  python run.py
  ```

**3. Deepgram Proxy** (`microservices-main-2/deepgramProxy/`)

- Put the **access token public key** from the user service (e.g. `accessTokenPublic.key`) in this service’s `certs/` folder.
- **Environment variables:**
  ```
  NODE_ENV=development
  DEEPGRAM_API_KEY=<your-deepgram-api-key>
  MONGODB_URI=<your-mongodb-uri>
  ```
- **Run:**
  ```bash
  cd microservices-main-2/deepgramProxy
  pnpm i
  pnpm run dev
  ```

---

### 3. Aria (desktop app)

**Required:** Monolith and microservices (userService, deepgramProxy, inference) must be running first.

Create a `.env` (or `.env.local`) in `Aria-main/` with the base URLs of your running services:

```bash
# Auth (userService)
VITE_AUTH_URL=http://localhost:8000

# Transcription (deepgramProxy)
VITE_TRANSCRIPTION_URL=http://localhost:3001

# Notes / inference
VITE_NOTES_URL=http://localhost:8080
```

Adjust host/port if your services run elsewhere. Then install and run:

```bash
cd Aria-main
pnpm install
pnpm run dev
```

---

### 4. Landing site

From the repo root:

```bash
cd landing-site-main-3
pnpm i
pnpm run dev
```

---


---

## 📁 Repository structure

| Folder | Purpose |
| ------ | ------- |
| `Aria-main/` | Desktop app (Viscrow Scribe) — run and build from here. |
| `monolith-backend-main-2/` | Main backend server. |
| `microservices-main-2/` | Microservices: userService, deepgramProxy, inference, assemblyAIProxy, subscriptionService, analyticsService, noteTemplatesService, settingsService. |
| `landing-site-main-3/` | Public marketing/landing site. |
| `demo-repository-main/` | Demo assets and GitHub Actions workflows. |

---

## 🙏 About this portfolio
This repo is my **personal portfolio** for the Viscrow app: a full-stack showcase covering the desktop app (Aria), API design, microservices, and the product-facing web experience. Built to demonstrate my work on a real healthcare productivity product.
