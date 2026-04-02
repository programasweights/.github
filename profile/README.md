<h1 align="center">ProgramAsWeights</h1>

<p align="center">
  Compile natural language specs into tiny neural functions that run locally.
</p>

<p align="center">
  <a href="https://pypi.org/project/programasweights/"><img alt="PyPI" src="https://img.shields.io/pypi/v/programasweights?label=pypi"></a>
  <a href="https://www.npmjs.com/package/@programasweights/web"><img alt="npm" src="https://img.shields.io/npm/v/@programasweights/web?label=npm"></a>
  <a href="https://github.com/programasweights/programasweights-python/blob/main/LICENSE"><img alt="License" src="https://img.shields.io/badge/license-MIT-blue"></a>
</p>

<p align="center">
  <a href="https://programasweights.com">Website</a> · <a href="https://programasweights.com/docs">Docs</a> · <a href="https://programasweights.com/hub">Program Hub</a> · <a href="https://programasweights.com/agents">Agents</a> · <a href="https://github.com/programasweights/programasweights-python/discussions">Discussions</a>
</p>

---

### Quick Start

```bash
pip install programasweights --extra-index-url https://pypi.programasweights.com/simple/
```

```python
import programasweights as paw

# Compile a natural language spec into a neural function
program = paw.compile(
    "Classify if this message requires immediate attention or can wait",
)

# Load and run locally — no internet needed after download
fn = paw.function(program.id)
fn("Server is down, customers affected!")  # → "immediate"
fn("Newsletter: spring picnic Friday")     # → "wait"
```

Once compiled, functions run offline — no API keys, no internet, no per-call cost.

### When to use PAW

- **Classification** — sentiment, urgency, intent routing
- **Extraction** — emails, names, dates from unstructured text
- **Format repair** — fix broken JSON, normalize dates
- **Fuzzy search** — typo-tolerant matching, near-duplicate detection
- **Agent preprocessing** — parse tool calls, validate outputs, route tasks

### Browser SDK

Programs compiled with the Compact interpreter also run in the browser via WebAssembly — no server needed, data stays on the user's device.

```bash
npm install @programasweights/web
```

```javascript
import paw from '@programasweights/web';

const fn = await paw.function('programasweights/email-triage');
await fn('Server is down!');  // → "immediate"
```

### Repositories

| Repo | Description |
|------|-------------|
| [**programasweights-python**](https://github.com/programasweights/programasweights-python) | Python SDK |
| [**programasweights-js**](https://github.com/programasweights/programasweights-js) | Browser SDK |
| [**wllama**](https://github.com/programasweights/wllama) | WebAssembly llama.cpp fork with LoRA + KV cache support |

### Two interpreters

| | Standard (Qwen3 0.6B) | Compact (GPT-2 124M) |
|---|---|---|
| Accuracy | Higher | Lower |
| Program size | ~22 MB | ~5 MB |
| Runs in browser | No | Yes |
