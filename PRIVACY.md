# Privacy

## The promise

Jot Local is a personal Apple-Silicon macOS app that processes dictation on
your Mac. It needs no account or API key and sends no dictation audio,
transcripts, settings, or History data to a runtime cloud service.

## Network use

Jot Local downloads or re-downloads the pinned local models only when you
choose that action during onboarding or in Settings. Downloads are verified
before use. Recording, Nemotron transcription, optional S1-mini cleanup,
insertion, History, and retry all run locally and work offline.

Release builds also use Sparkle to check the public GitHub-hosted update feed
and download signed app updates. Automatic checks and downloads can be disabled
from the menu bar. These requests expose ordinary connection information,
including your IP address and the updater's user agent, to GitHub and its
download infrastructure. Sparkle system-profile reporting is disabled. Update
requests do not include dictation audio, transcripts, History, or your Dictionary.

## What stays on this Mac

- Dictation audio and metadata, stored in
  `~/Library/Application Support/Jot Local/recordings/`.
- The History index and transcripts, stored in
  `~/Library/Application Support/Jot Local/history.sqlite` and the recording
  folders.
- Pinned local models, stored in
  `~/Library/Application Support/Jot Local/Models/`.
- Your Dictionary and application settings.

History keeps audio and text available for recovery and retry. In Settings →
Privacy & Storage, you can select audio retention or delete all History. Local
files are protected by FileVault when it is enabled; the app does not add a
separate encryption layer.

## What the app does not collect

- No account, API key, analytics, telemetry, or crash uploader.
- No screenshots, screen capture, window contents, surrounding text, or typed
  text.
- No keystroke logging. The event tap watches only the fixed `fn 🌐 + left ⌃`
  dictation chord and, while a dictation is active, `Esc`, `Space`, and the
  accidental-chord guard.

## Secure input

When a password field is focused, dictation does not start. If secure input
becomes active before insertion, text stays in History and is not inserted or
placed on the clipboard.

## Verify it

- Build and inspect the source with `./scripts/build.sh`.
- Complete the explicit model download, then disable networking and use Jot
  Local normally.
- Inspect the local files listed above or delete them through Privacy & Storage.
