# Secret Redactor

A lightweight, 100% local tool for redacting secrets before sharing text with AI.

## Usage

Just open `index.html` in a browser. Bookmark it for quick access.

## Features

- **Paste** → **Preview** → **Copy Redacted**
- Highlights detected secrets with confidence levels:
  - 🔴 High confidence (known API key formats, private keys, etc.)
  - 🟡 Likely secret (password patterns, auth headers)
  - 🔵 Possible (high-entropy strings, internal IPs)
- All processing happens locally — nothing sent anywhere
- Toggle detection categories on/off

## Detection Patterns

### High Confidence
- API keys: `sk-ant-*`, `sk-*`, `ghp_*`, `AKIA*`, `xox*-*`, `VENICE_*`
- Private keys: PEM format, 64-char hex (ETH private keys)
- Tokens: JWT, Bearer, Discord, Telegram bot tokens
- URLs with embedded credentials
- Database connection strings

### Medium Confidence  
- Password/secret assignments: `password=`, `secret:`, `api_key=`
- Auth headers

### Entropy Detection
- Random-looking strings with high Shannon entropy (> 4.5 bits)
- Catches tokens/keys without known prefixes

## Customization

Toggle categories in the Settings panel. Patterns are defined in the `patterns` object in the HTML file.

## Privacy

Zero network requests. Everything stays in your browser. Check the source — it's a single HTML file.
