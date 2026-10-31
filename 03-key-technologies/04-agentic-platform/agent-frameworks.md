# Agent Frameworks

Libraries that give you the agent loop, tool calling, memory hooks and multi-agent orchestration so you do not write it from scratch. Last verified: 2026-10.

## Comparison

| Framework | Model | Notes |
|---|---|---|
| **Microsoft Agent Framework** | Agents + graph-based Workflows + a Harness Agent | .NET, Python, Go (preview). Successor to Semantic Kernel and AutoGen (same teams). Sessions for state, context providers for memory, middleware, MCP client, telemetry. Providers include Foundry, Azure OpenAI, OpenAI, Anthropic, Ollama. Runs as a hosted agent in Foundry |
| **Semantic Kernel** | Plugins, planners, filters | Mature .NET/Python/Java SDK; Agent Framework is the direction for new work |
| **LangGraph** | Explicit state graph, checkpointers | Python/JS; strong persistence and human-in-the-loop; also deployable as a Foundry hosted agent |
| **OpenAI Agents SDK, others** | Handoffs, guardrails, tracing | Lightweight; provider-centric |
| **Raw SDK + your code** | Full control | Fine for simple loops, you own everything |

## Agents vs workflows

| Use an agent when | Use a workflow when |
|---|---|
| Task is open-ended and needs autonomous tool choice | Steps are known and order matters |
| One LLM call (maybe with tools) suffices | Several agents or functions must coordinate |

"If you can write a function, do that instead of using an agent." Workflows give explicit paths, typed messages, checkpoints and human-in-the-loop.

## What a framework should give you

- Tool and MCP integration with schema generation and validation.
- **State and sessions** (thread history, checkpoints) with pluggable stores.
- **Middleware/filters** for logging, guardrails, approvals, cost caps.
- **Telemetry** (OpenTelemetry traces with token and cost data).
- Orchestration patterns: sequential, concurrent, handoff, group chat, supervisor.

## How to choose

1. Azure-first, .NET or Python, want Foundry hosting and evals: Microsoft Agent Framework.
2. Existing LangGraph investment or need its checkpointing model: LangGraph, hosted on Container Apps or Foundry.
3. Long-running and crash-safe: put the framework loop inside a durable engine, see [Durable Orchestration](durable-orchestration.md).
4. Avoid lock-in: keep tools behind MCP, prompts and eval sets outside the framework.

## Failure modes

- Framework abstractions hide token use: instrument traces early.
- Rapid version churn (preview packages): pin versions, test upgrades with your eval set.
- In-memory session state lost on restart: use a durable store.
- Third-party servers and tools run outside your compliance boundary: review data flow.

## Interview cheat-sheet

- Say: "Agent Framework workflows for the deterministic parts, an agent loop with budgets for the open-ended part, tools via MCP, state in a durable store, traces to Application Insights."
- Related: [Foundry](foundry.md), [Agent Orchestration Patterns](../../02-core-concepts/04-agentic/agent-orchestration-patterns.md).
