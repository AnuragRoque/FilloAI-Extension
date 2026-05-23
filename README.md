# FilloAI-Extension

A Chrome extension that fills any web form automatically using your saved profile and a locally running AI. You fill in your details once, and it handles the rest — whether it's a registration page, a survey, an application, or any other form.
<br>
Checkout: https://fillo-ai-landing-page.pages.dev/

The AI part handles open-ended questions and text fields. Everything runs on your machine via Ollama. Nothing leaves your browser.
<img width="440" height="450" alt="Fillo_AI__main" src="https://github.com/user-attachments/assets/c8044175-43d0-4406-80b0-d8a73bd6f26b" />
<img width="740" height="440" alt="Fillo_AI_custom_fill" src="https://github.com/user-attachments/assets/7ef09a52-19dc-4147-926a-e44585190ec2" />


---

## What it actually does

Most form fillers just paste name and email. This one goes further:

- **NEW: One-Click Resume Upload** — Upload your PDF resume to have the AI instantly extract your profile details, draft a universal cover letter, and pre-generate 20 custom interview Q&As based specifically on your experience.
- Fills all standard fields (name, email, phone, address, salary, work auth, etc.) from your profile instantly
- Detects open-ended text boxes and uses a local AI to write the answer based on your profile
- Lets you pre-write answers to questions you know will come up — and AI-polish them before you need them
- Right-click any field on any page and fill just that one field, at a specific length
- Works on any website with forms — not locked to a specific platform
<img width="950" height="800" alt="Fillo_AI__setting" src="https://github.com/user-attachments/assets/73945826-d36c-464b-add6-8b977eb42f6a" />

<img width="1280" height="589" alt="Fillo_AI_profile" src="https://github.com/user-attachments/assets/23a6fe6e-6546-4928-96c8-dc4481956246" />

---

## How to install

1. Install from Chrome Web Store (coming soon)
2. Contract me for Free Demo

---

## Setting up your profile

Click the extension icon → gear icon → fill in the tabs:

- **Personal** — name, email, phone, date of birth
- **Address** — city, state, zip, country
- **Professional** — current title, company, experience, LinkedIn, GitHub, portfolio, bio
- **Work Auth** — visa type, sponsorship, work eligibility
- **Preferences** — salary, job type, notice period, relocation, remote
- **Documents** — default cover letter and "why this company" answer (optional, for job forms)
- **Custom Q&A** — pre-write answers to questions you know will show up (see below)
- **EEO** — demographic fields (optional)
- **AI Settings** — Ollama URL and model
- **Context Menu** — configure length options for right-click fill

Press **Save Profile** or `Ctrl+S`.

---

## Filling a form

1. Open any page with a form
2. Click the extension icon
3. Hit **Auto Fill** to fill structured fields from your profile
4. Hit **AI Fill (Empty)** to have the AI also handle open-ended text fields
5. Or right-click any individual input → pick the fill style you want

There's also an **Auto-fill on page load** toggle if you want it to run automatically.

---

## Custom Q&A

This is for questions you know will show up repeatedly. Things like:

- "Tell us about yourself"
- "What's your biggest strength?"
- "Describe a challenging project you worked on"

Go to **Custom Q&A** in settings. Add a question, write your own answer or just a rough draft, then pick Short / Long / Detailed and click **AI Enhance**. The AI reads your saved profile and rewrites the answer properly in your voice.

These answers are saved and reused automatically when the extension detects a matching question on a form.

---

## Setting up Ollama

AI features need Ollama running on your machine. If you skip this, structured field filling still works — just no AI-written answers.

**Crucial Step for Chrome Extensions**: By default, Ollama blocks browser extensions. You *must* allow cross-origin requests for the extension to communicate with it.

### Windows
1. Download from [ollama.com](https://ollama.com) OR run `winget install Ollama.Ollama`.
2. Completely quit the Ollama system tray app if it is running.
3. Open Command Prompt or PowerShell and run:
   ```cmd
   set OLLAMA_ORIGINS="*"
   ollama serve
   ```
4. Open a *new* terminal window and download the recommended model: `ollama run gemma3:1b`

### macOS
1. Download from [ollama.com](https://ollama.com) and drag `Ollama.app` to Applications.
2. Completely close the Mac Menu Bar App.
3. Open Terminal and run:
   ```bash
   OLLAMA_ORIGINS="*" ollama serve
   ```
4. Open a *new* terminal window and download the recommended model: `ollama run gemma3:1b`

### Linux
1. Install using the official script: `curl -fsSL https://ollama.com/install.sh | sh`
2. Stop the systemd service, then run manually:
   ```bash
   OLLAMA_ORIGINS="*" ollama serve
   ```
   *(Or permanently add `Environment="OLLAMA_ORIGINS=*"` to your `ollama.service` file)*
3. Open a *new* terminal window and download the recommended model: `ollama run gemma3:1b`

### Final step
Once installed, open the extension **Settings → AI Settings**, click **Test Connection**, and you are good to go!

---

## How it detects fields

The extension scans every input on the page and checks multiple signals — the field's `name`, `id`, `placeholder`, `aria-label`, linked label text, and nearby text in the DOM. It matches these to your profile using keyword patterns.

Handles: text inputs, email, phone, URL, date, number, textarea, select dropdowns, radio buttons.

---

## Works on

It works on any site with standard HTML forms. Some examples:

| Site type | Notes |
|-----------|-------|
| Job portals (LinkedIn, Indeed, Greenhouse, Lever) | Full support |
| Workday | Basic support — shadow DOM makes it harder |
| Registration/signup pages | Standard support |
| Survey and feedback forms | Standard support |
| Any other HTML form | Universal support |

---

## Privacy

Your profile data is stored in `chrome.storage.local` — it never leaves your browser. The only network call the extension makes is to your local Ollama server at localhost. No cloud, no accounts, no tracking.

---
