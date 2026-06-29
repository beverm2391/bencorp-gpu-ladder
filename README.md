# BENCORP GPU Ladder

Practical GPU and quant profiles for running open coding agents.

This repo is the public map for BENCORP's local-agent inference experiments:
which open models run on which GPUs, what they cost, how they feel in real
agent work, and what it takes to reproduce the useful profiles.

The goal is not to crown a generic "best local LLM." The goal is narrower and
more useful:

```text
Given a GPU tier, what is the smartest coding-agent profile that is still
usable, reproducible, and cost-rational?
```

## First Ladders

The initial ladder starts with the hardware people actually ask about:

| Tier | Question | First profiles |
| --- | --- | --- |
| RTX 3090 24GB | Cheapest serious local-agent tier | Ornith 35B Q5, Qwen3.6 27B Q5 |
| A100 40GB | Cheap Q8 frontier | Qwen3.6 27B Q8 at reduced context |
| RTX 6000 Ada / L40S | Comfortable single-GPU Q8 tier | Qwen/Qwable 27B Q8-class profiles |
| H100 / H200 | Reference ceiling | Full-context Q8 and larger model probes |

## What Each Experiment Reports

Each experiment should answer the same questions:

- **Verdict:** would we use it, for what, and why?
- **Hardware:** GPU, VRAM, provider, cost per hour, and any host caveats.
- **Model:** Hugging Face repo, exact file, quant, size, and hash when useful.
- **Runtime:** llama.cpp or fork, commit, context, KV cache format, MTP,
  offload, batch settings, and important flags.
- **Fit:** idle and active VRAM, what failed, and what finally worked.
- **Speed:** prompt prefill, server decode tok/s, wall tok/s, and first-token
  behavior when measured.
- **Quality:** coding-agent eval result, visible caveats, and subjective notes
  that survived comparison.
- **Run it:** commands or pointers that let someone reproduce the profile
  without guessing.

## Current Bias

Quality is the objective. Hardware and context are constraints. Speed is a
floor.

For coding-agent work, a profile that is merely fast is not enough. A profile
has to clear a practical wall-clock floor and then win on usefulness. The
default floor for these notes is 5 request-observed wall tokens per second on
the target workload.

## Safety Boundary

This repo should contain safe summaries: model links, configs, hashes, counts,
timings, costs, and high-level conclusions. It should not contain raw
red-team prompts, raw sensitive model responses, private traces, credentials,
or BENCORP-internal task data.

## Status

Bootstrap repo. The first published page will start from the already-proven
single-RTX-3090 Ornith Q5 work, followed by the Qwen3.6 27B 3090 and A100
experiments.
