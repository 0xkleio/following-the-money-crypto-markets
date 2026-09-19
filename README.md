# Following the Money in Crypto Markets

**Reproduction package** for the Computation + Journalism 2026 short paper:

> Kleio Kalamaridi, Catherine Sotirakou, Constantinos Mourlas.  
> *Following the Money in Crypto Markets: A Reproducible Blockchain-Forensic Workflow for Investigative Journalism.*  
> Computation + Journalism Symposium, October 2026, Evanston, Illinois.

This repository publishes the on-chain identifiers, tool links, sampling rules, and step-by-step procedure that the short paper could not fit. A second researcher should be able to open the linked explorers, recover the same addresses and paths, and separate **direct observations** from **third-party labels** and **inferences**.

The case study is drawn from the practical chapters of:

> Kleio Kalamaridi. 2026. *Investigative Journalism and Blockchain Forensics: An On-Chain Analysis of Celebrity and Political Memecoin Launches on Solana.* Undergraduate thesis, National and Kapodistrian University of Athens.

**Repo:** https://github.com/0xkleio/following-the-money-crypto-markets

![QR code to this repository](https://api.qrserver.com/v1/create-qr-code/?size=220x220&data=https%3A%2F%2Fgithub.com%2F0xkleio%2Ffollowing-the-money-crypto-markets)

Scan the QR code to open this repository on a phone.

---

## How to use this package

1. Read the **interpretive caution** below.
2. Open the token and wallet tables in [`artifacts/`](artifacts/).
3. Follow the five stages in order. Do not skip to a later token unless Stage 3 or Stage 4 produced a direct lead.
4. Grade each link with the evidence-strength rubric.
5. Cross-check the Figma graph and the walkthrough video only after you have reproduced the path in a block explorer.

### Interpretive caution

This package reports **address-to-address transactions** and **time-stamped third-party labels**. It does **not** identify wallet controllers, beneficial owners, or legal responsibility.  
**Entity A** in the short paper is a neutral pseudonym for a third-party analytics label (Arkham Intelligence: *Kelsier Ventures*). The label is a lead, not proof of ownership, control, or liability.

---

## Visual and video supplements

| Resource | URL | What it shows |
|---|---|---|
| Full transaction graph (Figma) | [Thesis board, node `2983-802`](https://www.figma.com/board/On7B3joUExUT0xtcoTpICB/Thesis?node-id=2983-802) | End-to-end map of wallets, bridges, and cash-out hops used in the thesis |
| Overview of the same board | [Thesis board, node `0-1`](https://www.figma.com/board/On7B3joUExUT0xtcoTpICB/Thesis?node-id=0-1) | Entry view of the graph |
| Walkthrough video | [YouTube: `V7PD2sIA2eo`](https://www.youtube.com/watch?v=V7PD2sIA2eo) | Screen-recorded reconstruction from the $WAP social-media seed through $LIBRA and $MELANIA |

The Figma graph is the complete visual artifact; thesis figures and the short-paper figures are excerpts from it.

---

## Tools (all public)

| Stage | Tool | Role |
|---|---|---|
| Seed / price | [GMGN](https://gmgn.ai/), Dexscreener | Launch date, market-cap collapse, first-buyer ranking |
| Holder clusters | [Bubblemaps](https://v2.bubblemaps.io/) | Visualize early holders; distinguish *cluster* from *bundle* |
| Solana verification | [Solscan](https://solscan.io/) | Creator address, oldest funding tx, token mint |
| Cross-chain (transparent) | [deBridge](https://app.debridge.com/) | Backward trace of Solana funding to an EVM source |
| Cross-chain (opaque / mixer-like) | FixedFloat, SideShift | Correlate deposits and payouts by time and value |
| Graph + labels | [Arkham Intelligence](https://www.arkhamintelligence.com/) | Path visualization and third-party entity labels |
| USDC interchain | [Range](https://usdc.range.org/) | Forward / return USDC flows |

No paid API and no leaked records are required.

---

## Methodological parameters

These are the boundary conditions reviewers asked for. Full notes live in [`artifacts/parameters.md`](artifacts/parameters.md).

| Parameter | Operational definition used in this case |
|---|---|
| **Cluster** | Bubblemaps group linked by *observed transfers* between wallets |
| **Bundle** | Wallets that buy in the *same block*, or that Bubblemaps / Jito data treat as a coordinated same-slot purchase. Temporal co-occurrence is a *probabilistic* signal, not proof of shared control |
| **Date filter for $WAP holders** | Launch calendar date: **7 October 2024** |
| **Stage 3 sampling** | **One sample wallet from each of 20 major visible holder clusters** on the date-filtered Bubblemaps graph (not a random 10% draw; not “top 3 by balance” only). See [`artifacts/wap-sample-wallets.csv`](artifacts/wap-sample-wallets.csv) |
| **FixedFloat match window** | Same calendar day as the Solana-side funding of the $LIBRA deployer (**14 February 2025**), with liquidity-hot-wallet inflows allowed *slightly after* the Solana credit because FixedFloat sometimes delays internal sweeps |
| **FixedFloat value band** | Solana-side credits of about **USD 2,180–2,300** |
| **FixedFloat chain priority** | Among value/time matches, prefer deposits that originate on **Arbitrum**, consistent with the Ethereum-side funding already seen in $WAP |
| **Expansion rule** | Move to a second token *only* when Stage 3 or Stage 4 produces a **direct on-chain lead** (shared funded wallet reused as a later sniper, or a shared upstream funder) |

---

## Evidence-strength rubric

Use this when writing up a path. Do not combine grades into a hidden numeric score; state the strongest *kind* of evidence you actually have.

| Grade | What counts | Example in this case |
|---|---|---|
| **Strong** | Direct transaction relationship: shared funding source, deployer-to-funder path, or profits returning to the same wallet | Same Ethereum funder behind the $WAP deployer and many early cluster wallets; $MELANIA first-buyer proceeds looping back toward the same upstream address |
| **Moderate** | Recurring operational pattern: similar funding timing, repeated bridge, comparable amounts | Repeated deBridge preparation of many Solana wallets; FixedFloat used again for $LIBRA and $MELANIA |
| **Weak** | General behavioral resemblance or common infrastructure (public snipers, shared DEX, common bridge) | “Bought early” alone; “used FixedFloat” alone |
| **Label lead** | Third-party classification (Arkham, etc.) | “Entity A / Kelsier Ventures” on Arkham. Treat as a lead. Never as proof of control |

---

## Token index

| Token | Chain | Launch | Mint / contract | Explorer / market |
|---|---|---|---|---|
| **$WAP** | Solana | 7 Oct 2024 | `Bz7vVzQhm2KMW1XgcrDruYega1MiwrAs1DQysrx4tFkp` | [GMGN](https://gmgn.ai/sol/token/Bz7vVzQhm2KMW1XgcrDruYega1MiwrAs1DQysrx4tFkp) · [Bubblemaps](https://v2.bubblemaps.io/map?address=Bz7vVzQhm2KMW1XgcrDruYega1MiwrAs1DQysrx4tFkp&chain=solana) |
| **$LIBRA** | Solana | 14 Feb 2025 | `Bo9jh3wsmcC2AjakLWzNmKJ3SgtZmXEcSaW7L2FAvUsU` | [GMGN](https://gmgn.ai/sol/token/Bo9jh3wsmcC2AjakLWzNmKJ3SgtZmXEcSaW7L2FAvUsU) · [Solscan](https://solscan.io/token/Bo9jh3wsmcC2AjakLWzNmKJ3SgtZmXEcSaW7L2FAvUsU) |
| **$MELANIA** | Solana | 19 Jan 2025 | `FUAfBo2jgks6gB4Z4LfZkgSZgzNucisEHqnNebaRxM1P` | [GMGN](https://gmgn.ai/sol/token/FUAfBo2jgks6gB4Z4LfZkgSZgzNucisEHqnNebaRxM1P) |
| **$NETH** (pattern check, not a seed) | Solana | Feb 2025 window | `s2dm5sk46qys6ecff7Wia2ANFS269MLfvcyMWKkNETH` | Used only after the Entity A–labelled funder appeared on both deployer and sniper sides |

Public promotion posts used as *seeds*, not as proof:

- Cardi B / $WAP: https://x.com/iamcardib/status/1843429101518172618
- Melania Trump / $MELANIA: https://x.com/MELANIATRUMP/status/1881094861279129643
- Javier Milei / $LIBRA: original post deleted; contemporaneous screenshot circulated in news coverage (see thesis Fig. 6.7)

---

## Stage-by-stage reproduction

### Stage 1 — Seed selection

**Criterion used.** Celebrity or political endorsement + abnormal price collapse + visible early-holder concentration.

1. Open the Cardi B post and copy the contract `Bz7vVzQhm2KMW1XgcrDruYega1MiwrAs1DQysrx4tFkp`.
2. Confirm on GMGN that $WAP launched **7 October 2024**, peaked near **$40M** market cap, and later traded near **$21K**.
3. Treat this as a *starting point*, not a finding of manipulation.

### Stage 2 — Holder-cluster analysis

1. Open the [Bubblemaps map for $WAP](https://v2.bubblemaps.io/map?address=Bz7vVzQhm2KMW1XgcrDruYega1MiwrAs1DQysrx4tFkp&chain=solana).
2. Filter holders to **7 October 2024**.
3. Record the large visible clusters. They are not initially joined by obvious direct transfers.
4. Distinguish:
   - **cluster** = transfer-linked wallets;
   - **bundle** = same-block / extremely narrow-window buyers.
5. Sample **one wallet from each of 20 major clusters**. The exact sample used in the thesis is in [`artifacts/wap-sample-wallets.csv`](artifacts/wap-sample-wallets.csv).

An apparently independent early wallet that later joined the same funding pattern:

```
sJJKPpXknWMD5KirZ9WpxGzh8VeMKXrpy48uzYRUgcV
```

### Stage 3 — Funding-source tracing

For each sample wallet:

1. Open the address on Solscan.
2. Inspect the **oldest incoming SOL**.
3. If the source is deBridge, open [deBridge orders](https://app.debridge.com/orders) for the EVM sender.

**Result that should reproduce**

| Role | Address | Notes |
|---|---|---|
| Primary EVM funder | `0xd7ecb027f7d6100b6147f50baed6f787a86004b2` | deBridge source for sample wallets in clusters **1–8, 10–14, 16, 17**; funded **129** Solana wallets on the $WAP launch date; also funded the $WAP deployer |
| deBridge order book | [orders?s=0xd7ecb027f7d6100b6147f50baed6f787a86004b2](https://app.debridge.com/orders?s=0xd7ecb027f7d6100b6147f50baed6f787a86004b2) | Confirm count and timing |
| $WAP deployer / creator | `8yrmLzJBNyAmc8GhrcyEXRA4aUFdHsx3DsZ8QVrHPdLB` | Funded by the same primary EVM wallet |
| Fee-dust funder | `0x4a2fa18a171e00069b8831c613ebd106fcb37388` | Funded **147** wallets with **0.08 SOL** via deBridge the day after launch (clusters 9 and 15). [orders](https://app.debridge.com/orders?s=0x4a2fa18a171e00069b8831c613ebd106fcb37388) |
| Secondary EVM funder | `0x8a83e661a86e31c6b337b5d7bc10ced9a645d2c7` | Cluster 19 only |
| Cluster-18 funder (label lead) | `DQ6r7i7VydwDRijiZ5XGEKWKVh21kVobvMdvQcj4upfb` | [Arkham](https://arkm.com/explorer/address/DQ6r7i7VydwDRijiZ5XGEKWKVh21kVobvMdvQcj4upfb) labels this address as Entity A / Kelsier Ventures |

The two EVM funders `0xd7ec…04b2` and `0x4a2f…7388` also transact with each other. That is a **strong** indicator that several Bubblemaps clusters were not independent.

Cluster 20 did **not** follow the main pattern and is left as a possible independent trader.

### Stage 4 — Cash-out tracing

Start from the Cluster 1 sample:

```
J6285GUWnbt8EMa6aap5m6oodqtvbpZB9o7J1ZdfRYtr
```

Saved Arkham tracer used in the thesis:

- https://arkm.com/tracer/00faed5d-4e1b-46d3-a604-f5c2c2d12bdf

Proceeds fan out through intermediaries rather than a single hop. One recipient:

```
C5rJQ5s9xZvogMUbyPCG6iB2k6cD3h3qmJsGXSiZVvgi
```

[Arkham page](https://arkm.com/explorer/address/C5rJQ5s9xZvogMUbyPCG6iB2k6cD3h3qmJsGXSiZVvgi) — labelled Entity A / Kelsier Ventures. Grade: **label lead**, not proof of control.

**Direct lead used to expand the case.** Two wallets from this cash-out environment later bought $LIBRA at launch:

```
8izuN26YkEv1CJxbD5EFcFKzKSJCWVgZozsyh93jdZEE
7qN8RpRpggQf1gH6pE11vCrWfSH6t9WGZqepR33g5ac7
```

Reuse of funded wallets across two launches is a **strong** transaction link. This is why Stage 5 is allowed.

### Stage 5a — Cross-case expansion to $LIBRA

1. On [Solscan token page](https://solscan.io/token/Bo9jh3wsmcC2AjakLWzNmKJ3SgtZmXEcSaW7L2FAvUsU), read **Creator**:

```
DefcyKc4yAjRsCLZjdxWuSUzVohXtLna9g22y3pBCm2z
```

2. Sort that wallet by oldest activity. The first inbound is labelled **FixedFloat**.
3. On Arkham, open the [FixedFloat entity](https://arkm.com/explorer/entity/fixedfloat).
4. Filter transfers on **14 February 2025** in the **USD 2.18k–2.30k** band.
5. Keep the three Arbitrum-origin FixedFloat deposit addresses:

```
0x86de3FD45FE10a1418C23A5cEBAEF0DBfc55B0F9
0x89Bdc61C0b26F4e9eA9ABCfEB210C427853F768e
0x144285e8D53a07894B2490a88c93DD39E03478Bc
```

6. All three were funded by:

```
0xcEAeFb5BEC983Fd10e324d7e6F5457507BA006e2
```

[Arkham](https://arkm.com/explorer/address/0xcEAeFb5BEC983Fd10e324d7e6F5457507BA006e2) labels this address Entity A / Kelsier Ventures.

7. Matching FixedFloat *payouts* on Solana that day went to three deployers:

| Solana wallet | What it deployed |
|---|---|
| `Ea7Ld4nmdLot5kiREtoVKxyvyAJ1ray7YkiYzEM18jsx` | $ARG |
| `FeJ58f8T6EeBS3X6Dt4gGUpxzKsmkuNcfKzgvntxKz75` | short-lived test token named $LIBRA |
| `DefcyKc4yAjRsCLZjdxWuSUzVohXtLna9g22y3pBCm2z` | the $LIBRA mint later promoted as Milei-associated |

Grade the upstream match as **strong-to-moderate**: timing + value + three parallel same-day deployers from one EVM sender, routed through a mixer-like venue. It is not a transparent bridge hop like deBridge.

### Stage 5b — Same funder, other launches ($NETH pattern check)

On **10 February 2025** the same EVM address `0xcEAe…006e2` funded Solana wallets via deBridge, including:

```
CGzGdWk42B3C1FgPre9hHhsXzQES3cj3iWBbKwSS1tVs
```

Funds hopped through:

```
Em7WgaPE17nvea78hbX2WzUdXJ4PT38Fb4AhHsefLaeo
oAMSw14MMah2xKrTwdpsbntymw9nshU6zVt3pQ4xp8H
6cBSgin3E5M5Vt1bnJijzvsRNjkjMCcpfs13WGK3VQKk
7N82XbiRGARbZCqAuezYCK4uD4hSnRR7E4X6igtFoaKJ
```

and later reached the $NETH sniper:

```
9EmBgGD6M633r54uoNogg8S1mdpnAjyUXfMGq61fhV8T
```

$NETH deployer:

```
ArQ7DqzjD2vchBfReegKNV1rkvAGrunmvwvayn7WC3cX
```

funded via SideShift address

```
ABNL41SwMLVRaCq6okEWsWyvLwm56nazUNwMrTHgmuyf
```

[Arkham](https://arkm.com/explorer/address/ABNL41SwMLVRaCq6okEWsWyvLwm56nazUNwMrTHgmuyf). Matching SideShift deposit:

```
0xE29E251a87F8F09A1eaf7235a9d3dDe8e6F0AA84
```

with the same ultimate EVM sender `0xcEAe…006e2`. This is a **pattern** finding (deployer-side and sniper-side funding from one labelled upstream wallet). It is not used as a fourth seed.

### Stage 5c — Cross-case expansion to $MELANIA

1. Confirm mint `FUAfBo2jgks6gB4Z4LfZkgSZgzNucisEHqnNebaRxM1P` launched **19 January 2025**.
2. The same EVM address `0xcEAe…006e2` funded, via FixedFloat:

```
P5tb4T6SBVQaM3BAoGfpVudLtTdecqzsh4KV9ESAhKg
```

3. On GMGN, this wallet is the **first buyer** of $MELANIA (~USD 40k entry, later ~USD 2.4M realized profit on the tool’s PnL view).
4. USDC outflows from that wallet can be followed on Range:

- https://usdc.range.org/transactions?sc=INTERCHAIN&s=P5tb4T6SBVQaM3BAoGfpVudLtTdecqzsh4KV9ESAhKg

5. Those interchain USDC transfers move back toward `0xcEAeFb5BEC983Fd10e324d7e6F5457507BA006e2`.

That bidirectional path (fund → first buy → return USDC) is a **strong** transaction relationship between the $MELANIA first buyer and the $LIBRA funding path. Early entry alone would only be **weak**.

---

## What a reproduction should and should not conclude

**Supported as an investigative hypothesis**

- Overlapping address infrastructure across $WAP, $LIBRA, and $MELANIA.
- Recurring preparation pattern: cross-chain funding, many fresh Solana wallets, early entry, mixer-like venues when a transparent bridge is not used.
- Direct transaction links that justify *asking* whether the launches share an operational environment.

**Not supported by this package alone**

- That a named person or firm controlled every wallet.
- That any launch was unlawful.
- That a public figure who posted a contract address controlled the deployer or the sniper wallets.

External reporting and lawsuits are **context**, not a substitute for the explorer records. A list of triangulation sources is in [`artifacts/osint-sources.md`](artifacts/osint-sources.md).

---

## Repository layout

```
README.md                      This file
artifacts/parameters.md        Thresholds and sampling rules
artifacts/tokens.csv           Mints and dates
artifacts/wap-sample-wallets.csv
artifacts/key-addresses.csv    Deployers, funders, snipers, labelled wallets
artifacts/osint-sources.md     External cross-checks (not primary proof)
CITATION.cff
LICENSE                        CC BY 4.0
```

Transaction **hashes** and exact block heights are not frozen here as a second database. They are recoverable, and should be recovered, from the linked explorers using the addresses and time windows above. That is intentional: the claim is that a reporter can rebuild the path from public ledgers, not from a private dump.

---

## Citation

If you use this package, cite both the short paper (once the proceedings version is public) and this repository.

```
Kalamaridi, K., Sotirakou, C., & Mourlas, C. (2026). Following the Money
in Crypto Markets: A Reproducible Blockchain-Forensic Workflow for
Investigative Journalism. Computation + Journalism Symposium.
Reproduction files: https://github.com/0xkleio/following-the-money-crypto-markets
```
