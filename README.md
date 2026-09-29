# Lighter Student Engagement Recognition Using Skeletal Keypoints

Code for the paper **"Lighter Student Engagement Recognition in a Classroom
Environment Using Skeletal Keypoints"** — detecting student engagement from
skeletal keypoints extracted with object detection + pose estimation, and
classified with lightweight machine learning.

## Publication

> Gabriel Asael Tarigan, Gregorius Natanael Elwirehardja, Kuncahyo Setyo Nugroho,
> and Bens Pardamean. "Lighter Student Engagement Recognition in a Classroom
> Environment Using Skeletal Keypoints." *IAENG International Journal of Computer
> Science*, vol. 52, no. 6, June 2025, pp. 1997-2014.

## Approach

```
Raw video → person detection + pose estimation → skeleton keypoints → lightweight ML classifier → engagement label
```

The proposed method combines **YOLOv8m** for object (person) detection with
**MediaPipe** for skeletal keypoint estimation as state-of-the-art
alternatives, outperforming the baseline **YOLOv4 + OpenPose**:

| Metric | Proposed (YOLOv8m + MediaPipe) | Baseline (YOLOv4 + OpenPose) |
|---|---|---|
| Accuracy (test set) | **0.70** | 0.41 |
| Cross-entropy loss (test set) | **0.40** | 0.60 |
| Pose-detection data collection speed | **~16x faster** | 1x |

The accuracy and loss gains are confirmed by a statistically significant paired
t-test. Despite not being designed for it, the proposed method achieves multiple
keypoint detection matching the baseline's amount.

## Pose estimation

- **YOLOv8m** — person (object) detection
- **MediaPipe** — skeletal keypoint extraction / pose estimation

## Classification

Keypoint features are fed into a lightweight machine-learning classifier that
maps pose sequences to engagement states.

## Repository layout

- `experiments/` — Jupyter notebooks (result processing, baseline vs proposed
  methods, t-test analysis)
- `papers/` — the published IJCS paper (PDF)
- `dataset/processed/` — cleaned dataframes (CSV feature data)
- `dataset/results/` — compiled per-class result CSVs
- `dataset/raw/` — (not committed) raw source dataset, kept private

> Note: `dataset/raw/` is gitignored by design — it holds the raw
> student-engagement recordings (`Dataset.zip`), which remain private; the
> cleaned CSVs in `dataset/processed/` and `dataset/results/` are the public,
> reproducible layer. Notebooks in `experiments/` are committed with their cell
> outputs stripped for clean diffs.

## Dataset

The pose-coordinate dataset used in the paper is available separately:
`github.com/asaeltarigan/pose_coordinate`.

## Author

Gabriel Asael Tarigan — [asaeltarigan.github.io](https://asaeltarigan.github.io)