# Lesson 06 — Deep learning theory ("under the hood")

**Time:** 3 weeks (~25 hours)  
**Prerequisite:** [Lesson 05](05-ml-foundations.md)  
**Job alignment:** Layer details, loss functions, optimization

## Learning objectives

- Perceptron → multi-layer network
- Activations, forward pass
- Loss functions (MSE, cross-entropy)
- SGD, Adam, learning rates
- Backpropagation intuition

## 1. Neuron

\[
y = \sigma\left(\sum_i w_i x_i + b\right)
\]

- \(x_i\): inputs (sensor features, pixels)
- \(w_i, b\): learnable parameters
- \(\sigma\): activation (ReLU, sigmoid, softmax)

## 2. Common activations

| Activation | Use |
|------------|-----|
| ReLU | Hidden layers in CNNs/MLPs |
| Sigmoid | Binary output |
| Softmax | Multi-class output |
| GELU | Transformers |

## 3. Loss functions

**Regression (MSE):**

\[
L = \frac{1}{n}\sum_i (\hat{y}_i - y_i)^2
\]

**Classification (cross-entropy):**

\[
L = -\sum_i y_i \log(\hat{y}_i)
\]

## 4. Optimization

Gradient descent update:

\[
w \leftarrow w - \eta \frac{\partial L}{\partial w}
\]

- \(\eta\) = learning rate
- **Adam** adapts per-parameter learning rates (default in many repos)

## 5. Backprop (intuition)

1. Forward pass computes prediction and loss
2. Backward pass applies chain rule to get \(\partial L / \partial w\)
3. Optimizer updates weights

PyTorch computes this automatically with `loss.backward()`.

## 6. Batch normalization, dropout (brief)

- **BatchNorm** — stabilizes training
- **Dropout** — random neuron dropout; reduces overfitting

## 7. Manual tiny network in NumPy (optional exercise)

Implement 2-layer MLP on XOR or small regression — then appreciate PyTorch.

## Readings

- [3Blue1Brown — Neural networks](https://www.youtube.com/watch?v=aircAruvnKk)
- [Michael Nielsen — Neural Networks and Deep Learning](http://neuralnetworksanddeeplearning.com/) (Ch. 1–2)

## Exercises

1. Draw computational graph for \(L = (wx + b - y)^2\).
2. Experiment: high vs low learning rate on toy data (Lesson 7 code).
3. Explain why ReLU helps vs sigmoid in hidden layers (vanishing gradients).

**Next:** [Lesson 07 — PyTorch fundamentals](07-pytorch-fundamentals.md)
