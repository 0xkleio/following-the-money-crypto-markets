# Methodological parameters

These notes answer the C+J reviewer questions about implicit thresholds.

## Cluster versus bundle

Taken from Bubblemaps’ own distinction and from the short paper:

- A **cluster** is a group of wallets joined by *observed transfers*.
- A **bundle** is a group of wallets that purchase in the **same block** or an extremely narrow slot window (including Jito bundles where that metadata is available).

This case uses Bubblemaps’ date-filtered holder graph as the cluster source. Same-block / same-slot co-purchase is treated as a *probabilistic* signal of shared control, never as proof by itself. Independent snipers and bots can also land in the same slot.

No additional numeric “N seconds” cutoff beyond same-block / adjacent-slot co-purchase was imposed.

## Stage 3 sampling

Not random, not “top 3 only”.

- Unit: one address per major visible cluster on the $WAP Bubblemaps graph filtered to **7 October 2024**.
- N = **20** clusters (the major clusters that were large enough to appear as separate groups on that date filter).
- The exact addresses are frozen in `wap-sample-wallets.csv`.
- After sampling, every wallet was traced backward to its first material funding event. Wallets that shared an upstream deBridge sender were then grouped.

## FixedFloat correlation

FixedFloat does not publish a transparent sender→recipient map the way deBridge does. The heuristic used:

1. Read the Solana-side credit that first funded the $LIBRA deployer (`DefcyKc4yAjRsCLZjdxWuSUzVohXtLna9g22y3pBCm2z`). Note timestamp and USD value.
2. Restrict Arkham’s FixedFloat entity view to **14 February 2025**.
3. Keep deposits / sweeps whose USD value falls in **2,180–2,300**.
4. Allow FixedFloat *hot-wallet* inflows to land **minutes after** the Solana credit. The service sometimes sweeps personalized deposit addresses to a liquidity wallet with a short delay.
5. Prefer matches that originate on **Arbitrum**, because the $WAP work had already established an Ethereum-side funding habit.
6. Require a **common EVM sender** behind several of those deposit addresses before treating the path as a lead.
7. Confirm that the corresponding Solana payouts land on wallets that *do something* the same day (here: three token deployments).

Value delta accepted: roughly **± USD 120** around the 2.2k band, which is the band observed on the Solana credits themselves. Wider matches were discarded.

## SideShift correlation

Same logic as FixedFloat: match time window + value + a common ultimate EVM sender. Used only for the $NETH pattern check, not to justify expanding the original seed.

## Expansion rule

A second token is in scope only if Stage 3 or Stage 4 produced one of:

- the same funded Solana wallet appearing as an early buyer of the next token, or
- the same upstream EVM funder appearing behind the next deployer or first buyer.

Thematic similarity (“another celebrity coin”) is not a reason to expand.

## Labels

Arkham entity names are recorded in `key-addresses.csv` under `arkham_label`. In the short paper they are collapsed to **Entity A**. Reproduction should keep the raw label visible and the paper’s caution intact.
