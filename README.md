# CYA Burn Book — V1 prototype

A standalone, mobile-first, installable web app for personal workplace incident documentation. Separate from the proposed Union Assistant. No account, database server, analytics, CDN or paid API is required by this code. ChatGPT is an optional manual handoff; the app does not send records anywhere automatically.

## Free iPhone installation (GitHub Pages)
1. Sign in at https://github.com/ or create a free account.
2. Create a **public** repository named `cya-burn-book` (public code is needed for GitHub Pages on the free plan). Upload the six files in this ZIP to its root, not a nested folder. Never upload your records, recordings, evidence, or backups to the repository.
3. In the repository, open Settings > Pages. Choose Deploy from a branch, then `main` and `/(root)`, and save. GitHub will show the published HTTPS address. The exact address depends on your account.
4. Open the published address in Safari on your iPhone. Share > Add to Home Screen (enable Open as Web App if offered). Launch online once to allow the service worker to cache the app shell.
5. Create a passphrase of at least 12 characters. Test with fictional records first. Export and verify an encrypted backup before trusting the app with any data.

GitHub Pages documentation: https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site

Alternatively, from a computer with Python installed, run `python3 -m http.server 8000` in this folder and open `http://localhost:8000` on that computer. For iPhone recording and offline installation, use an HTTPS host. Opening the HTML directly from iPhone Files is not a supported installation method.

## Features
- Create, edit, search, filter and delete incident records, with incident time and created/modified timestamps.
- Evidence vault: upload originals (15 MB per file), export originals, SHA-256 hashes, link evidence to an incident.
- Voice notes: foreground microphone recording (up to five minutes), playback and export. Browser microphone permissions required; no covert or background recording.
- ChatGPT handoff: review/edit a prompt, copy and paste into ChatGPT, then manually paste results back. Export recordings and attach them to ChatGPT only if your account supports the file type and audio upload. Never send sensitive or identifiable information without authorization. AI transcription and responses are not performed by the app itself.
- Incident timeline and printable reports (device print dialog / save to PDF). Reports list hashes and file names; export original evidence separately.
- AES-256-GCM encrypted vault with PBKDF2-SHA-256 (600,000 iterations), 5-minute inactivity auto-lock, encrypted backup and restore. No password recovery.
- Offline app shell after successful service worker installation; no ongoing hosting fee needed for this static prototype on a suitable free host.

## Privacy and limitations
Prototype, not security-audited or App Store-ready. Encryption at rest does not protect an unlocked vault, compromised device, or maliciously modified hosted code. Back up frequently; browser storage can be cleared or evicted, and moving to a different host creates a separate storage origin. Browser storage differs between Safari and installed apps, so test in the installed app itself. No native Face ID, background recording, verified timestamps, tamper-proof audit trail, sync, automatic transcription, or direct AI integration. All dates are device-reported, records can be edited, and hashes alone do not establish legal admissibility. Explicit exports are not encrypted unless they are the encrypted backup. Keep original files and backup passphrase safely. The entire vault is re-encrypted on each write, so large collections may be slow. Obtain lawful consent before recording conversations, follow workplace policies and do not retain patient information. Not legal advice.

## Validation performed
- JavaScript syntax checks passed for application and service worker.
- Tested actual cryptographic routines in Node Web Crypto: encrypted round trip, wrong passphrase rejection and SHA-256 known-answer test passed.
- Browser end-to-end tests were blocked by the execution environment's navigation policy; UI, real microphone, backups, PDF printing and offline behavior remain to be verified on iPhone. Start with fictional data.

## Future commercial version
A native iOS build would require Swift/SwiftUI or another native wrapper, App Store distribution enrollment, privacy review, robust storage and backup design, independent security testing, native recording and device authentication, and licensing/branding review. No commercial release is included here.
