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
