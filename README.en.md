<div align="center">

[繁體中文](README.md) · [English](README.en.md) · [日本語](README.ja.md) · [한국어](README.ko.md)

# 🎙️ Speakey

**Hold, speak, release — your words are already typed.**

AI voice input for Mac — use your voice instead of a keyboard in any text field, in any app.
Automatically strips filler words ("um", "uh"), adds punctuation, and can even translate on the fly.

[![Download Latest](https://img.shields.io/badge/Download-Latest%20Release-16818F?style=for-the-badge)](https://github.com/wylopci/speakey/releases/latest)
![macOS](https://img.shields.io/badge/macOS-12%2B-black?style=for-the-badge&logo=apple)
![Notarized](https://img.shields.io/badge/Apple-Notarized-success?style=for-the-badge)

</div>

---

## ✨ Features

- **🎙 Hold to talk**: Hold Right Option and speak. 1–2 seconds after you release it, the text appears right at your cursor — LINE, Email, browser, Notes, anywhere
- **🧹 AI polish**: Not a raw transcript — it's what you *meant* to say. Filler words, stutters, and repetition are cleaned up automatically, with punctuation added
- **🌏 Multi-language**: Chinese (Taiwan) / English / Japanese / Korean, with auto-detection — speak any of them and it types in that language
- **🔁 Live translation**: Speak Chinese, get English out — great for writing English emails or replying to overseas clients
- **🎯 Context-aware tone**: Formal when pasted into Email, casual when pasted into a chat app — it adapts to where you're typing
- **🧠 Gets better with use**: Learns your vocabulary locally on your Mac and suggests frequent terms; a "misheard → correct" rule set permanently fixes stubborn mis-transcriptions
- **🕶 Privacy by design**: No account, no tracking, no company server — usage history lives only on your Mac, and you can turn it off or delete it anytime

## 📥 Download & Install

1. Go to **[Releases](https://github.com/wylopci/speakey/releases/latest)** and download the right build:

   | Your Mac (→ About This Mac) | Download |
   |---|---|
   | Chip: Apple M1 / M2 / M3 / M4 | `Speakey-AppleSilicon.dmg` |
   | Processor: Intel Core i5 / i7 / i9 | `Speakey-Intel.dmg` |

2. **Double-click the `.dmg`**, then drag the Speakey icon into "Applications"
3. Open "Applications" and **double-click to launch** (fully notarized by Apple — no warnings)
4. Follow the on-screen steps: paste in your free Groq API key (the app walks you through getting one) → grant permissions → start talking

Full step-by-step instructions are in the interactive *Install Guide* inside the DMG (available in Traditional Chinese/English/日本語/한국어, auto-switches to your system language).

## 🔑 Cost

**Speakey is completely free.** Speech recognition runs on your own free [Groq](https://console.groq.com) quota, which is more than enough for everyday use — your key, your data, your call.

## 🛡 Privacy & Security

**What goes through the cloud (required for the feature to work)**
- What you say and the recognized text are sent, encrypted, to Groq for speech recognition and AI polishing/translation
- The default models are OpenAI's openly released `whisper-large-v3` (speech recognition) and `gpt-oss-120b`
  (text polishing), both running on Groq's (a US company) servers — **by default, no AI model from any Chinese vendor is used**
- You can switch to other models from the menu (every option is labeled with its developer and country of origin, including selectable models from Chinese vendors); once you switch, your chosen model applies
- Groq's official policy states it does not retain this data or use it for training

**What stays 100% on your Mac and is never uploaded**
- Your Groq API key (stored in your own user directory)
- Usage history, learned frequent terms, custom glossary, correction rules
- Runtime logs

**On the developer's side**
- Speakey has no server of its own — there is no upload logic anywhere in the code
- Data only ever flows between "your Mac" and "the Groq account tied to your own API key" — the developer cannot see or collect any usage content
- The keyboard listener only checks "was the hotkey pressed" — it never records keystroke content; password fields are protected by macOS Secure Input, so voice input inherently cannot enter one by mistake

## 💻 Requirements

- macOS 12 (Monterey) or later; "Launch at login" requires macOS 13+
- Apple Silicon or Intel chip (download the matching build)
- Internet connection required (speech recognition runs in the cloud)

## 🗒 Changelog

### 2.7.0 (2026-07-21)
- **Auto-update added**: Speakey periodically checks GitHub for new versions. When one is found, click "Update Now" to automatically download, verify the signature (notarization + developer identity double-check), install, and relaunch — no more manual DMG downloads. Auto-checking can be turned off in Advanced settings, and you can always trigger "Check for Updates" manually
- Privacy disclosure updated to describe that the update check sends only a version query, no personal data or usage content

### 2.6.1 (2026-07-20)
- Important fix: when dictating imperative sentences ("look this up for me…", "help me compare…"), the AI polish step could mistake the content for instructions addressed to itself and answer instead (e.g., outputting "Sorry, I can't help with that"). Dictation is now always transcribed faithfully, with a new safety fuse that falls back to the raw transcript if the polish output ever looks like an AI reply — strongly recommended for anyone dictating into ChatGPT/Claude or other AI tools

### 2.6.0 (2026-07-20)
- **New "Self-Evolution"**: automatically analyzes your usage history, spots words that keep getting misheard, and proposes correction rules — approve once and they're fixed automatically forever. The more you use it, the more accurate it gets
- **New TAIDE local polishing option**: supports Taiwan NSTC's TAIDE model (runs locally on your Mac via Ollama, so polished text never leaves your computer); full setup guidance included. Speech recognition and translation still use Groq
- Local model resource optimization: capped context length and 3-minute idle auto-unload, preventing memory bloat and heat
- Fix: error when the spoken content was pure digits (e.g., "123")
- Fix: digit-heavy Chinese sentences being misdetected as foreign language and translated into English

### 2.5.1 (2026-07-19)
- Fix: Cmd+V paste (and Cmd+C/X/A/Z) not working in dialog text fields such as the API Key box — right-click was previously the only way

### 2.5.0 (2026-07-19)
- New "Taiwanese Hokkien (Experimental)" recognition mode — speak Taiwanese, and with output language set, get Chinese/English/Japanese/Korean text
- Selectable speech-recognition and polish/translate models, each labeled with developer and country of origin (defaults unchanged)
- New "Condensing Strength" with three levels: Off (fillers only) / Conservative (merge obvious repeats) / Aggressive (boil down to the point)
- Interface language now includes 日本語 and 한국어 (full EULA included), following the system or set manually
- Menu reorganized: API Key, models, condensing, and history grouped under "Advanced" for a cleaner main menu
- Active hint when recording volume is too low, instead of silently skipping

### 2.4.0 (2026-07-18)
- First public release: Apple-signed & notarized DMG for Apple Silicon and Intel (macOS 12+)
- Interactive install guide in four languages (繁體中文/English/日本語/한국어, auto-switching by system language)
- License terms built into the app's "About Speakey" dialog
- More precise privacy disclosure: clear separation of "must go through the cloud" vs. "100% local" data

## 📄 License

Free to use and share as-is; modification-and-redistribution, renaming/reselling, and reverse engineering are prohibited.
Full terms are available in the app's menu bar → "About Speakey" → "License Terms".

© 2026 wppppwpp. All rights reserved.
