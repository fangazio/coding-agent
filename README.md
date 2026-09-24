# Coding Agent

[简体中文](./README.md) | **English**

A reusable set of instructions for AI coding agents, designed to help them work like software engineers accountable for delivery: understand requirements, control scope, complete implementation, verify results, and clearly explain unresolved issues.

The core file is [AGENTS.md](./AGENTS.md). It defines working principles and execution boundaries. It contains no standalone application and is not tied to a particular programming language or technology stack.

## Design Goals

Reduce repeated exploration, unnecessary tool calls, and excessive process while preserving correctness and maintainability. Successful task completion matters more than step counts, document length, or the number of tool calls.

- **Deliver the smallest complete solution**: Implement the requested behavior without unrelated cleanup, refactoring, or overengineering.
- **Match effort to risk**: Handle small, local changes directly; analyze and validate shared interfaces, authentication, concurrency, and data migrations more carefully.
- **Act on evidence**: Start implementation once enough context is available. Expand exploration only when new risks or failed validation justify it.
- **Protect existing work**: Preserve uncommitted changes, stay within authorized scope, and do not perform destructive operations or commit and push code without authorization.
- **Report results accurately**: Distinguish passed, failed, and blocked validation. Never describe unverified behavior as successful.

## How to Use

1. Download [AGENTS.md](./AGENTS.md) from this repository.
2. Place it in the instruction location expected by your coding assistant. If your assistant supports a root-level `AGENTS.md`, place it in your project's root directory.
3. If the project already has an instruction file, compare and merge the applicable rules while preserving existing project constraints. Do not overwrite it blindly.
4. Add the necessary project-specific information, then ask the assistant to perform a concrete task.

File discovery, instruction priority, and directory scope may vary between assistants. Integrate the file according to your actual environment. Uploading it to GitHub alone does not configure assistants in other projects.

## Recommended Project Information

Use Section 12 of `AGENTS.md`, or existing project documentation, to record verified facts that are needed regularly:

| Area | What to Record |
| --- | --- |
| Code entry points | Main source directories, shared modules, and architectural boundaries |
| Development environment | Package manager, required runtimes, and startup instructions |
| Validation | Working commands for tests, builds, type checks, and linting |
| Special constraints | Sources of generated files, migration rules, and compatibility requirements |
| Tools and documentation | Priority of configured code graph tools and authoritative documentation entry points |

Include only information that affects recurring decisions. Put long or infrequently used procedures in separate documents and reference them from the instruction file.

## What the Instructions Cover

| Sections | Focus |
| --- | --- |
| 1–3: Goals, authorization, and task scale | Define delivery standards and match work depth to uncertainty and impact |
| 4–5: Context and tools | Gather focused information, reuse valid evidence, and reduce repeated queries |
| 6: Delegation | Use subagents only when permitted and justified by independent work; keep integration and verification with the main agent |
| 7–8: Engineering practices and task focus | Reuse existing structures, preserve type safety, and apply guidance specific to building, debugging, refactoring, reviewing, and UI work |
| 9: Security, data, and Git | Protect credentials and user work; respect authorization for changes and publishing |
| 10–11: Validation and delivery | Run applicable checks and accurately report completion status and blockers |
| 12: Project facts and maintenance | Keep instructions concise and verifiable, and improve them based on actual use |

## Working Approach

The instructions encourage the following rhythm, without imposing the same process on every task:

1. Establish the user's expectations, scope, and success criteria.
2. Gather enough context about the code, dependencies, and project constraints to act.
3. Complete the smallest full implementation within the authorized scope.
4. Run validation that can detect relevant failures and inspect the final changes.
5. Deliver the result with validation evidence and any remaining limitations.

When blocked, complete work that can proceed independently, then clearly identify the missing input, permission, or environmental condition.

## Limitations

This file provides behavioral guidance. It does not replace runtime permission controls, testing, or code review, and it does not install code graph or documentation tools. Model selection, tool availability, caching, billing, and execution outcomes depend on the assistant and its runtime environment.

This repository does not promise a fixed reduction in token usage or a guaranteed performance improvement. Evaluate changes by comparing correctness and completion first, then consider elapsed time, repeated queries, and actual usage data under comparable model and repository conditions.
