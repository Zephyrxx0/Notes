# RBF Numericals - Final Answer First

## Core Formulas

$$
||x-c||=\sqrt{\sum_i(x_i-c_i)^2}
$$

$$
||x-c||^2=\sum_i(x_i-c_i)^2
$$

$$
\phi(x)=\exp\left(-\frac{||x-c||^2}{2\sigma^2}\right)
$$

$$
y=\sum_{i=1}^{m}w_i\phi_i+b
$$

$$
w_i(new)=w_i(old)+\eta(t-y)\phi_i
$$

$$
\sigma=\frac{d_{max}}{\sqrt{2m}}
$$

---

# Q1. Single RBF Activation

## Final Answer

$$
\phi(x)=0.535
$$

## Problem

$$
x=[2,3],\quad c=[1,1],\quad \sigma=2
$$

## Steps

$$
||x-c||^2=(2-1)^2+(3-1)^2=5
$$

$$
\phi(x)=\exp\left(-\frac{5}{2(2)^2}\right)
$$

$$
\phi(x)=\exp(-0.625)=0.535
$$

---

# Q2. RBF Output with Two Neurons

## Final Answer

$$
y=1.25
$$

## Problem

$$
\phi_1=0.8,\quad \phi_2=0.3
$$

$$
w_1=1.5,\quad w_2=-0.5,\quad b=0.2
$$

## Steps

$$
y=(1.5)(0.8)+(-0.5)(0.3)+0.2
$$

$$
y=1.2-0.15+0.2=1.25
$$

---

# Q3. One-dimensional RBF Activation

## Final Answer

$$
\phi(x)=0.8825
$$

## Problem

$$
x=3,\quad c=2,\quad \sigma=2
$$

## Steps

$$
||x-c||^2=(3-2)^2=1
$$

$$
\phi(x)=\exp\left(-\frac{1}{2(2)^2}\right)=\exp(-0.125)
$$

$$
\phi(x)=0.8825
$$

---

# Q4. Three-neuron RBF Output

## Final Answer

$$
y=0.89
$$

## Problem

$$
\phi_1=0.9,\quad \phi_2=0.4,\quad \phi_3=0.2
$$

$$
w_1=0.8,\quad w_2=0.5,\quad w_3=-0.4,\quad b=0.05
$$

## Steps

$$
y=(0.8)(0.9)+(0.5)(0.4)+(-0.4)(0.2)+0.05
$$

$$
y=0.72+0.20-0.08+0.05=0.89
$$

---

# Q5. Width Calculation

## Final Answer

$$
\sigma=2
$$

## Problem

$$
d_{max}=4,\quad m=2
$$

## Steps

$$
\sigma=\frac{d_{max}}{\sqrt{2m}}
$$

$$
\sigma=\frac{4}{\sqrt{2(2)}}=\frac{4}{2}=2
$$

---

# Q6. Output Weight Update

## Final Answer

$$
w_1(new)=0.532,\quad w_2(new)=-0.188
$$

## Problem

$$
w_1=0.5,\quad w_2=-0.2
$$

$$
\phi_1=0.8,\quad \phi_2=0.3
$$

$$
t=1,\quad y=0.6,\quad \eta=0.1
$$

## Steps

$$
t-y=1-0.6=0.4
$$

$$
\Delta w_1=0.1(0.4)(0.8)=0.032
$$

$$
w_1(new)=0.5+0.032=0.532
$$

$$
\Delta w_2=0.1(0.4)(0.3)=0.012
$$

$$
w_2(new)=-0.2+0.012=-0.188
$$

---

# Q7. Complete RBF Forward Pass

## Final Answer

$$
\phi_1=0.8825,\quad \phi_2=0.5353
$$

$$
y=0.9119
$$

## Problem

$$
x=[1,2]
$$

$$
c_1=[1,1],\quad c_2=[3,3]
$$

$$
\sigma=2
$$

$$
w_1=0.7,\quad w_2=0.4,\quad b=0.08
$$

## Steps

For first center:

$$
||x-c_1||^2=(1-1)^2+(2-1)^2=1
$$

$$
\phi_1=\exp\left(-\frac{1}{8}\right)=0.8825
$$

For second center:

$$
||x-c_2||^2=(1-3)^2+(2-3)^2=5
$$

$$
\phi_2=\exp\left(-\frac{5}{8}\right)=0.5353
$$

Output:

$$
y=(0.7)(0.8825)+(0.4)(0.5353)+0.08
$$

$$
y=0.61775+0.21412+0.08=0.9119
$$

---

# Q8. Normalized RBF

## Final Answer

$$
\hat{\phi}_1=0.6667,\quad \hat{\phi}_2=0.3333
$$

## Problem

$$
\phi_1=0.6,\quad \phi_2=0.3
$$

## Steps

$$
\phi_1+\phi_2=0.9
$$

$$
\hat{\phi}_1=\frac{0.6}{0.9}=0.6667
$$

$$
\hat{\phi}_2=\frac{0.3}{0.9}=0.3333
$$

---

# Q9. RBF Classification

## Final Answer

Class = 1

## Problem

$$
y=0.73
$$

Decision rule:

$$
Class=1 \text{ if } y\geq0.5
$$

## Steps

$$
0.73\geq0.5
$$

So predicted class is 1.

---

# Common Mistakes

| Mistake | Correction |
|---|---|
| Using distance instead of squared distance | Use $||x-c||^2$ in exponent |
| Forgetting $2\sigma^2$ | Denominator is always $2\sigma^2$ |
| Thinking far center gives high activation | Far center gives low activation |
| Forgetting output bias | Add $b$ in final output |
