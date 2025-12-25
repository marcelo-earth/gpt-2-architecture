# Introduction to Positional Encoding

Let's go from the start. We have an input.

"Hello, how are you?"

This in **Input Embedding** is transformed into a vector of numbers.

```
[0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9]
[0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9]
[0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9]
```

Now, so far with recurrent neural networks, we have been able to capture the order of the words because we have been able to pass the previous word to the next one.

But with **transformers**, we need to capture the order of the words without having to pass the previous word to the next one.

Now, we may think, OK. Let's add the position of the word to the embedding.

```
[0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9, 1.0]
[0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9, 2.0]
[0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9, 3.0]
```

That was a good idea, but it's not enough.

If there are like 200 words in the sentence, we would need to add 200 positions to the embedding. And that decreases the value of the embedding. OK. So we can think, on maybe divide that position value by 200 position, like normalizing it.

This works if we codified in a fixed way, but if we have a longer sentence, we have a problem again. The value behind it doesn't make sense anymore.

**OK, let's try binary coding.**

Now, if we use binary coding, that's so much better!, We don't have large values, and we provide information about the position in a very elegant way.

**What is RoPE (Rotary Position Embedding)?**

Indicate the **ORDER** of the words

**Problem:** Without position, the model doesn't know the order
"The cat chases the dog" ≠ "The dog chases the cat"

**Solution:** ROTATE the embedding according to the position
"cat" in position 0: [0.8, 0.3]   (no rotation)
"cat" in position 1: [0.77, 0.38] (rotated 10°)
"cat" in position 2: [0.72, 0.45] (rotated 20°)
