# Tavern (beta)

Tavern is a Grok Bot template for playing a tabletop RPG in a group chat. An AI **DM** bot runs the game,
a **Cast** bot voices the NPCs and foes, and a **Party** bot plays AI heroes next to the human players.

**Status: BETA.** Expect rough edges.

## Installing
You don't need to install anything by hand. The DM bot sets up the engine itself the first time it
runs (the `tavern-core-bootstrap` skill). It downloads the engine release from this repo's
[Releases](../../releases) and checks its sha256 before installing.

## How releases work
- Each engine version is a GitHub release (`v0.3.4` today) with three files: `tavern-install.py`, `tavern-engine-<v>.tar.gz` and `tavern-guides-<v>.tar.gz`, each tarball with a `.sha256` file next to it.
- The DM bot's `tavern-core-bootstrap` skill pins one installer URL **and its sha256**. A changed file is refused. The installer then checks the engine tarball's sha256, runs a smoke game, and only then switches over.
- Old releases are never deleted or replaced, so bots cloned from an older template keep installing the version they were built for. A new version ships as a new tag plus a template update that pins the new installer.
- Campaign saves are never touched by an install or update.

## Tests
The engine's test suite ships inside the release tarball (`tests/test_engine.py`, 22 tests plus 1 optional regression test). Run it from the unpacked release root: `python3 -m pytest -q tests`. The `engine-tests` workflow does the same against the pinned release.

## License
MIT. See [LICENSE](LICENSE).

## What's new
See [CHANGELOG.md](CHANGELOG.md). Latest: **0.3.4**. The bots stay in the conversation, scenes get room to breathe, and fights end by the rules. A mature-content setting is available per table (off by default).

## Bugs and feedback
Type `report bug` in the game and describe what happened. The DM writes it up.

Made by [@ChefMcMakin](https://x.com/ChefMcMakin).
