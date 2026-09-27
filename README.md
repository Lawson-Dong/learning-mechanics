# Learning Mechanics

This repository contains computational experiments for studying deep-learning training as a discrete dynamical system from an analytical-mechanics perspective.

## Overview

The project investigates optimizer dynamics by treating neural-network parameters as the state of a high-dimensional dynamical system. The current experiments include:

- mechanical fitting of optimizer trajectories for SGD, momentum SGD, and Adam;
- a learning Reynolds number (Re) based on discrete velocity and acceleration;
- training/overfitting dynamics and the relationship between Re and validation behavior;
- GPT-2 experiments at small, medium, and large scales;
- analysis of optimizer schedules and parameter trajectories.

## Repository structure

```text
learning-mechanics/
├── README.md
├── requirements.txt
├── requirements/
│   ├── base.txt
│   ├── classical.txt
│   ├── gpt2.txt
│   └── gpt2-large.txt
├── data/
│   └── README.md
└── experiments/
    ├── 01_mechanical_fitting/
    │   ├── README.md
    │   └── fitting.ipynb
    ├── 02_reynolds_number/
    │   ├── README.md
    │   └── Re.ipynb
    ├── 04_gpt2_small/
    │   ├── README.md
    │   └── GPT_2_small.ipynb
    ├── 05_gpt2_medium/
    │   ├── README.md
    │   ├── GPT_2_medium.ipynb
    │   └── GPT_2_medium_cosine_data_analysis.ipynb
    └── 06_gpt2_large/
        ├── README.md
        ├── GPT_2_large.ipynb
        └── GPT_2_large_data_analysis.ipynb
```

The experiment numbering follows the current notebook collection; it is not intended to imply that every intermediate experiment is already present in this repository.

## Experiments

| Experiment | Notebook(s) | Description |
|---|---|---|
| Mechanical fitting | `experiments/01_mechanical_fitting/fitting.ipynb` | Fits a mechanical description to optimizer parameter trajectories from controlled synthetic experiments. |
| Learning Reynolds number | `experiments/02_reynolds_number/Re.ipynb` | Computes and analyzes a discrete learning Reynolds number using parameter velocity and acceleration. |
| GPT-2 Small | `experiments/04_gpt2_small/GPT_2_small.ipynb` | GPT-2 training and trajectory/Re analysis on WikiText-2. |
| GPT-2 Medium | `experiments/05_gpt2_medium/GPT_2_medium.ipynb` | GPT-2-medium experiments on TinyStories with different learning-rate schedules. |
| GPT-2 Medium analysis | `experiments/05_gpt2_medium/GPT_2_medium_cosine_data_analysis.ipynb` | Downstream analysis of the GPT-2-medium cosine-restart results. |
| GPT-2 Large | `experiments/06_gpt2_large/GPT_2_large.ipynb` | GPT-2-large + LoRA/PEFT experiments on CodeAlpaca-20K. |
| GPT-2 Large analysis | `experiments/06_gpt2_large/GPT_2_large_data_analysis.ipynb` | Downstream analysis of the GPT-2-large experiment results. |

Each experiment directory contains a short README describing its notebook(s), dependencies, and expected data flow.

## Research pipeline

A more detailed description of how the experiments connect is available in [`theory/research_pipeline.md`](theory/research_pipeline.md). The core discrete quantities are summarized in [`theory/equations.md`](theory/equations.md).

The current repository extends the original controlled experiments with GPT-2 Small, Medium, and Large studies. These later notebooks should be viewed as extensions of the same dynamical framework rather than as interchangeable reproductions of the earlier experiments.

## Reproducibility

### Classical experiments

For the first two experiments:

```bash
pip install -r requirements/classical.txt
```

These experiments are self-contained and do not require external datasets or model downloads.

### GPT-2 experiments

For GPT-2 Small and Medium:

```bash
pip install -r requirements/gpt2.txt
```

For GPT-2 Large:

```bash
pip install -r requirements/gpt2-large.txt
```

The GPT-2 experiments use the Hugging Face ecosystem and require internet access. GPT-2 Large additionally uses PEFT/LoRA-related packages and requires substantially more compute.

The notebooks may contain environment-specific cells inherited from their original experimental workflow (for example, Google Colab utilities). They should therefore be treated as research notebooks rather than polished standalone Python packages.

## Data and generated artifacts

Large generated artifacts are intentionally not committed to Git. This includes:

- model checkpoints;
- `.npz`, `.npy`, and pickle experiment outputs;
- compressed experiment archives;
- generated model-weight files;
- large intermediate training artifacts.

See [`data/README.md`](data/README.md) and the README inside each experiment directory for the expected inputs and outputs.

## Related work

The repository accompanies work on a discrete analytical-mechanics framework for deep-learning optimizers.

## License

License information will be added when the project license is finalized.
