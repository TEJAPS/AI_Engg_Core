# Week 1 · Day 1 — Running a Local LLM with Ollama

**Date:** 2026-11-24  
**Course:** AI Engineer Core Track — LLM Engineering  
**Status:** Local model interaction demonstrated; full Day 1 lecture/notebook not yet confirmed complete.

## Source references

- Instructor repository: https://github.com/ed-donner/llm_engineering
- Instructor README, Week 1 Day 1 "Instant Gratification": https://github.com/ed-donner/llm_engineering#instant-gratification-instructions-for-week-1-day-1---with-llama-32-not-llama-33
- Instructor notebook: https://github.com/ed-donner/llm_engineering/blob/main/week1/day1.ipynb
- Ollama: https://ollama.com/
- Model directory: https://ollama.com/search
- Udemy lesson provided by learner: https://jpmc.udemy.com/course/llm-engineering-master-ai-and-large-language-models/learn/lecture/52932165#overview

## Actual hands-on work (confirmed from learner screenshot)

1. Ran `ollama run gemma3:270m` in Windows Command Prompt (command reported by learner).
2. Download completed: layers reached 100%; sha256 digest verification, writing manifest, and success appeared.
3. Entered `hi there` and received a greeting.
4. Entered `my name is teja`; model replied `My name is teja. How can I help you?`, mistakenly adopting the user's name.
5. Entered `no that is my name`; model repeated that response.
6. Entered `it is not ur name, it is my name`; model apologized and asked how to help.
7. Exited the Ollama interactive session back to Windows Command Prompt.

## Core concepts

- **Ollama** runs compatible language models locally and provides a command-line interface and local API.
- **Model vs. runner:** `gemma3:270m` identifies a model/tag; Ollama is the runtime that downloads and serves it.
- **Parameters:** 270M is approximately 270 million model parameters, not token capacity or context-window size.
- **Instruction following:** A fluent response does not guarantee correct interpretation of speaker identity or user intent.
- **Conversational evaluation:** Test behavior across follow-up turns and corrections, not only one isolated prompt.

## Course alignment

The instructor's README suggests `ollama run llama3.2` (or `llama3.2:1b` for a smaller machine). Using Gemma 3 270M is an alternative local-model experiment; don't treat the two models as equivalent or the entire Day 1 as finished.

## Reproduce locally

```powershell
ollama run gemma3:270m
```

Try: `My name is Teja. What is my name?`, then `What name did I tell you?`.

In a separate terminal, useful diagnostics:

```powershell
ollama list
ollama ps
```

## FDE / production relevance

- A locally hosted model can be useful for prototyping, privacy, and offline experiments; assess machine resources and enterprise security requirements before deployment.
- Validate model reliability with repeatable prompt sets, including multi-turn corrections.
- Compare model quality, latency, memory use, and costs before choosing one for a customer workflow.
- This screenshot is evidence of a successful local interactive run, not evidence of production readiness.

## Suggested next experiment (not yet completed)

Run the same short dialogue with a different locally available model, e.g. `llama3.2:1b`, and record which model maintains the user's identity correctly.

## Interview review

**Q: Is a successful natural-language response proof of accuracy?**  
No. Evaluate the response against expected behavior and test follow-up turns, edge cases, and corrections.

**Q: Why run an LLM locally?**  
For low-friction experimentation and possible data-locality benefits, while accepting hardware and model-quality constraints.

**Q: What is a model parameter?**  
A learned numerical weight (or other learned model value), distinct from the number of tokens a model can accept.

## Additional model experiments — 2026-11-24

Learner reports trying Phi-3 and GPT-OSS in addition to Gemma 3 270M. Exact tags, download sizes, outputs and performance are not yet confirmed. Learner described GPT-OSS as 20 GB; if the tag is `gpt-oss:20b`, 20B denotes parameter count rather than storage size. Use `ollama list` to verify tags and sizes and `ollama ps` to inspect loaded models. Next: compare identical prompts, correctness and latency across all three models.
