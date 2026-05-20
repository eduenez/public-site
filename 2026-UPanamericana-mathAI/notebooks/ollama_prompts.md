# Ollama prompt list — Universidad Panamericana talk

Curated and **tested on `llama3.2:latest` (3B)** during prep. Every prompt below has
been run live; expected behavior matches what's shown.

---

## 0. Pre-flight (T – 30 min, at the venue)

```sh
ollama list                       # confirm llama3.2 is present
ollama run llama3.2 ""            # warm up the model (first run is ~2 s slower)
```

If anything is missing:

```sh
ollama pull llama3.2              # 2 GB; needs WiFi the first time
```

Keep the terminal at **font size ≥ 18 pt**, dark background, large window.

---

## 1. Opening hook  (t ≈ 0:30 – 4:00)

You will type one of these into `ollama run llama3.2 >>>`. The point is to show the
model *thinking out loud, token by token, on this laptop*. Activity Monitor reveal
happens while it streams.

**Pick one (ranked from safest to most "performative"):**

### 1A. (Recommended) Self-referential

```
Explain in two sentences why neural networks are useful for recognizing handwritten digits.
```

**Expected behavior:** two clean coherent sentences about pattern recognition,
hierarchical features. Streams in ~20 s. Bridges directly into Act I's MNIST demo.

### 1B. Mathematical heritage (safe, dry)

```
What is the Pythagorean theorem? State it precisely and give one short sentence about why it matters.
```

**Expected:** clean statement + one-sentence "fundamental for geometry/distance."
~20 s. Nice if a math-history framing feels right in the moment.

### 1C. Continuation — model surprises you

```
Complete this sentence in an interesting way: The most beautiful equation in mathematics is
```

**Expected:** the model picked **Navier–Stokes** in testing (!) — *not* the
conventional Euler's identity. A genuinely surprising, very flowery answer. ~30 s.
Use this if you want the audience to chuckle and lean in. Risk: longer output, the
content may not be the conventional answer (which is itself the talking point).

### ✂️ Cut if behind schedule

Skip Activity Monitor reveal (saves ~45 s). Just point at the laptop and say
"this model is *on this disk* — not a network call."

---

## ⛔ Do **not** type these (tested, known failure modes)

| Prompt                                                              | Why avoid                                                                                              |
|---------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|
| `Find lim_{n→∞} (1+1/n)^n and explain.`                             | Llama 3.2 mangles the L'Hôpital step and declares the limit is **infinity**. A math audience will notice. |
| `If a cat has 4 legs and a dog has 4 legs, how many legs does a spider have?` | The instruction-tuning RLHF flags this as a "trick question" and refuses to commit. Funny but kills the demo. |
| `cat -> 4\ndog -> 4\nspider -> ` *(symbolic notation)*               | Llama 3.2 sometimes **hallucinates a different pattern** (e.g., "counting vowels: spider → 2"). Brittle. |

---

## 2. Act III callback — ICL prompts  (t ≈ 48:00 – 51:00)

After Act III's GPT-2 notebook demo, you cmd-tab back to **the terminal** and run
the same three probes against Llama 3.2. The punchline: GPT-2 failed on these,
Llama (25× the parameters) succeeds. *That's what scaling buys you.*

Use **plain-sentence phrasing** — the symbolic `x -> y` notation is brittle on the
3B model.

### 2A. Spider legs (GPT-2 said gibberish)

```
A cat has 4 legs. A dog has 4 legs. A spider has 
```

**Expected:** `8 legs.` (confirmed across 3 independent runs). May add a sentence
like "Most spiders have eight legs, although…"

### 2B. Capitals (GPT-2 said "Madrid", wrong)

```
The capital of Spain is Madrid. The capital of France is Paris. The capital of Mexico is 
```

**Expected:** `Mexico City.` (confirmed across 3 runs). The audience — *in Mexico
City's metropolitan area* — will appreciate.

### 2C. Opposites (GPT-2 already got this right; use to bookend the comparison)

```
hot : cold
big : small
day : 
```

**Expected:** `night.` plus a brief explanation of antonyms. This one is the
**control**: even GPT-2 nailed it. Use it to set the baseline ("both models can
do *easy* patterns") before moving to 2A/2B ("but only the bigger model can do
the *harder* ones").

**Speaker line:** *"Same architecture. Same operation. 25× more parameters and a
few hundred times more training data. That's what scaling buys you."*

---

## 3. Troubleshooting

| If…                                          | Then…                                                                                          |
|----------------------------------------------|------------------------------------------------------------------------------------------------|
| Ollama daemon not running                    | `ollama serve &` in a separate terminal; retry                                                 |
| `llama3.2` missing                           | `ollama pull llama3.2` (needs WiFi; ~2 GB)                                                     |
| Model rambles past ~30 s                     | Hit `Ctrl-C` to interrupt; "I'll let it think; meanwhile…" then move on                        |
| First response is empty                      | The 0-token warmup happens sometimes. Re-send the prompt — the second one streams fine.        |
| Output is gibberish / weird tokens           | Restart: `Ctrl-D` to exit, then `ollama run llama3.2` again                                    |
| WiFi/everything broken                       | Skip the ICL callback entirely; instead, say "the same three prompts on a real LLM produce…" and show a screenshot in slides (TODO: prep this screenshot if you have time) |

---

## 4. Quick reference card (print or memorize)

```
OPENING:
  Explain in two sentences why neural networks are useful for recognizing handwritten digits.

ICL CALLBACK:
  A cat has 4 legs. A dog has 4 legs. A spider has 
  The capital of Spain is Madrid. The capital of France is Paris. The capital of Mexico is 
  hot : cold
  big : small
  day : 
```
