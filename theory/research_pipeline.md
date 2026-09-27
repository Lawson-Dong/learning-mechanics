# Research pipeline

This repository is organized around a progression from controlled optimizer dynamics to larger language-model experiments.

## 1. Mechanical identification of optimizer dynamics

**Notebook:** `experiments/01_mechanical_fitting/fitting.ipynb`

The first experiment records neural-network parameter trajectories and gradients for SGD, momentum SGD, and Adam. The trajectory is then used to fit mechanical parameters such as mass and damping.

The purpose is to test whether the proposed discrete mechanical equation reproduces the observed optimizer dynamics.

The paper reports that the fitted parameters for SGD and momentum SGD agree closely with their theoretical mappings, while Adam requires a time-varying interpretation because of its adaptive mechanism.

## 2. Learning Reynolds number

**Notebook:** `experiments/02_reynolds_number/Re.ipynb`

The next experiment constructs a dimensionless diagnostic from discrete parameter velocity and acceleration,

```
Re_k = ||a_k|| / (||v_k|| + epsilon).
```

The notebook studies its behavior under learning-rate sweeps and during prolonged training.

The associated analysis connects the growth of Re with the changing balance between parameter velocity and acceleration near the later stages of training.

## 3. Overfitting dynamics

The same Reynolds-number framework is then used to study the transition into overfitting.

The paper describes an Adam/MNIST experiment in which validation loss reaches a minimum and subsequently rises while Re enters a higher-fluctuation regime. In the paper's interpretation, the Re trajectory provides a dynamical signal associated with the loss of dissipative control preceding or accompanying degradation in validation performance.

The repository's `Re.ipynb` contains the corresponding analysis workflow.

## 4. Large-model dynamical response

The later notebooks extend the framework beyond the controlled MNIST/MLP experiments.

### GPT-2 Small

**Notebook:** `experiments/04_gpt2_small/GPT_2_small.ipynb`

GPT-2 small is trained on WikiText-2 and trajectory data are recorded for subsequent Re analysis.

### GPT-2 Medium

**Notebooks:**
- `experiments/05_gpt2_medium/GPT_2_medium.ipynb`
- `experiments/05_gpt2_medium/GPT_2_medium_cosine_data_analysis.ipynb`

GPT-2-medium is trained on TinyStories under different learning-rate schedules. The analysis notebook focuses on the cosine-restart results.

### GPT-2 Large

**Notebooks:**
- `experiments/06_gpt2_large/GPT_2_large.ipynb`
- `experiments/06_gpt2_large/GPT_2_large_data_analysis.ipynb`

GPT-2-large is fine-tuned with LoRA/PEFT on CodeAlpaca-20K. The experiment records trajectory-related quantities and analyzes the response to aggressive learning-rate changes.

## Conceptual flow

```text
optimizer update rules
        |
        v
parameter trajectory theta_k
        |
        +--------------------+
        |                    |
        v                    v
velocity v_k          acceleration a_k
        |                    |
        +---------+----------+
                  |
                  v
          Learning Reynolds
              number Re_k
                  |
                  v
       dynamical-state diagnostics
                  |
        +---------+---------+
        |                   |
        v                   v
   overfitting       scheduler response
        |                   |
        +---------+---------+
                  |
                  v
          larger-model tests
       GPT-2 Small / Medium / Large
```

## Scope and interpretation

The notebooks are experimental research artifacts rather than a single software package. Some experiments share definitions and physical quantities but differ in model, dataset, optimizer configuration, scheduler, and output format.

Generated trajectory files, checkpoints, and compressed experiment archives are therefore treated as experiment outputs rather than source code. They should be regenerated or obtained from an explicitly documented data source when exact numerical reproduction is required.
