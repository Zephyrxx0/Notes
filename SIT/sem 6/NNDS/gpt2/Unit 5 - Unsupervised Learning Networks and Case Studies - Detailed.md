# Unit 5 — Unsupervised Learning Networks and Case Studies - Detailed

## 1. Self-Organizing Feature Map

> [!important] Definition
> A Self-Organizing Map (SOM) is an unsupervised neural network that maps high-dimensional data to a low-dimensional grid while preserving topology.

```mermaid
flowchart LR
    A[High-dimensional data] --> B[SOM]
    B --> C[2D feature map]
```

---

## 2. SOM Structure

A SOM has:
1. Input layer
2. Output grid
3. Weight vector for each neuron

If input is:

$$
x=[x_1,x_2,\dots,x_n]
$$

Each neuron has:

$$
w_j=[w_{j1},w_{j2},\dots,w_{jn}]
$$

---

## 3. Best Matching Unit

> [!important] Definition
> BMU is the neuron whose weight vector is closest to the input vector.

$$
BMU=\arg\min_j||x-w_j||
$$

---

## 4. SOM Training

```mermaid
flowchart TD
    A[Initialize weights] --> B[Present input]
    B --> C[Find BMU]
    C --> D[Update BMU]
    D --> E[Update neighbours]
    E --> F[Reduce learning rate and neighbourhood]
```

Update:

$$
w_j(t+1)=w_j(t)+\eta(t)h_{cj}(t)[x-w_j(t)]
$$

---

## 5. Topology and Neighbourhood

Topology defines arrangement of neurons:
- Rectangular
- Hexagonal
- Linear

Gaussian neighbourhood:

$$
h_{cj}(t)=\exp\left(-\frac{d_{cj}^2}{2\sigma^2(t)}\right)
$$

Early training:
- Large neighbourhood
- High learning rate

Late training:
- Small neighbourhood
- Low learning rate

---

## 6. Cluster Analysis

> [!important] Definition
> Cluster analysis groups similar data points together without predefined class labels.

Good clusters have:
- High similarity within cluster
- Low similarity between clusters

```mermaid
flowchart TD
    A[Unlabelled data] --> B[Similarity measure]
    B --> C[Cluster 1]
    B --> D[Cluster 2]
    B --> E[Cluster 3]
```

---

## 7. Probabilistic Neural Network

> [!important] Definition
> PNN is a supervised classification network based on probability density estimation and Bayes decision theory.

Architecture:

```mermaid
flowchart LR
    A[Input] --> B[Pattern Layer]
    B --> C[Summation Layer]
    C --> D[Decision Layer]
```

Gaussian pattern function:

$$
\phi_i(x)=\exp\left(-\frac{||x-x_i||^2}{2\sigma^2}\right)
$$

Decision:

$$
Class(x)=\arg\max_kP(C_k|x)
$$

---

## 8. PNN for Image Pattern Detection

Pipeline:

```mermaid
flowchart TD
    A[Image dataset] --> B[Preprocessing]
    B --> C[Feature extraction]
    C --> D[PNN similarity calculation]
    D --> E[Class probability]
    E --> F[Detected pattern]
```

Advantages:
- Fast training
- Probabilistic output
- Useful for classification

Limitations:
- Large memory
- Slow prediction for large data
- Sensitive to spread parameter

---

## 9. Adaptive Resonance Theory

> [!important] Definition
> ART is a neural network model that learns new patterns without forgetting old patterns.

### Stability-plasticity dilemma

| Term | Meaning |
|---|---|
| Stability | Keep old knowledge |
| Plasticity | Learn new information |
| Dilemma | New learning can overwrite old learning |

---

## 10. ART Structure

```mermaid
flowchart LR
    A[F1 Input/Comparison Layer] -->|Bottom-up| B[F2 Category Layer]
    B -->|Top-down| A
    C[Vigilance ρ] --> A
```

Vigilance:

$$
0\leq \rho \leq 1
$$

High vigilance:
- strict matching
- more categories

Low vigilance:
- loose matching
- fewer categories

---

## 11. ART Learning Process

```mermaid
flowchart TD
    A[Input pattern] --> B[Choose best category]
    B --> C{Vigilance test passes?}
    C -->|Yes| D[Resonance and update]
    C -->|No| E[Reset and search next]
    E --> B
    C -->|No category| F[Create new category]
```

---

## 12. ART Variants

| Model | Input |
|---|---|
| ART1 | Binary patterns |
| ART2 | Continuous/analog patterns |
| ART3 | More biologically inspired |

---

## 13. RBFNN Medical Imaging Case Study

```mermaid
flowchart TD
    A[Medical images] --> B[Preprocessing]
    B --> C[Feature extraction]
    C --> D[Select RBF centers]
    D --> E[Calculate RBF activations]
    E --> F[Train output layer]
    F --> G[Normal / abnormal detection]
```

RBFNN is useful because centers act as prototypes of visual patterns.

---

## 14. Solved Example — SOM BMU

### Final Answer

$$
BMU=w_1
$$

### Problem

$$
x=[1,2],\quad w_1=[1,1],\quad w_2=[4,5]
$$

### Steps

$$
d_1=\sqrt{(1-1)^2+(2-1)^2}=1
$$

$$
d_2=\sqrt{(1-4)^2+(2-5)^2}=4.24
$$

Since $d_1<d_2$, BMU is $w_1$.
