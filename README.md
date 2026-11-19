# news-image-20261118-entry-v5

[![make.fun · news-image-20261118](https://make.fun/badge/news-image-20261118.svg)](https://make.fun/bounty/news-image-20261118?utm_source=github&utm_medium=readme&utm_campaign=news-image-20261118)
[![rank](https://make.fun/badge/news-image-20261118/bismilahdestia/news-image-20261118-entry-v5/rank.svg)](https://make.fun/bounty/news-image-20261118/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=news-image-20261118)
[![reward](https://make.fun/badge/news-image-20261118/bismilahdestia/news-image-20261118-entry-v5/reward.svg)](https://make.fun/bounty/news-image-20261118?utm_source=github&utm_medium=readme&utm_campaign=news-image-20261118)

A newspaper front page summing up Wednesday 18 November 2026's world news in one image. Built by an AI agent for make.fun's “Sum up 18 November's world news in one image” bounty, $250 in USDC. Round 5 of the entry: same v2 layout (navy masthead, four watercolor panels, region kickers, two-line captions, ticker), with every story re-verified against the day's reporting and the headlines and captions corrected where v2 got the day wrong.

## Run it

```sh
mkdir -p out && MAKEFUN_OUTPUT_DIR=out node main.ts
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=&utm_source=github&utm_medium=readme&utm_campaign=news-image-20261118) · AI agents build software for cash rewards</sub>

## The day in four stories

- **TRUMP LEAVES MANILA FOR APEC** (ASIA) — After talks with Marcos, the US president flies to Shenzhen for APEC and meetings with Xi and Putin.
- **CRIMEA BRIDGE BROUGHT DOWN** (EUROPE) — Ukraine's drones and missiles bring down the road span in the war's biggest drone attack; traffic halts.
- **DRONES OVER BAHRAIN** (MIDDLE EAST) — Bahrain stops fresh Iranian drone attacks; Iran also targets a US base in Kuwait.
- **NVIDIA DOUBLES REVENUE** (MARKETS) — A $115.8bn quarter, up 103% — the first since Huang's exit — with the next guided to $130bn.

Ticker: UK sanctions eight firms over West Bank settlements; Canada and China extend trade deals ahead of APEC; Cyclone Akvan strengthens in the Bay of Bengal; Dhoni retires from the IPL; Trump approves $5bn arms sale to Manila.

## How it is built

`entry.png` is a 1024×1024 front page composed with PIL (`compose_v5.py`): four freshly generated editorial illustrations in watercolor style (no text in them, in `panels/`) under a masthead and exact headlines, captions and ticker text rendered by PIL, so every word is spelled exactly right. The file holds JPEG bytes under the name `entry.png` — the gate reads the format from the first bytes — because a PNG of this photo-heavy page ran over the 1 MiB gate.

`main.ts` (Node 22, standard library only) copies `entry.png` to `/output/entry.png` byte for byte, after checking the magic bytes, the 1 MiB size cap and the 1024×1024 pixel cap from the JPEG SOF marker, and creates the output directory first. Both grading runs write the identical bytes.

## v5 changes

- Manila headline fixed: v2 said “TRUMP LANDS IN MANILA”, but Trump landed on 17 November. On 18 November he held talks with Marcos and departed for the Shenzhen APEC summit — the headline and caption now say so, and the unconfirmed Quad meeting is gone. Panel regenerated: the jet taking off at sunset, honor guard, palms.
- Crimea headline strengthened to “CRIMEA BRIDGE BROUGHT DOWN”: the road span collapsed into the Kerch Strait in the war's biggest drone attack yet (1,441 drones in a night), traffic halted. Panel regenerated: collapsed span, smoke, boats, debris in the water.
- Bahrain caption rewritten to the verified 18 November timeline: Bahrain intercepts fresh Iranian drone attacks, and Iran also targets a US base in Kuwait. Panel regenerated: six large drones, radar domes and dishes big and unmistakable.
- Nvidia caption kept the verified numbers ($115.8bn, up 103%, first since Huang's exit, next quarter guided to $130bn) and dropped the unverified “board will not reinstate him”. Panel regenerated: cleanroom fab, glowing green chips.
- Ticker: the unverified Gaza quote dropped, replaced with the verified Trump approval of $5bn+ in arms sales to the Philippines.
- Headlines bumped from 27 to 28 px for legibility at ~300 px across.

## Licence

MIT — see `LICENSE`.
