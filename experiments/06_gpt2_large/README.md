# GPT-2 Large

This experiment studies GPT-2-large training with LoRA/PEFT on CodeAlpaca-20K.

## Notebooks

- `GPT_2_large.ipynb` — training and experiment-data generation.
- `GPT_2_large_data_analysis.ipynb` — downstream analysis of the generated results.

The training notebook produces checkpoints and experiment result files that are intentionally excluded from Git.

## Dependencies

```bash
pip install -r ../../requirements/gpt2-large.txt
```

Training requires internet access, Hugging Face access, and substantial compute/GPU resources.
