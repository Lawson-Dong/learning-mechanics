# Learning Mechanics

This repository contains computational experiments for studying deep-learning training as a discrete dynamical system from an analytical-mechanics perspective.

## Overview

The project investigates optimizer dynamics by treating neural-network parameters as the state of a high-dimensional dynamical system. The experiments include:

- mechanical fitting of optimizer trajectories for SGD, momentum SGD, and Adam;
- a learning Reynolds number (Re) based on discrete velocity and acceleration;
- overfitting dynamics and the relationship between Re and training behavior;
- GPT-2 experiments at small, medium, and large scales;
- analysis of optimizer schedules and parameter trajectories.

## Experiments

| Experiment | Notebook | Description |
|---|---|---|
| Mechanical fitting | experiments/01_mechanical_fitting/fitting.ipynb | Fits a mechanical description to optimizer parameter trajectories. |
| Learning Reynolds number | experiments/02_reynolds_number/Re.ipynb | Computes and analyzes the learning Reynolds number and its dynamics. |
| GPT-2 Small | experiments/04_gpt2_small/ | GPT-2 training and trajectory/Re analysis on WikiText-2. |
| GPT-2 Medium | experiments/05_gpt2_medium/ | GPT-2-medium experiments with TinyStories and learning-rate schedules. |
| GPT-2 Large | experiments/06_gpt2_large/ | GPT-2-large + LoRA experiments on CodeAlpaca-20K. |

## Reproducibility

The classical experiments are designed to run with standard scientific Python packages. The GPT-2 experiments additionally require the Hugging Face ecosystem and, for the large-model experiment, PEFT/LoRA-related dependencies.

Large training outputs and generated .npz/checkpoint artifacts are intentionally kept separate from the source notebooks.

## Related work

The repository accompanies work on a discrete analytical-mechanics framework for deep-learning optimizers.

## License

License information will be added when the project license is finalized.
