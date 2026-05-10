# Backpropagation Numericals - Final Answer First

## Core Formulas

$$
f(x)=\frac{1}{1+e^{-x}}
$$

$$
f'(x)=f(x)(1-f(x))
$$

$$
E=\frac{1}{2}(t-y)^2
$$

$$
\delta_o=(t-y)y(1-y)
$$

$$
\delta_h=h(1-h)\sum_o\delta_ov_{ho}
$$

$$
w_{new}=w_{old}+\eta\delta(input)
$$

$$
b_{new}=b_{old}+\eta\delta
$$

---

# Q1. Single Output Neuron

## Final Answer

$$
y=0.6225,\quad \delta=0.0887
$$

$$
w_1(new)=0.14435,\quad w_2(new)=0.28870
$$

## Problem

$$
x_1=1,\quad x_2=2
$$

$$
w_1=0.1,\quad w_2=0.2,\quad b=0
$$

$$
t=1,\quad \eta=0.5
$$

Activation: sigmoid.

## Steps

$$
net=(0.1)(1)+(0.2)(2)=0.5
$$

$$
y=\frac{1}{1+e^{-0.5}}=0.6225
$$

$$
\delta=(1-0.6225)(0.6225)(1-0.6225)=0.0887
$$

$$
\Delta w_1=0.5(0.0887)(1)=0.04435
$$

$$
\Delta w_2=0.5(0.0887)(2)=0.08870
$$

$$
w_1(new)=0.1+0.04435=0.14435
$$

$$
w_2(new)=0.2+0.08870=0.28870
$$

---

# Q2. Output Neuron with Bias

## Final Answer

$$
y=0.7109,\quad \delta=-0.1462
$$

$$
w_1(new)=0.1269,\quad w_2(new)=-0.26345,\quad b(new)=0.16345
$$

## Problem

$$
x_1=2,\quad x_2=-1
$$

$$
w_1=0.2,\quad w_2=-0.3,\quad b=0.2
$$

$$
t=0,\quad \eta=0.25
$$

Activation: sigmoid.

## Steps

$$
net=(0.2)(2)+(-0.3)(-1)+0.2=0.9
$$

$$
y=\frac{1}{1+e^{-0.9}}=0.7109
$$

$$
\delta=(0-0.7109)(0.7109)(1-0.7109)=-0.1462
$$

$$
\Delta w_1=0.25(-0.1462)(2)=-0.0731
$$

$$
\Delta w_2=0.25(-0.1462)(-1)=0.03655
$$

$$
\Delta b=0.25(-0.1462)=-0.03655
$$

$$
w_1(new)=0.2-0.0731=0.1269
$$

$$
w_2(new)=-0.3+0.03655=-0.26345
$$

$$
b(new)=0.2-0.03655=0.16345
$$

---

# Q3. One Hidden Neuron and One Output Neuron

## Final Answer

$$
h=0.5,\quad y=0.5866
$$

$$
\delta_o=0.1003,\quad \delta_h=0.00752
$$

$$
v(new)=0.31003
$$

$$
w_1(new)=0.10150,\quad w_2(new)=0.19850
$$

## Problem

$$
x_1=1,\quad x_2=-1
$$

Input-to-hidden:

$$
w_1=0.1,\quad w_2=0.2,\quad b_h=0.1
$$

Hidden-to-output:

$$
v=0.3,\quad b_o=0.2
$$

$$
t=1,\quad \eta=0.2
$$

Activation: sigmoid.

## Steps

Hidden net:

$$
net_h=(0.1)(1)+(0.2)(-1)+0.1=0
$$

Hidden output:

$$
h=\frac{1}{1+e^0}=0.5
$$

Output net:

$$
net_o=(0.3)(0.5)+0.2=0.35
$$

Output:

$$
y=\frac{1}{1+e^{-0.35}}=0.5866
$$

Output delta:

$$
\delta_o=(1-0.5866)(0.5866)(1-0.5866)=0.1003
$$

Hidden delta:

$$
\delta_h=0.5(1-0.5)(0.1003)(0.3)=0.00752
$$

Update output weight:

$$
\Delta v=0.2(0.1003)(0.5)=0.01003
$$

$$
v(new)=0.3+0.01003=0.31003
$$

Update hidden weights:

$$
\Delta w_1=0.2(0.00752)(1)=0.00150
$$

$$
w_1(new)=0.1+0.00150=0.10150
$$

$$
\Delta w_2=0.2(0.00752)(-1)=-0.00150
$$

$$
w_2(new)=0.2-0.00150=0.19850
$$

---

# Q4. Backpropagation with Momentum

## Final Answer

$$
\Delta w(t)=0.055,\quad w(new)=0.455
$$

## Problem

$$
\eta=0.5,\quad \delta=0.1,\quad x=1
$$

$$
\alpha=0.25,\quad \Delta w(t-1)=0.02,\quad w=0.4
$$

## Steps

$$
\Delta w(t)=\eta\delta x+\alpha\Delta w(t-1)
$$

$$
\Delta w(t)=0.5(0.1)(1)+0.25(0.02)
$$

$$
\Delta w(t)=0.05+0.005=0.055
$$

$$
w(new)=0.4+0.055=0.455
$$

---

# Q5. Error Calculation

## Final Answer

$$
E=0.045
$$

## Problem

$$
y=0.7,\quad t=1
$$

## Steps

$$
E=\frac{1}{2}(t-y)^2
$$

$$
E=\frac{1}{2}(1-0.7)^2
$$

$$
E=0.045
$$

---

# Q6. Hidden Delta with Two Output Neurons

## Final Answer

$$
\delta_h=0.0144
$$

## Problem

$$
h=0.6
$$

$$
\delta_1=0.1,\quad \delta_2=-0.05
$$

$$
v_1=0.5,\quad v_2=-0.2
$$

## Steps

$$
\delta_h=h(1-h)(\delta_1v_1+\delta_2v_2)
$$

$$
\delta_h=0.6(0.4)[(0.1)(0.5)+(-0.05)(-0.2)]
$$

$$
\delta_h=0.24(0.05+0.01)
$$

$$
\delta_h=0.0144
$$

---

# Q7. Bias Update

## Final Answer

$$
b(new)=0.26
$$

## Problem

$$
b=0.2,\quad \eta=0.3,\quad \delta=0.2
$$

## Steps

$$
b(new)=b+\eta\delta
$$

$$
b(new)=0.2+0.3(0.2)=0.26
$$

---

# Common Mistakes

| Mistake | Correction |
|---|---|
| Using $net(1-net)$ for sigmoid derivative | Use $y(1-y)$ |
| Giving target to hidden neuron | Hidden delta comes from next layer |
| Forgetting bias update | Use $b_{new}=b+\eta\delta$ |
| Wrong sign | Be consistent with $(t-y)$ and plus update |
