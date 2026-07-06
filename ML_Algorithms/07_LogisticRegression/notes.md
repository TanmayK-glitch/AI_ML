# Perceptron Trick (Short Notes)

## Core Idea
The **Perceptron Trick** is a simple learning rule:

> If the model makes a wrong prediction, adjust the weights slightly so the correct prediction becomes more likely.

---

## How It Works

1. Start with **random weights**.
2. Make a prediction.
3. Compare it with the actual label.
4. If the prediction is wrong:
   - Update the weights.
   - The decision boundary (line) moves.
5. Repeat until the model learns a good boundary.

---

## Key Points

- **Weights control the decision boundary.**
- Changing the **weights** moves or rotates the boundary.
- The model learns by **reducing prediction errors**.
- Labels (e.g., Cat = 0, Dog = 1) are provided in the training data.
- The model **does not know what a cat or dog is**; it only learns patterns from the features.

---

## Logistic Regression vs Perceptron

| Perceptron | Logistic Regression |
|------------|---------------------|
| Predicts 0 or 1 directly | Predicts a probability (0–1) |
| Updates weights only on mistakes | Updates weights based on **how wrong** the prediction is |
| Hard decision boundary | Smooth probability-based learning |

---

## One-Line Summary

> **Perceptron Trick:** Move the decision boundary by updating the weights whenever the model makes a wrong prediction.

> -------------------------------------------------------------------------------------------------------------------------------

# Sigmoid Function (Logistic Regression)

## Definition
The **Sigmoid (Logistic) Function** converts a linear score into a **probability** between **0 and 1**, making it ideal for binary classification.

## Formula

\[
\sigma(z)=\frac{1}{1+e^{-z}}
\]

where,

\[
z=w^Tx+b
\]

- \(w\): Weights
- \(x\): Features
- \(b\): Bias

---

## Workflow

```text
Features (x)
     │
     ▼
z = wᵀx + b
     │
     ▼
Sigmoid σ(z)
     │
     ▼
Probability (0–1)
     │
     ▼
Threshold (0.5)
     │
     ▼
Class 0 or Class 1
```

---

## Output Interpretation

| z | σ(z) |
|---|------|
| Large Negative | ≈ 0 |
| 0 | 0.5 |
| Large Positive | ≈ 1 |

---

## Why Sigmoid?

- Converts any real value into a probability.
- Smooth & differentiable (supports gradient descent).
- Used for **binary classification**.

---

## Decision Rule

- **P ≥ 0.5** → Class 1
- **P < 0.5** → Class 0

---

## Key Idea

- Linear model computes **score**:
  \[
  z=w^Tx+b
  \]
- Sigmoid converts the score into **probability**.

---

## Log-Odds

Logistic Regression assumes:

\[
\log\left(\frac{p}{1-p}\right)=w^Tx+b
\]

> **Log-odds are linear, not the probability.**

---

## Pros

- Probability output (0–1)
- Easy to interpret
- Works well with Binary Cross-Entropy Loss

---

## Limitations

- Suffers from **vanishing gradients** for very large \(|z|\).
- Logistic Regression still has a **linear decision boundary**.

---

## Quick Revision

- **Function:** Converts score → probability
- **Range:** (0, 1)
- **Formula:** \(\sigma(z)=\frac{1}{1+e^{-z}}\)
- **Threshold:** 0.5 (default)
- **Decision Boundary:** \(w^Tx+b=0\)
- **Use:** Binary Classification