<h1 align="center">Programs as Weights</h1>

<p align="center">
  <strong>Compile natural-language specs into lightweight neural functions that run anywhere.</strong>
</p>

<p align="center">
  <a href="https://programasweights.com">Website</a> ·
  <a href="https://programasweights.com/docs">Docs</a> ·
  <a href="https://programasweights.com/hub">Program Hub</a> ·
  <a href="https://programasweights.com/browser">Browser Demo</a> ·
  <a href="https://github.com/programasweights/programasweights-python/discussions">Discussions</a>
</p>

---

### What is PAW?

PAW compiles a plain-English specification into a small, deterministic neural function — a LoRA adapter + KV cache prefix — that runs on any device without an API key or internet connection.

```bash
pip install programasweights --extra-index-url https://pypi.programasweights.com/simple/
```

```python
import programasweights as paw

# Compile a spec into a neural function (runs on server, ~3s)
fn = paw.compile_and_load(
    "Classify support tickets as 'urgent' or 'normal'. "
    "Urgent: outages, security, data loss. Normal: everything else."
)

# Run locally — no internet needed after download
fn("Our database is not responding")  # → "urgent"
fn("How do I reset my password?")     # → "normal"
```

### Repositories

| Repo | Description |
|------|-------------|
| **[programasweights-python](https://github.com/programasweights/programasweights-python)** | Python SDK — `pip install programasweights` |
| **[programasweights-js](https://github.com/programasweights/programasweights-js)** | Browser SDK — `npm install @programasweights/web` |
| **[wllama](https://github.com/programasweights/wllama)** | Fork of wllama with LoRA + KV cache session support |

### Models

| Model | Size | Use Case |
|-------|------|----------|
| **Standard** (Qwen3 0.6B) | ~22 MB per program | Higher accuracy, GPU or CPU |
| **Compact** (GPT-2 124M) | ~5 MB per program | Browser/edge, ~200ms inference |

### Links

- **Website**: [programasweights.com](https://programasweights.com)
- **Documentation**: [programasweights.com/docs](https://programasweights.com/docs)
- **PyPI**: [pypi.org/project/programasweights](https://pypi.org/project/programasweights/)
- **npm**: [@programasweights/web](https://www.npmjs.com/package/@programasweights/web)
