# Fire and Hammer: The Unbroken East

A Hearts of Iron IV total alternate-history world mod (built for 1.16.x).

**Premise:** Muhammad is never born. There is no Islam and no Arab conquests, and fourteen centuries of
consequences follow. Rome and Persia both survive. Charlemagne never happens. The Baltic pagans keep their
gods. The Norse stay in Vinland, the Inca and Mexica survive contact, and Aksum, Wagadu, Majapahit and
Vijayanagara never fall.

By 1936 the world is ready to split:

- **The Roman Proletarian Republic:** the Eastern Roman Empire, turned communist by the 1917 Constantinople
  Soviet. It rules from Sicily to the Nile and leads the **Red Ecumene**.
- **The Saoshyantate of Eranshahr:** the surviving Sasanian realm, now a Zoroastrian theocracy under a
  self-proclaimed messiah. It leads the **Concord of the Sacred Fire**.
- **The North Sea Empire:** Cnut's Anglo-Danish-Norwegian empire, never broken up, with dominions in Markland,
  the Cape and Nýjaland. It leads the **North Sea Thing**.
- 114 other nations, including the Hanseatic Union, the Avar Khaganate, Lord Novgorod the Great, the Khazar
  Khaganate, the Empire of the Great Song, Tawantinsuyu, the Commonwealth of Vinland and the Republic of Fusang.

**Every one of the game's 1046 states is reassigned.** See [`WORLD.md`](WORLD.md) for the full chronicle of all
117 nations.

## What the mod does

| Feature | Where |
|---|---|
| Whole-world map, subjects, factions and cores at game start | `common/scripted_effects/aw_world_effects.txt`, run from `common/on_actions/aw_world_on_actions.txt` |
| Name, flag, ideology, leader, party names and national spirit for each of the 115 world nations | same, plus `common/ideas/aw_world_ideas.txt` and `gfx/flags/AW_*` |
| Starting armies for nations that did not exist in vanilla | same |
| A chronicle event for every nation (shown to players at start, re-readable from the *Chronicles* decisions) | `events/aw_world_events.txt` |
| A shared 22-focus tree for every nation except Rome and Eranshahr, replacing vanilla trees whose history no longer exists | `common/national_focus/aw_world_focus.txt` |
| Hand-made focus trees, events, decisions and spirits for Rome and the Saoshyantate | `common/national_focus/rpr_focus.txt`, `sao_focus.txt`, `events/byzsao_events.txt`, … |

## Editing the world

All the generated files above come from one table, `tools/world_data.py`. Each country entry there has its tag,
name, ideology, leader, capital, states, national spirit, flag design and lore.
`tools/vanilla_states.json` holds the 1936 owner and name of every vanilla state.

```sh
python3 tools/build_world.py              # validate and regenerate everything
python3 tools/build_world.py --no-flags   # skip the (slow) flag rendering
```

The build refuses to run if any state is unassigned, assigned twice, or if a capital lies outside its
country.

## Install

1. Copy this folder to `Documents/Paradox Interactive/Hearts of Iron IV/mod/fire_and_hammer/`.
2. Next to it, create `mod/fire_and_hammer.mod` containing `descriptor.mod` plus one extra line:
   `path="mod/fire_and_hammer"`.
3. Enable the mod in the launcher and start a 1936 game.

## Notes and limitations

- The world is redrawn in `on_startup`, so the country-selection screen still shows vanilla borders. Pick the
  vanilla country whose tag is listed for your nation in `WORLD.md` (for example `ENG` for the North Sea
  Empire).
- New nations are spawned by releasing their tag and then transferring their states. Vanilla armies stay
  with their original tags, so units may begin outside their country's new borders.
- Vanilla national spirits of reused tags are not removed. Vanilla decisions that check a tag may still
  appear.
- The mod has not been run in-game yet. Check `error.log` on first launch.
