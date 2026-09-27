# Core quantities

This file records the main discrete-dynamics quantities used throughout the experiments.

## Parameter state

Let `theta_k` denote the flattened neural-network parameter vector at training step `k`.

## Discrete velocity

```
v_k = theta_k - theta_{k-1}
```

## Discrete acceleration

```
a_k = v_{k+1} - v_k
```

## Learning Reynolds number

The experimental Reynolds-number diagnostic is defined as

```
Re_k = ||a_k|| / (||v_k|| + epsilon)
```

where `epsilon` is used to avoid division by zero.

## Mechanical equation

The paper formulates the optimizer dynamics through the discrete mechanical relation

```
m_{k+1} a_k + (m_{k+1} - m_k + gamma_k) v_k = -g_k
```

where `g_k` denotes the gradient and `m_k` and `gamma_k` are the effective mass and damping quantities.

The exact interpretation depends on the optimizer. In the paper's framework, SGD and momentum SGD correspond to constant/isotropic special cases, while Adam is interpreted using time-varying, coordinate-wise effective quantities.

## Important distinction

The equations in this document describe the conceptual and analytical framework. Individual notebooks may use simplified estimators, finite-difference conventions, smoothing, or experiment-specific normalizations. For exact reproduction of a figure or numerical result, use the implementation in the corresponding notebook.
