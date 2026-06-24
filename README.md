## **The Algebra of Learning**

> Neural networks, derived from scratch. No hand-waving, no "trust me," no magic — just linear algebra and calculus, built one piece at a time until you can read a transformer paper without losing the thread.

A five-part tutorial series that builds a neural network from a single neuron all the way to a production-ready, regularized, cross-validated model — deriving every gradient by hand, then proving the maths matches TensorFlow and PyTorch to floating-point precision.

If most tutorials show you the frameworks and tell you the maths is too hard to derive, this series does the opposite: it derives the maths, then shows you the frameworks are just convenient packaging on top of it.

---

### **Why this series exists**

Neural networks sound terrifying from a distance — backpropagation, gradient descent, activation functions, optimizers, loss landscapes. They sound like research-lab magic.

They are not. At their core, **every** neural network does five things:

1. Make a prediction.
2. Measure how wrong it was.
3. Figure out which knobs caused the error.
4. Nudge those knobs slightly.
5. Repeat.

That's the whole algorithm. The work — and the fun — is making each of those five steps mathematically precise. That's what this series does, with a deliberately tiny toy dataset so you can see every gear turn.

Every claim is derived. Every line of code runs. Every number in the text is a real output you can reproduce.

---

### **The series**

| # | Part | What you'll learn |
|---|------|-------------------|
| 1 | [Inside the Neuron](1-the-algebra-of-learning-part-1-inside-the-neuron.md) | The static architecture — neurons, layers, weighted sums, why nonlinearity is non-negotiable (with a three-line proof), ReLU, He initialization, and feature standardization. |
| 2 | [How a Network Actually Learns](2-the-algebra-of-learning-part-2-how-a-network-learns.md) | Backpropagation, derived from scratch. The loss function, gradient descent, the chain rule worked by hand, the dead-ReLU problem, and an autograd parity check against PyTorch. |
| 3 | [Adam, Frameworks & the Question of Tomorrow](3-the-algebra-of-learning-part-3-adam-and-frameworks.md) | The Adam optimizer derived in four equations, a fair SGD-vs-Adam race on real data, and the same network rebuilt in TensorFlow and PyTorch — all three producing identical numbers. |
| 4 | [Can It Actually Generalize? (Theory & Diagnosis)](4-the-algebra-of-learning-part-4-can-it-generalize.md) | Generalization, the train/validation split done right, overfitting watched in real time, the bias–variance tradeoff, and the validation curve. |
| 5 | [Treatments for Overfitting](5-the-algebra-of-learning-part-5-treatments-for-overfitting.md) | Early stopping, L2 / weight decay, dropout, and k-fold cross-validation — each derived, implemented in NumPy, and verified in TensorFlow and PyTorch. Plus how this scales to billion-parameter systems. |

**Recommended order:** read them 1 → 2 → 3 → 4 → 5. Each part builds directly on the last.

---

### **What gets built**

A two-layer regression network (`3 → hidden → 1`) trained on a 100-day toy dataset, where the goal is to predict a daily score from three inputs (sleep hours, study minutes, and the previous day's score). The data is generated from a known rule plus Gaussian noise, so we can check whether the network actually recovers the rule it was never shown.

By the end you'll have, written from first principles:

- A single neuron and a fully-connected layer (NumPy)
- A complete forward and backward pass, with hand-derived gradients
- Plain gradient descent **and** a from-scratch Adam optimizer
- Early stopping, L2 regularization, and inverted dropout
- A 5-fold cross-validation harness
- The same model, three ways — NumPy, TensorFlow, PyTorch — proven to agree

---

### **Requirements**

- Python 3.9+
- `numpy`
- `pandas`
- `matplotlib`
- `torch` (Parts 2, 3, 5 — for the parity checks)
- `tensorflow` (Parts 3, 5 — for the parity checks)

Parts 1, 4, and the core of every other part run on NumPy / pandas / matplotlib alone. TensorFlow and PyTorch are only needed for the "does our hand-derived maths match the frameworks?" sections.

### **Install**

```bash
git clone https://github.com/<your-username>/the-algebra-of-learning.git
cd the-algebra-of-learning
pip install -r requirements.txt
```

A minimal `requirements.txt`:

```text
numpy
pandas
matplotlib
torch
tensorflow
```

---

### **Reproducibility**

Every figure and number in the series comes from a fixed seed (`np.random.seed(42)` plus explicit seeds in the class constructors). Run the code blocks **in order** and your outputs will match the text.

- The train/validation split is always made **before** standardization, so no information leaks from validation into training.
- Validation loss is only ever *observed* (and used for early stopping) — never used to compute gradients.
- The autograd parity checks agree with PyTorch to the float32 precision floor (~10⁻⁷); the framework training runs agree to three decimal places at every milestone.

---

### **How to use this repo**

Each part is a standalone Markdown document with runnable code blocks. You can:

- **Read top to bottom** like a blog post — the prose is written to stand on its own.
- **Copy the code blocks into a notebook** and run them in order to reproduce every result.
- **Use individual sections as reference** — the recap tables at the end of each part are quick refreshers on every concept introduced.

---

### **A note on the synthetic dataset**

The tutorials use a small, intuitive regression problem (predicting a score from sleep, study time, and a previous score) purely as a teaching device. It is a *controlled experiment*, not a model of any real person — the whole point is that we know the true rule, so we can check whether the network rediscovers it. The maths is what matters; the dataset just keeps it grounded in something concrete.

---

### **License**

Released under the MIT License. See [`LICENSE`](LICENSE) for details. Use it, fork it, teach from it.

---

### **Contributing**

Spotted an error in a derivation, a number that doesn't reproduce, or an explanation that could be clearer? Open an issue or a pull request. Corrections to the maths are especially welcome — the entire premise of the series is that every claim holds up.

---

*If you read all five parts carefully, you'll understand neural networks at a level most practitioners don't. A network with 41 parameters and one with hundreds of billions are the same algorithm — they differ in scale, not in kind. Use it well.*

**Originally Published** on **[blog](https://talkcodetome.com)**

---

**Link to Medium Article (The Algebra of Learning — Part 1: Inside the Neuron)**
*([Medium](https://medium.com/@cobena_i))*

**Link to Medium Article (The Algebra of Learning — Part 2: How a Network Actually Learns)**
*([Medium](https://medium.com/@cobena_i))*

**Link to Medium Article (The Algebra of Learning — Part 3: Adam, Frameworks, and the Question of Tomorrow)**
*([Medium](https://medium.com/@cobena_i))*

**Link to Medium Article (The Algebra of Learning — Part 4: Can It Actually Generalize? (Theory & Diagnosis))**
*([Medium](https://medium.com/@cobena_i))*

**Link to Medium Article (The Algebra of Learning — Part 5: Treatments for Overfitting)**
*([Medium](https://medium.com/@cobena_i))*
