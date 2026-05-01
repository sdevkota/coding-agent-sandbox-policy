# Problem Statement

## Pain point

Coding agents interact with legacy IDEs, terminals, package managers, and secrets that were not designed for autonomous behavior.

## Why now

AI systems are moving from chat into action: they retrieve, decide, write, buy, deploy, remember, and delegate. Existing software governance patterns help, but they do not fully describe model uncertainty, prompt/context boundaries, tool autonomy, memory consent, or provenance across AI pipelines.

## v1 intervention

A sandbox policy checker that validates file write roots, network rules, secret exposure controls, and command approval boundaries.

## Non-goals

- This v1 release does not claim to solve the entire research problem.
- It does not require a hosted service or proprietary model.
- It does not hide policy decisions inside opaque model prompts.

## Success criteria

- A maintainer can run the CLI offline.
- A contributor can understand the domain packet in under ten minutes.
- A team can add fixtures, adapters, and stricter checks without rewriting the project.
