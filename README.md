# BENCORP GPU Ladder

Practical GPU and quant profiles for running open coding agents.

This repo is a public notebook for BENCORP's local-agent inference experiments:
which models fit on which GPUs, what they cost, what quality evidence exists,
and what it takes to reproduce the useful profiles.

> This repo is sponsored by [BENCORP](https://bencorp.dev/).

The HTML pages are the primary reports. The README is the index.

## Start Here

- [HTML index](index.html)
- [Ornith 1.0 35B Q5 on one RTX 3090](experiments/ornith-35b-rtx-3090.html)
- [Planned: Qwen3.6 27B on one RTX 3090](experiments/qwen-27b-rtx-3090.html)

## Current Ladder

| Tier | Best current question | Status |
| --- | --- | --- |
| RTX 3090 24GB | What is the smartest serious local-agent profile under cheap rented GPU economics? | Ornith 35B Q5 runtime proven; Qwen3.6 27B next. |
| A100 40GB | Can Qwen3.6 27B run at higher fidelity without H100 pricing? | Planned. |
| L40S / RTX 6000 Ada | Is comfortable single-GPU Q8 the best cost/intelligence point? | Planned. |
| H100 / H200 | What is the reference ceiling before bigger multi-GPU models? | Internal baseline evidence exists; public page pending. |

## How To Read A Result

Each experiment tries to separate three claims:

- **Fit:** does the model actually load at the target context and stay stable?
- **Speed:** does it clear the practical agent floor, using both server decode
  and client-observed wall tokens per second?
- **Quality:** does it solve agent tasks well enough to matter?

The default floor is 5 wall tokens per second. Above that floor, quality wins.
A smaller or lower-quant profile is only better if it makes the agent more
useful, not merely faster.

## Safety Boundary

This repo contains safe summaries: model links, configs, hashes when useful,
timings, costs, and high-level conclusions. It should not contain raw red-team
prompts, private traces, credentials, or BENCORP-internal task data.
