# benchmark-triage-agent

An AI agent that finds performance regressions in benchmark results across
game builds, GPU drivers and hardware, investigates them with MCP tools
(log analysis, benchmark history, known issues) and writes evidence-backed
triage reports for human review.

## Why
Performance labs run thousands of benchmarks per driver or build. When a number
drops, an engineer must find out whether the drop is real, what changed and
whether it is already known. This project automates that first triage step and
keeps a human in the loop.

## How it works (planned)
1. Detect: statistical regression detection (Mann-Whitney U, FDR control)
2. Investigate: an LLM agent calls MCP tools to diff service logs, check
   history and search known issues (PostgreSQL + pgvector)
3. Report: structured report with root-cause hypothesis, evidence, next steps
4. Evaluate and observe: precision/recall, LLM-as-a-judge, human review,
   OpenTelemetry traces

## Data
All data is synthetic and generated with a fixed seed: fictional games, GPUs
and driver versions with injected regressions and a known ground truth.

## Roadmap
- [ ] Synthetic benchmark data, service logs and known issues
- [ ] Regression detection and its evaluation
- [ ] MCP server for log analysis and benchmark history
- [ ] Known-issue retrieval with pgvector
- [ ] Triage agent with structured reports
- [ ] Evaluation with LLM-as-a-judge and human review
- [ ] Observability and guardrails
- [ ] Docker Compose and CI

## Tech
Python 3.12, uv, PostgreSQL + pgvector, MCP Python SDK, OpenAI-compatible
LLM API (NVIDIA API Catalog), FastAPI, OpenTelemetry, GitHub Actions