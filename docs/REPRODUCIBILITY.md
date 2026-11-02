# Reproducibility and visual sources

## Scope

This guide describes what is available in the committed project and what is required to reproduce it. The documentation update inspected source and saved outputs; it did not rerun model training or hardware/simulation experiments.

## Required inputs

Supply the real and manipulated video datasets expected by the configuration. The repository does not include the videos, trained weights, or a dependency lockfile. Keep the evaluation split at the video/source level when reporting generalization; sequences from the same video are correlated.

## Entry point

Use Jupyter with a compatible PyTorch/torchvision environment. The notebook imports NumPy, pandas, tqdm, OpenCV, MediaPipe, Matplotlib, seaborn, and scikit-learn in addition to PyTorch.

Open `advanced_resnet_lstm_deepfake.ipynb`, review the configuration cell, replace local real/fake video and checkpoint paths, and execute the data-processing sections before training. CUDA is recommended for the full model; pretrained ResNet weights require a model download.

## Evidence and interpretation

The figures included here are original saved outputs from the committed notebook, showing training history and a confusion matrix. They describe that saved run and were not regenerated here. The notebook's '>90%' statement is a target, and these results do not establish performance on arbitrary unseen video sources.

## Visual provenance

All screenshots and experiment figures are tied to repository material. Workflow SVGs are explanatory illustrations. The full image inventory is in [assets/sources.json](assets/sources.json).

| Visual | Source |
| --- | --- |
| [overview.svg](assets/overview.svg) | New explanatory project-workflow diagram based on the committed source and documentation; not a screenshot or measured result. |
| [notebook-1.png](assets/notebook-1.png) | advanced_resnet_lstm_deepfake.ipynb, cell 25 (1-based), committed image/png output; not rerun |
| [notebook-2.png](assets/notebook-2.png) | advanced_resnet_lstm_deepfake.ipynb, cell 27 (1-based), committed image/png output; not rerun |

## Validation

```bash
python tools/check_docs.py
```

The standard-library checker validates README/docs local link destinations and SVG/PNG/JPEG headers. It makes no external requests and installs no project runtime dependencies. External web links, model accuracy, image semantics, and full application execution need separate review.

## Refresh notebook visuals

The exporter reads saved `image/png` outputs without executing notebook code:

```bash
python tools/export_notebook_images.py "advanced_resnet_lstm_deepfake.ipynb"
```

Review the exported images, remove any unsuitable or private content, choose the figures that explain the project, and update the README links and `docs/assets/sources.json`. It does not manufacture results when a notebook has no saved PNG output.

## Reproduction record

For a new experiment or demo, record the source commit, environment versions, data provenance and split, configuration, command/notebook order, and resulting artifacts. Only label a measurement as reproduced after completing that run. Keep credentials and restricted datasets outside version control.
