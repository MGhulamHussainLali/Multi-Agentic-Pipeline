# Multi-Agent AI Game Development Pipeline

An agentic LangGraph pipeline that autonomously generates, executes, and iteratively refines a fully playable Chrome Dino Runner game using a team of specialized LLM agents.

## Features

- **Director Agent** — Defines the game requirements and kicks off the pipeline
- **Architect Agent** — Produces a detailed technical design document covering game loop, classes, physics, and controls
- **Engineer Agent** — Generates complete, runnable pygame code informed by the architect's design and QA feedback
- **QA Agent** — Reviews runtime output and code against design requirements, flagging bugs and missing features
- **Scorer Agent** — Rates code quality (1–10) and conditionally re-routes back to the Engineer for fixes

## Tech Stack

`Python` `LangGraph` `LangChain` `Pygame` `Databricks` `Meta LLaMA 3.3 70B` `LangSmith`

## Architecture

```
Director → Architect → Engineer → File Writer → Execute
                          ↑                        ↓
                          └──── Scorer ←────── QA
```

## Self-Improvement Loop

| Node | Role |
|---|---|
| **QA** | Identifies bugs, missing features, and runtime errors |
| **Scorer** | Assigns a quality score (1–10) |
| **Router** | Re-routes to Engineer if score < 10, else exits |

## Observability

LangSmith tracing is integrated for end-to-end visibility into agent decisions, LLM calls, and graph transitions.
