# Opening the "Black Box"

### *From Linear Regression to ChatGPT in 60 Minutes*

**Eduardo Dueñez** · University of Texas at San Antonio
**Universidad Panamericana** · May 21, 2026

A 1-hour survey talk for an undergraduate mathematics audience, presenting three
mathematical surprises that animate modern AI:

1. **Universal approximation** — any continuous function lives in the space neural
   networks can represent.
2. **Double descent** — making the model *bigger* past the data size makes it
   generalize *better*.
3. **In-context learning** — large language models learn at inference time, without
   changing a weight.

## Slides

- **[2026-UPanamericana-mathAI.pdf](./2026-UPanamericana-mathAI.pdf)** — Beamer PDF, 16 slides.

## Notebooks

Each notebook is the live demo for one act of the talk. Click the Colab badge to
open in your browser, or download the `.ipynb` and run locally with
`jupyter lab` / `jupyter notebook`.

| Act | Topic | Open in Colab |
|----:|-------|---------------|
| **I** — How does a network learn? | MNIST classification with a small MLP; lands the **Universal Approximation Theorem**. | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/eduenez/public-site/blob/main/2026-UPanamericana-mathAI/notebooks/act1_mnist_demo.ipynb) |
| **II** — Why does making it bigger help? | Random ReLU features sweep across the interpolation threshold; lands **double descent**. | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/eduenez/public-site/blob/main/2026-UPanamericana-mathAI/notebooks/act2_double_descent_demo.ipynb) |
| **III** — How does ChatGPT actually work? | Tokens → embeddings → attention → text generation with GPT-2; lands **in-context learning**. | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/eduenez/public-site/blob/main/2026-UPanamericana-mathAI/notebooks/act3_attention_demo.ipynb) |

## Live-demo prompts

[**`ollama_prompts.md`**](./notebooks/ollama_prompts.md) — the exact prompts used during
the talk's live Ollama demos, with expected behavior and known failure modes. Run
locally with [Ollama](https://ollama.com/) after `ollama pull llama3.2`.

## Acknowledgements

The course materials for [MAT 4953/6973 — Mathematical Foundations of AI](https://github.com/eduenez/MathAIspring2026UTSA)
(UTSA, Spring 2026) were the seedbed for these notebooks.
