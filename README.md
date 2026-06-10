# GAREUD: Ground-Aerial RGB--Event UAV Dataset

GAREUD is a large-scale RGB--Event UAV detection benchmark designed for aligned multimodal sensing, small-target detection, and edge-oriented evaluation. The dataset contains real-world and synthetic subsets covering ground-to-air (G2A) and air-to-air (A2A) viewpoints, diverse illumination conditions, complex backgrounds, and challenging target motion.

**GAREUD-Real:** [Google Drive](https://drive.google.com/drive/folders/1WSdUVY31Msf_oUpoDQa9QQLj8btxbZYy?usp=drive_link)  
**GAREUD-Sim:** Google Drive link to be added.  
**Project page:** GitHub Pages can be enabled from the `docs/` folder after this repository is published.

## Highlights

- **RGB--Event UAV benchmark:** paired RGB frames and event representations for UAV detection.
- **Real-world and synthetic data:** real acquisition for natural sensing conditions and simulation for controlled analysis.
- **Precise sensing design:** co-axial RGB--Event imaging and microsecond-level trigger synchronization in the real-world subset.
- **Multiple viewpoints:** ground-to-air and air-to-air scenarios.
- **Small-target focus:** many UAV instances occupy only a small fraction of the image.
- **Edge-oriented evaluation:** designed with real-time RGB--Event UAV detection and deployment analysis in mind.

## Dataset Overview

| Subset | Domain | Viewpoints | Resolution | Duration | UAV types | Illumination |
|---|---:|---:|---:|---:|---:|---:|
| GAREUD-Real | Real-world | G2A and A2A | 1280 x 720 | 4.1 h | 4 | 10--160,000 lux |
| GAREUD-Sim | Synthetic | A2A | 1280 x 720 | 14 min | 2 | Controlled lighting |

GAREUD contains synchronized RGB data, raw event streams, event-frame representations for the synthetic subset, bounding-box labels, and synchronization metadata. The synthetic subset provides native spatial and temporal correspondence and is intended for controlled perturbation and robustness analysis.

## Download

The real-world subset is available on Google Drive:

[Download GAREUD-Real](https://drive.google.com/drive/folders/1WSdUVY31Msf_oUpoDQa9QQLj8btxbZYy?usp=drive_link)

The synthetic subset will be released through a separate `GAREUD_S` Google Drive link.

See [download.md](download.md) for recommended directory organization and integrity checks.

## Dataset Structure

```text
GAREUD_R/
|-- GAREUD_R_000001/
|   |-- rgbframe/
|   |   `-- *.jpg
|   |-- *.hdf5
|   |-- calibration_info.txt
|   |-- labels.txt
|   `-- params.json
|-- GAREUD_R_000002/
`-- ...

GAREUD_S/
|-- GAREUD_S_000001/
|   |-- images/
|   |   `-- *.png
|   |-- event_frames/
|   |   `-- *.png
|   |-- events.h5
|   `-- labels.txt
|-- GAREUD_S_000002/
`-- ...
```

### Real-world Sequence Files

Each real-world sequence is stored as `GAREUD_R/GAREUD_R_xxxxxx/`.

| Path | Description |
|---|---|
| `rgbframe/` | RGB frames associated with the synchronized labels. |
| `*.hdf5` | Raw event stream recorded by the event camera. |
| `calibration_info.txt` | Stereo rectification, calibration, and synchronization information. |
| `labels.txt` | Bounding-box annotations paired with synchronized frames. |
| `params.json` | Supplementary synchronization metadata. |

The real-world label file uses one annotation per line:

```text
timestamp class_id x_center y_center width height
```

Bounding boxes use normalized YOLO-style coordinates.

### Synthetic Sequence Files

Each synthetic sequence is stored as `GAREUD_S/GAREUD_S_xxxxxx/`.

| Path | Description |
|---|---|
| `images/` | RGB frames. File names are frame identifiers, for example `000001.png`. |
| `event_frames/` | Frame-like event representations paired with RGB frames. |
| `events.h5` | Raw event stream. |
| `labels.txt` | Bounding-box annotations. |

The synthetic label file uses one annotation per line:

```text
frame_id class_id x_center y_center width height
```

Bounding boxes use normalized YOLO-style coordinates.

## Citation

If you use GAREUD, please cite the corresponding paper:

```bibtex
@article{xia2026gareud,
  title   = {Full-Stack UAV Detection Pipeline from Precise RGB--Event Sensing to Efficient Edge Processing},
  author  = {Xia, Haoji and Liu, Siying and Jin, Jiaqi and Wang, Sihan and Huang, Tong and Han, Xujie and Wang, Zikai and Zhong, Yuxing and Zheng, Hanle and Cheng, Chen and Guo, Hao and Deng, Lei},
  journal = {To appear},
  year    = {2026}
}
```

## License

The dataset is released under the [Creative Commons Attribution-NonCommercial 4.0 International License](LICENSE).

## Contact

For questions, please contact Haoji Xia at hjxia@link.tyut.edu.cn.
