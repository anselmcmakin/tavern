# Tavern changelog

## 0.3.4 (2026-10-17)
Table fixes from real play: the Party and Cast bots stopped being cued, scenes rushed, and fights ended by fiat.

**Engine**
- Bot seats are guarded: if a character belongs to the Party or Cast bot, the DM can't act for it without a cue
  and the bot's proposal. After a missed cue, the DM can cover it with `--cue <n> --cover "<why>"`, which is logged.
  Tables without bots are unchanged.
- `status` shows warnings for stale cues (a proposal left open, or an open cue from an earlier scene) and for
  cue drift (several beats with no cue while bots hold characters; set the threshold with `settings set cue_drift_beats <n>`).
- `beat open` is logged, so beats can be counted.
- `roll` needs `--reason`, and when the DM rolls, `--actor <id|world>`. `damage` and `heal` need `--source`.
- `combat next` warns about an empty turn (a living actor that took no action).
- Fights end by the rules. `kill` refuses a standing foe mid-fight unless a successful `--ruling <id>` backs it.
  New `morale <foe> --reason ... [--break flee|yield]` rolls a foe's nerve. `combat end` warns while foes still stand.
- Briefs carry each character's `want` and `fear`. Its `secret` goes only to its own seat.
- New test suite: `python3 -m unittest discover -s tests -v`.

**DM, Party and Cast guides**
- AI heroes always act through the Party bot and named NPCs through the Cast bot, at solo and multiplayer tables alike.
  An NPC who speaks twice becomes a Cast character with a want, a fear and a secret.
- Scene-setting beats (5–8 sentences: place, senses, someone doing something, history, stakes) at every new place, scene,
  time jump or major NPC. "Let it breathe" after big moments. "Yes, and" for player ideas. At most 1 beat in 3 ends with "what do you do?".
  Numbered choices only in fights and at clear forks. One scene per place or day.
- An open proposal must be resolved at the DM's next post. Cue drift must be fixed on the next beat.
- Private notes and letters stay with the characters who know them.
- New per-table **mature content** setting, **OFF by default**. Turning it on allows darker content.
  At every setting, sex fades to black, and `pause`, X-card, lines and veils always apply. The Party and Cast playbooks follow the same limits.

## 0.3.3 (2026-10-08)
- Previous public release.
