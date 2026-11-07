# Development status — 7 November 2026

H1Z1EU remains a local development project. There is no public server or downloadable production release yet.

## Latest work

- Saved dressing-room outfits are applied when a character joins and after respawn. Nearby players receive the appearance too. Cosmetics leave the character's actual equipment and protection unchanged.
- Fixed an edge case in login fall-damage protection: a deck that arrives near the loading timeout keeps its remaining collision-settling period. Protection expires afterwards; ordinary falls still cause damage.
- The local operations dashboard now reads actual Codex sessions and model usage. It runs as a normal local program and consumes no AI tokens itself.
- Client-bot failures now stop instead of repeatedly relaunching the game and opening login-error pages. A local server check runs before launch, and default endpoints stay on the bot's own server.
- Fixed the real client's local login failure by aligning the client, server and probe on the same interface assigned to the PC. The copied client gets temporary local connection settings with browser-error redirects disabled; original settings are restored afterwards.

## Verification

Local checks on 7 November passed all 408 server-plugin tests and all 21 dashboard tests. The targeted outfit and original deck-login checks passed all 23 Node checks; the updated deck-login scenario then passed all 10 Node checks, including the late-arriving deck. Each bot run also confirmed that the creator's separate H1Emu saves were untouched.

The fresh full bot run on 7 November passed **736/736 recorded checks with zero failures or skips**, in about 30 minutes. That report contains 727 individual tests, 8 suite containers and the separate real-save isolation check. The test server still accepted a protocol login after the run.

This is local development verification, not a production deployment. An earlier strict outfit packet-decoding assertion is no longer present; the green result does not establish that the underlying unknown packet decodes were fixed. That gap remains for separate investigation.

Six launch/window checks, five client-configuration checks and six relay checks passed without starting the game. The real client has also passed login, server selection and world entry. A deck logout/relogin passed in game with 37 collision reports and no lost inventory or position. VPN and tunnel settings were unchanged.

The normal-fall control also passed: a 10 metre fall after login grace reduced health from 10000 to 7393, with the character still alive. This verifies that the deck-login protection does not prevent ordinary fall damage.

After the interface change, the gateway/patch and deck-login protocol regressions passed all 37 Node checks, followed by the real-save isolation check.

GitHub Actions jobs are currently prevented from starting by an account billing or spending-limit restriction. Local checks are recorded separately; no successful hosted CI run is claimed.

## Next

- Keep real-client checks repeatable and extend gameplay coverage.
- Investigate the packet-decoding coverage gap and reconcile remaining progress evidence.
- Continue launch preparation, permissions, source-publication checks and private-beta setup.

This public repository contains reviewed project documentation and screenshots. Private implementation files, game files, credentials and runtime logs are not included.
