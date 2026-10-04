# Fire and Hammer: The Unbroken East

A Hearts of Iron IV alternate-history mod (built for 1.16.x).

**Premise:** Muhammad is never born, so the Arab conquests never happen. Rome and Persia keep
fighting for another thirteen centuries. By 1936 the Middle East is split between two powers:

- **The Roman Proletarian Republic** (plays as `TUR`): the Eastern Roman Empire, overthrown in
  1917 by the Constantinople Soviet. Its capital is Constantinople. It holds Anatolia, Greece,
  the Levant and Egypt.
- **The Saoshyantate of Eranshahr** (plays as `PER`): the surviving Sasanian realm, now a
  Zoroastrian theocracy ruled by a magus who claims to be Astvat-ereta, the last Saoshyant.
  It holds Persia, Mesopotamia, Afghanistan and Arabia.

## Contents

| Feature | Files |
|---|---|
| Rewritten country history (communist Rome, theocratic Eranshahr, leaders, parties) | `history/countries/` |
| Map setup at game start (annexations and transfers of cored states) | `common/on_actions/byzsao_on_actions.txt` |
| A focus tree for each country (15 for Rome, 14 for the Saoshyantate) | `common/national_focus/` |
| 13 national spirits | `common/ideas/byzsao_ideas.txt` |
| A decision category for each side | `common/decisions/` |
| An intro event, a war news event and a flavour event for each side | `events/byzsao_events.txt` |
| Custom flags for every ideology | `gfx/flags/` |

The two focus trees both lead to **The Last War of Antiquity**: Rome's *Last War of Antiquity*
and the Saoshyantate's *Asha Against Druj* each give a war goal against the other.

## Install

1. Copy this folder into `Documents/Paradox Interactive/Hearts of Iron IV/mod/fire_and_hammer/`.
2. Next to it, create `mod/fire_and_hammer.mod` with the contents of `descriptor.mod` plus
   one line: `path="mod/fire_and_hammer"`.
3. Enable the mod in the launcher and start a 1936 game.

## Notes and limitations

- Territory changes run in `on_startup`, so the country selection screen still shows vanilla
  borders. The new map appears once the game starts.
- The mod doesn't override any vanilla state files. Territory moves by annexing whole tags
  (GRE, EGY, SYR, LEB, PAL, JOR → Rome; IRQ, AFG, SAU, YEM, OMA → Saoshyantate) and by
  transferring any state that carries one of those cores.
- Small British-held Gulf territories (Kuwait, Aden, the Trucial coast) and Cyprus stay with
  their vanilla owners.
- Leaders have no custom portraits and use the game's generic ones.
