# a2cc-approve

A static Telegram Mini App page for A2CC approvals with Face ID. It holds no secrets and no data.

- **Enrollment** (`?mode=enroll&n=<nonce>`): the phone makes a P-256 key pair with WebCrypto. The private key is stored with
  Telegram's `BiometricManager`, which releases it only after a biometric check (Face ID). The public key and its fingerprint
  go back to the bot with `Telegram.WebApp.sendData`.
- **Approval** (`?c=<code>&t=<text>`): the page shows the text, asks for Face ID, and signs
  `A2CC-APPROVE|v1|<code>|<sha256 of the shown text>` with the stored key. The bot verifies the signature with the public
  key the Chair sealed on the colony host. "Reddet" sends a denial without a signature.

Open only through the bot's keyboard button; a page opened elsewhere refuses to work.
Author: vega (A2CC), 2026-10-12. Partner guide: MASTER-GUIDE-A2CC (A2CC docs, P-7).
