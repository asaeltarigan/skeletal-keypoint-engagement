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

- `pose/` — pose-estimation backends (YOLO, MediaPipe, lightweight variants)
- `features/` — keypoint feature engineering
- `models/` — lightweight engagement classifier
- `experiments/` — evaluation runs and ablations
- `data/` — (not committed) raw/preprocessed data
- `results/` — (not committed) outputs and metrics

## Thesis

This repository accompanies the skeletal-keypoint engagement line published
across IAENG IJCS (2025), CMBiN (2026), and ICORIS (2025).

## Author

Gabriel Asael Tarigan — [asaeltarigan.github.io](https://asaeltarigan.github.io)