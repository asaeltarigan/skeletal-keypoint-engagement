# Skeletal Keypoint Engagement Detection

Master's thesis code — detecting student engagement from skeletal keypoints
extracted with pose estimation, classified with lightweight machine learning.

## Approach

```
Raw video → pose estimation → skeleton keypoints → lightweight ML classifier → engagement label
```

The pipeline compares several pose-estimation backends and keeps the total
stack light enough to run in real time on modest hardware.

## Pose estimation

Multiple pose backends are evaluated, so the whole pipeline can run fast and
reproducibly:

- **YOLO** — person detection, providing the input crop before keypoints are
  extracted
- **MediaPipe** — skeletal keypoint extraction (landmark tracking)
- **Lighter pose models** — e.g. MoveNet / YOLOv8-pose (light) as faster
  alternatives to MediaPipe/BlazePose, to reduce latency on long classroom
  footage

## Classification

Keypoint features are fed into a lightweight machine-learning classifier that
maps pose sequences to engagement states.

## Repository layout

- `experiments/` — Jupyter notebooks (result processing, baseline vs proposed
  methods, t-test analysis)
- `dataset/processed/` — cleaned dataframes (CSV feature data)
- `dataset/results/` — compiled per-class result CSVs
- `dataset/raw/` — (not committed) raw source dataset, kept private

> Note: `dataset/raw/` is gitignored by design — it holds the raw
> student-engagement recordings (`Dataset.zip`), which remain private; the
> cleaned CSVs in `dataset/processed/` and `dataset/results/` are the public,
> reproducible layer. Notebooks in `experiments/` are committed with their cell
> outputs stripped for clean diffs.

## Thesis

This repository accompanies the skeletal-keypoint engagement line published
across IAENG IJCS (2025), CMBiN (2026), and ICORIS (2025).

## Author

Gabriel Asael Tarigan — [asaeltarigan.github.io](https://asaeltarigan.github.io)