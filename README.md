# GPT-2-Replication Model

Now with Pytorch and CUDA

Let's start with the basics, from this very simple equation:

```
output = (weight × input) + bias
```

This equation is the core of a perceptron, a simple artificial neuron that can be used to solve problems like classification and regression.

## My Questions & Answers

**How do we know, during training, that the model has reached a local minimum? Gradient descent is often described as a way to find the lowest point in a landscape of hills, but what happens if different people train the same neural network? Could it be that one of them ends up “better positioned” simply because their starting point led them to a much lower region than the others?**

1. We do "know" local minimum only if:
- _Loss function suddenly drops_
- Gradient is close to 0
- Model starts overfitting

2. The initial point matters a lot

3. Local minimums are not "bad"

**Is Adam better than SGD? It looks like it is, but I think I'm missing something.**

Adam converges faster than SGD.

But SGD can be better only in giant models...

- **My small example (y = w*x + b):** 2 parameters → Trained in milliseconds
- **Medium model:** ~100,000 - 1,000,000 parameters → Trained in hours
- **Large model:** ~25,000,000 parameters (ResNet-50) → Trained in days
- **Giant model:** ~175,000,000,000 parameters (GPT-3) → Trained for $4.6 million

You can also get better results with SGD by tuning the hyperparameters.

Tuning is testing different values for the hyperparameters to find the best one.

**With Adam (easy):**

```python
optimizer = Adam(lr=0.001)  # Works 80% of the time
```

→ Test 2-3 values of lr → 1 day of experiments

**With SGD (difficult):**

You need to test many combinations:
Try 1: SGD(lr=0.1, momentum=0.9)    → 85% accuracy
Try 2: SGD(lr=0.01, momentum=0.9)   → 88% accuracy 
Try 3: SGD(lr=0.1, momentum=0.95)   → 87% accuracy
Try 4: SGD(lr=0.1, momentum=0.9) + scheduling → 90% accuracy ✓
→ Test 10-20 combinations → 1-2 weeks of experiments



