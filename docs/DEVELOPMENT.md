# Development status — 7 November 2026

H1Z1EU remains a local development project. There is no public server or downloadable production release yet.

## Latest work

- Saved dressing-room outfits are applied when a character joins and after respawn. Nearby players receive the appearance too. Cosmetics leave the character's actual equipment and protection unchanged.
- Fixed an edge case in login fall-damage protection: a deck that arrives near the loading timeout keeps its remaining collision-settling period. Protection expires afterwards; ordinary falls still cause damage.
- The local operations dashboard now reads actual Codex sessions and model usage. It runs as a normal local program and consumes no AI tokens itself.
- Client-bot failures now stop instead of repeatedly relaunching the game and opening login-error pages. A local server check runs before launch, and default endpoints stay on the bot's own server.

## Verification

Local checks on 7 November passed all 408 server-plugin tests and all 21 dashboard tests. The targeted outfit and original deck-login checks passed all 23 Node checks; the updated deck-login scenario then passed all 10 Node checks, including the late-arriving deck. Each bot run also confirmed that the creator's separate H1Emu saves were untouched.

These are targeted local results, not a claim that a fresh full suite or a production deployment passed. The last recorded full suite had 733 passing checks out of 735; both failures belonged to the outfit packet-decoding assertion. The current targeted outfit test passes, but it no longer makes that decoding assertion, so the older full-suite result is not a clean bill of health for packet decoding.

Four launch-guard checks and six relay checks also passed without starting the game. The bot server accepted a real protocol login, but the real client returned a login error and was stopped. The revised numeric-IP launch path remains unverified in the real game.

GitHub Actions jobs are currently prevented from starting by an account billing or spending-limit restriction. Local checks are recorded separately; no successful hosted CI run is claimed.

## Next

- Finish real-client verification of deck logins and normal fall damage.
- Re-run the full bot suite after the latest changes and investigate remaining failures.
- Continue launch preparation, permissions, source-publication checks and private-beta setup.

This public repository contains reviewed project documentation and screenshots. Private implementation files, game files, credentials and runtime logs are not included.
