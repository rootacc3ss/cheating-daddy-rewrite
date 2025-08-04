<img src="/src/assets/logo.png" alt="uwu" width="200"/>

# Cheating Daddy

> [!NOTE]  
> Use latest MacOS and Windows version, older versions have limited support

> [!NOTE]  
> During testing it wont answer if you ask something, you need to simulate interviewer asking question, which it will answer

A real-time AI assistant that provides contextual help during video calls, interviews, presentations, and meetings using screen capture and audio analysis.

## Features

- **Live AI Assistance**: Real-time help powered by Google Gemini 2.0 Flash Live
- **Screen & Audio Capture**: Analyzes what you see and hear for contextual responses
- **Multiple Profiles**: Interview, Sales Call, Business Meeting, Presentation, Negotiation
- **Transparent Overlay**: Always-on-top window that can be positioned anywhere
- **Click-through Mode**: Make window transparent to clicks when needed
- **Cross-platform**: Works on macOS, Windows, and Linux (kinda, dont use, just for testing rn)
- **Stealth Features**: Doesn't show up on screen recordings or sharing, has protections against content protections and disables screenshots when used.

## Setup

1. **Get a Gemini API Key**: Visit [Google AI Studio](https://aistudio.google.com/apikey)
2. **Install Dependencies**: `npm install`
3. **Run the App**: `npm start`

## Usage

1. Enter your Gemini API key in the main window
2. Choose your profile and language in settings
3. Click "Start Session" to begin
4. Position the window using keyboard shortcuts
5. The AI will provide real-time assistance based on your screen and what interview asks

## Keyboard Shortcuts

- **Window Movement**: `Ctrl/Cmd + Arrow Keys` - Move window
- **Click-through**: `Ctrl/Cmd + M` - Toggle mouse events
- **Close/Back**: `Ctrl/Cmd + \` - Close window or go back
- **Send Message**: `Enter` - Send text to AI

## Audio Capture

- **macOS**: [SystemAudioDump](https://github.com/Mohammed-Yasin-Mulla/Sound) for system audio
- **Windows**: Loopback audio capture
- **Linux**: Microphone input

## Requirements

- Electron-compatible OS (macOS, Windows, Linux)
- Gemini API key
- Screen recording permissions
- Microphone/audio permissions

## what i'm changing (rootacc3ss style)

i hope to add the following features (**and maybe even potentially rewrite in to python, to be honest... watch out for "Clue Daddy", a total rewrite that aims to clone functionality of Cluely and improve upon Cheating Daddy!**):
- fix typos

- add a real "homepage" gui that appears upon open to manage settings, knowledgebase, etc; you'll then launch cheating daddy when you're ready

- add support for claude and chatgpt api; gemini remains best for this due to the context window but others may want access to reasoning models for non time sensitive tasks.

- significantly improve the latency on responses for listening

- pick up your responses from your mic to contextualize responses, not just the other party

- beautify the gui a lot, lot more! typing animation for responses, loading screens, overall gui overhaul

- improve the modes; make an auto-solver for things that are on the screen for non-interview or live meetings (at first, this will simply be a hotkey to quickly send in a screenshot with a "solve all problems displayed on the screen)

- create a "custom mode" mode; prompt cheating daddy with what situation you are needing it for if the modes provided don't suffice -- before launching the gui for cheating daddy, you'll simply prompt

- better context engine; create profiles including custom AI instructions, text, pdfs and documents and select said context when opening a new session; failsafe for lost context is a "resend docs" button

- create "custom command" hotkeys -- i.e. if you're taking a subjective personality test for a job, make a hotkey with the prompt "I am taking a test for a job as an office administrator for an insurance company; answer these questions to the best of your ability in context."

- better conversation log; see all inputs, from your mic, screen, what the other party said AND response from

- ask AI about previous meetings using an enhanced database using the new conversation log

- generate follow up emails, summaries, follow up questions and more

- better stealthing features

- deep research function; generate context for the company you're researching (general or specific questions) not only through google search, but before the meeting with a perplexity api key

- and more!
