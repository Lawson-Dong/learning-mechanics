# GPT-2 Medium

This experiment studies GPT-2-medium training on TinyStories under different learning-rate schedules.

## Notebooks

- `GPT_2_medium.ipynb` — training experiments.
- `GPT_2_medium_cosine_data_analysis.ipynb` — downstream analysis of cosine-restart results.

The training notebook includes Adam with cosine annealing warm restarts and a linear-decay schedule.

## Dependencies

```bash
pip install -r ../../requirements/gpt2.txt
```

Training requires internet access and a suitable PyTorch environment. Large generated archives and model artifacts are not committed to Git.
