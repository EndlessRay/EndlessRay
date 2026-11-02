# Deepan Singh, MD, FAPA

Physician-founder and CEO of [DNAi Systems](https://dnai.systems). I build [Asha](https://askasha.org), a medical AI agent that returns its sources with every answer, and the platform it runs on.

## Start here

| If you want to | Go to |
|---|---|
| Call Asha from your product (OpenAI SDK, A2A, MCP, CLI) | [**DNAiOS/asha**](https://github.com/DNAiOS/asha) |
| Check the benchmark numbers item by item | [**asha-benchmarks**](https://github.com/EndlessRay/asha-benchmarks) |
| See the published register (hash-checked against the live API) | [dnai.systems/benchmarks](https://dnai.systems/benchmarks) |
| Read the paper (preprint, not peer reviewed) | [doi:10.21203/rs.3.rs-10206806/v1](https://doi.org/10.21203/rs.3.rs-10206806/v1) |

```python
from openai import OpenAI

client = OpenAI(base_url="https://api.askasha.org/v1", api_key="dnai_a2a_...")
reply = client.chat.completions.create(
    model="asha",
    messages=[{"role": "user", "content": "Which antihypertensives are safe in pregnancy?"}],
)
print(reply.choices[0].message.content)
print(reply.model_extra["dnai_meta"]["citations"][:3])
```

Free key: [askasha.org/developers](https://askasha.org/developers/).

## What Asha is

An architecture around a language model. No model is fine-tuned. Questions go through retrieval from a curated medical corpus (111M vectors in its 20 public collections, committed by SHA-512 at [`/api/audit/corpus-state/public`](https://api.askasha.org/api/audit/corpus-state/public)), specialist agents, claim falsification, and safety gates before and after generation. US Patent [12,555,008 B1](https://patents.google.com/patent/US12555008B1), granted 2026-02-17.

The benchmarks are paired: the same model alone and inside Asha, on the same items, under the same grader. Three rows from the register (2026-11-01):

| Benchmark | Model alone | Inside Asha |
|---|---|---|
| HealthBench Hard, 1,000 items, official gpt-4.1 grader | 32.4 | 48.7 (+16.3; length-adjusted +13.7) |
| HealthBench, all 5,000 conversations, official grader | 55.6 | 65.5 (+9.8; length-adjusted +7.4) |
| psychosis-bench, 96 turns, May 2026 model | 30.2% | 95.8% |

Limits are published next to every row, including where frontier models with web search score higher. Read them before quoting a number.

## Where the product code is

The Citadel monorepo (FastAPI, React + Vite, Qdrant, PostgreSQL, Redis, Docker) is private because it runs a live medical product with real users. Since December 2025: 3,521 commits on main and 1,315 merged pull requests, 97% of the commits by the two physician co-founders. Walkthrough on request.

Co-founder: [Paridhi Anand, MD](https://github.com/circumferance). Contact: dsingh@dnai.systems
