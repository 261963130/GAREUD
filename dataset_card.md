# Dataset Card for GAREUD

## Dataset Summary

GAREUD (Ground-Aerial RGB--Event UAV Dataset) is an RGB--Event benchmark for UAV detection under challenging sensing and deployment conditions. It contains real-world and synthetic subsets with paired RGB data, raw event streams, labels, and synchronization metadata.

## Intended Use

GAREUD is intended for:

- RGB--Event UAV detection
- multimodal fusion research
- small-target UAV detection
- cross-modal alignment and perturbation analysis
- edge-oriented detector evaluation

The dataset is intended for non-commercial research and educational use under CC BY-NC 4.0.

## Data Domains

- **GAREUD-Real:** real-world co-axial RGB--Event acquisition with microsecond-level trigger synchronization.
- **GAREUD-Sim:** synthetic RGB--Event data generated for controlled scenario diversity and perturbation analysis.

## Modalities

- RGB frames
- raw event streams
- event-frame representations in the synthetic subset
- bounding-box annotations
- calibration and synchronization metadata in the real-world subset

## Sequence Structure

Real-world sequences follow the pattern `GAREUD_R/GAREUD_R_xxxxxx/` and include `rgbframe/`, one raw event-stream HDF5 file, `calibration_info.txt`, `labels.txt`, and supplementary synchronization metadata.

Synthetic sequences follow the pattern `GAREUD_S/GAREUD_S_xxxxxx/` and include `images/`, `event_frames/`, `events.h5`, and `labels.txt`.

Real-world labels use:

```text
timestamp class_id x_center y_center width height
```

Synthetic labels use:

```text
frame_id class_id x_center y_center width height
```

All bounding boxes use normalized YOLO-style coordinates.

## Known Limitations

- Synthetic event data approximate the event-camera sensing mechanism and should not be interpreted as direct evidence of synthetic-to-real generalization.
- Frame-like event representations may reduce the native temporal advantage of event cameras.
- Real-world acquisition can still contain residual sensing noise, optical artifacts, and scene-dependent event activity.

## Ethical and Safety Notes

GAREUD is intended for research on UAV perception, sensing robustness, and edge deployment. Users are responsible for complying with local laws and institutional policies when applying UAV detection systems.
