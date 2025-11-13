# Telegram WebApp Chat v3 — E2E (A) + Server-encrypted (B)

## Summary
This project contains:
- Flask backend with endpoints to register public keys, store messages (A: client-encrypted, B: server-encrypted)
- Server generates a symmetric key for server-side encryption (mode B). Admin endpoint can decrypt messages.
- Frontend uses Web Crypto API; private keys are stored in IndexedDB (as JWK). Public key exported as PEM and registered to server.
- Bot (aiogram) provides a WebApp button to open the UI (set WEBAPP_URL).

## Quick start
1. Create venv and install:
   python -m venv venv
   source venv/bin/activate (macOS/Linux) or venv\\Scripts\\activate (Windows)
   pip install -r requirements.txt
2. Run Flask app:
   python app.py
3. (Optional) Run bot (set BOT_TOKEN and WEBAPP_URL):
   export BOT_TOKEN=...; export WEBAPP_URL=https://your-tunnel-url
   python bot.py

## Notes & limitations
- This demo focuses on showing both modes. E2E messages require recipient public key registered. For simplicity, some UX steps (like exporting existing public PEM) are simplified.
- Private keys are stored in IndexedDB as JWK — export if you need backup.
- Do not use this in production without security review.
