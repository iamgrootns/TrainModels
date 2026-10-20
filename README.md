# TrainModels

Training scripts for different kinds of models - one folder per model family,
one script per task. Everything runs from the command line so results stay
reproducible.

Planned layout:

```
TrainModels/
  vision/      image classification, object detection, segmentation
  audio/       ASR fine-tuning, speaker models, music / speech synthesis
  llm/         supervised fine-tuning, LoRA / QLoRA, preference tuning
  common/      dataset loading, metrics, training helpers
```

## Principles

* One script per task - `train.py` does one thing and takes config as flags
* Configs are explicit and versioned next to the script they belong to
* Every script prints the environment (GPU, torch, dataset size) before training
* Checkpoints and outputs go to `runs/<script_name>/<date>/` (git-ignored)

## Conventions

```bash
# run with uv (Python 3.10 pinned in .python-version)
uv sync
uv run python vision/train_classifier.py --data ./data/animals --epochs 10
```

Each training script follows the same shape:

```python
def main():
    # 1) load config + print environment
    # 2) build dataset
    # 3) build model
    # 4) train loop
    # 5) evaluate + save checkpoint
```

## Status

Work in progress - scripts are added one family at a time.

## License

MIT
