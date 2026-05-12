# How I work with AI coding agents

I use five phases. Here's what that actually looks like, using a recent project as an example.

> **Live demo:** [aymenfurter.github.io/dog-map](https://aymenfurter.github.io/dog-map/)

## The phases

### 1. Braindump

I record my ideas by voice and paste the transcript into a file. It's messy -- half-formed sentences, tangents, repetition. I don't clean it up. The agent can't read my mind, so this raw transcript has to do the job instead.

### 2. Research

Before anyone writes code, I need facts. What does the API actually return? What does the data look like? Which libraries exist for this?

The agent helps here. In this project I had it spin up research subagents to find all the CSV datasets on Zurich's open data portal. It came back with 16 data sources and their URLs.

<img src="images/02-research.png" alt="The agent running research subagents to find data sources">

This matters because agents will confidently make up API endpoints that don't exist. You have to ground them first.

### 3. Plan

We turn the braindump into actual tasks. Pick an architecture, figure out the order of work. The agent proposes, I push back, we go back and forth.

It asks clarifying questions -- what did I mean by "animated" patterns? What should the fun facts view show?

<img src="images/03-brainstorm.png" alt="The agent asking clarifying questions">

Then it puts together a plan: milestones, tech stack, data findings. I can accept it, change it, or throw it out. Nobody has written any code yet.

<img src="images/03-plan.png" alt="The agent presenting a structured plan for review">

### 4. Implement

The agent writes code and I review after each chunk. Not at the end -- after each one. If something drifts, I correct it right away.

Letting the agent run for 20 minutes unsupervised and then discovering it went sideways -- that's 20 minutes wasted.

### 5. Next session

At the end of a session I write a short summary: what got done, what's left, any decisions or blockers. This becomes the starting point for the next conversation.

Agents have zero memory between sessions. Without this handoff, every conversation starts from scratch.

## Tactics

A few things that make the phases above work better in practice.

I use **MS Learn MCP** to ground the agent in current docs. When it cites an API, I want it citing the real one, not something from its training data.

I run everything in a **devcontainer**. The agent can install packages, run scripts, break things, and none of it touches my actual machine.

I have the agent write **e2e tests** alongside features. If the test passes, I trust the code more. Linting and security scanning run automatically, so by the time I look at the code, the mechanical stuff is already caught. I care about review throughput, not how many PRs get opened.

Instead of accepting the first approach, I ask for **variants**: "Redesign this, give me 5 options." I can also tell it to **spawn subagents** so each option gets explored in parallel. For decisions that really matter I'll have it use **different models** for each variant -- Claude, Gemini, GPT -- because they have different blind spots.

Anything I do more than twice becomes a **skill file**. OTel instrumentation, test scaffolding, deployment configs. Write the instructions once and the agent reuses them.

I try to **keep context files lean**. Stale context is worse than no context. If a note is outdated, I delete it rather than letting it confuse the agent.

## License

MIT
