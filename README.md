<a name="readme-top"></a>

<div align="center">
  <h1 align="center" style="border-bottom: none">🧠 Self-Improving AI Pipelines & Prompt Optimizer Engine</h1>
  <p align="center">
    <strong>Declarative Framework for Programming Foundation Models, Automatic Prompt Compilation, and Self-Refining AI Pipelines (DSPy).</strong>
  </p>
</div>

<div align="center">
  <a href="https://github.com/NadeemAhmad3"><img src="https://img.shields.io/badge/Author-Nadeem%20Ahmad-blue?style=for-the-badge&logo=github" alt="Author"></a>
  <a href="mailto:engrnadeem26@gmail.com"><img src="https://img.shields.io/badge/Email-engrnadeem26%40gmail.com-red?style=for-the-badge&logo=gmail" alt="Email"></a>
  <a href="https://github.com/NadeemAhmad3/self-improving-ai-pipelines"><img src="https://img.shields.io/badge/Status-Production%20Ready-brightgreen?style=for-the-badge" alt="Status"></a>
</div>

<hr>

## 📌 Executive Overview

**Self-Improving AI Pipelines** (powered by **DSPy**) is a framework for **programming — rather than prompting — Large Language Models**. It replaces manual, fragile prompt engineering with declarative Python signatures, composable LLM modules, and automated prompt optimizers.

Instead of writing static system prompts, you define task contracts, and DSPy automatically compiles, tunes instructions, curates few-shot demonstrations, and optimizes pipeline weights to maximize evaluation metrics (F1, Accuracy, Exact Match).

```text
               ┌────────────────────────────────────────────────────────┐
               │         Declarative Python Signature Contract          │
               └───────────────────────────┬────────────────────────────┘
                                           │
         ┌─────────────────────────────────┼─────────────────────────────────┐
         ▼                                 ▼                                 ▼
┌──────────────────┐             ┌──────────────────┐             ┌──────────────────┐
│ DSPy Modules     │             │ Automated Prompt │             │ Computational    │
│ (CoT, ReAct)     │             │ Optimizer (MIPRO)│             │ Assertions       │
└──────────────────┘             └──────────────────┘             └──────────────────┘
```

---

## 🔥 Core Architectural Innovations

### 1. 📝 Declarative Task Signatures (`dspy.Signature`)
Defines structured input/output requirements cleanly as code contracts:
```python
class QuestionAnswering(dspy.Signature):
    """Answer questions with short, factual responses."""
    context = dspy.InputField(desc="Relevant document snippets")
    question = dspy.InputField()
    answer = dspy.OutputField(desc="Concise 1-5 word answer")
```

### 2. 🧩 Composable LM Modules (`dspy.Module`)
- **`dspy.Predict`**: Core LLM call wrapper.
- **`dspy.ChainOfThought`**: Forces step-by-step reasoning before output generation.
- **`dspy.ReAct`**: Interleaved reasoning and tool action execution for autonomous agent loops.
- **`dspy.ProgramOfThought`**: Generates and executes Python code for computational problem-solving.

### 3. 🚀 Automatic Prompt Compilers (`dspy.teleprompter`)
- **BootstrapFewShot**: Auto-evaluates pipeline executions to curate optimal few-shot prompt examples.
- **MIPROv2 & COPRO**: Uses Bayesian optimization and reflective LLM mutation to discover optimal system prompts.

### 4. 🛡️ Computational Assertions (`dspy.Assert` / `dspy.Suggest`)
Enforces hard execution constraints on LLM outputs (e.g. word length limits, PII filters). On failure, DSPy automatically backtracks and forces the LLM to self-refine its response.

---

## 📂 Repository Architecture

```text
self-improving-ai-pipelines/
├── dspy/                      # Core Framework Engine
│   ├── signatures/            # Typed Signature contracts & field definitions
│   ├── predict/               # Predict, ChainOfThought, ReAct, PoT modules
│   ├── teleprompter/          # Prompt optimizers (BootstrapFewShot, MIPROv2, COPRO)
│   ├── primitives/            # Assertions, suggestions, and backtrack handlers
│   ├── evaluate/              # Metric evaluation harness
│   └── clients/               # Model backends (OpenAI, Anthropic, Ollama, LiteLLM)
├── docs/                      # Technical documentation & user guides
└── tests/                     # Test suite
```

---

## ⚡ Quickstart Guide

### 1. Installation

```bash
pip install dspy
```

### 2. Basic DSPy Chain-of-Thought Program

```python
import dspy

# Configure LLM Client Backend
lm = dspy.LM("openai/gpt-4o-mini", api_key="YOUR_OPENAI_API_KEY")
dspy.configure(lm=lm)

# Define Declarative Signature
class GenerateSummary(dspy.Signature):
    """Summarize the input article into 3 key bullet points."""
    article = dspy.InputField()
    summary = dspy.OutputField(desc="3 bullet points")

# Wrap in Chain-of-Thought Module
summarizer = dspy.ChainOfThought(GenerateSummary)

# Execute Program
response = summarizer(article="DSPy replaces prompt engineering with programming...")
print(response.summary)
```

---

## 👤 Maintainer & Author Information

* **Author**: **Nadeem Ahmad**
* **GitHub**: [@NadeemAhmad3](https://github.com/NadeemAhmad3)
* **Email**: [engrnadeem26@gmail.com](mailto:engrnadeem26@gmail.com)
* **Repository**: [https://github.com/NadeemAhmad3/self-improving-ai-pipelines](https://github.com/NadeemAhmad3/self-improving-ai-pipelines)

---

## 📄 License

Distributed under the MIT License. See [`LICENSE`](./LICENSE) for full details.
