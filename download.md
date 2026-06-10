# Download GAREUD

The GAREUD release is split into two Google Drive folders.

## GAREUD-Real

[https://drive.google.com/drive/folders/1WSdUVY31Msf_oUpoDQa9QQLj8btxbZYy?usp=drive_link](https://drive.google.com/drive/folders/1WSdUVY31Msf_oUpoDQa9QQLj8btxbZYy?usp=drive_link)

## GAREUD-Sim

Google Drive link to be added.

## Recommended Steps

1. Open the Google Drive folder for the target subset.
2. Download `GAREUD_R` and `GAREUD_S` separately.
3. Preserve the released folder structure.
4. Keep each sequence directory intact, because RGB data, event data, labels, and synchronization metadata are stored together.
5. Verify that RGB frames, event representations, raw event streams, and labels remain under the same sequence folder.

## Released Structure

```text
GAREUD_R/
|-- GAREUD_R_000001/
|   |-- rgbframe/
|   |   `-- <timestamp>.jpg
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

## Annotation Format

Real-world labels:

```text
timestamp class_id x_center y_center width height
```

Synthetic labels:

```text
frame_id class_id x_center y_center width height
```

All bounding boxes use normalized YOLO-style coordinates.

## Data Availability Statement

The GAREUD dataset is released through separate Google Drive folders for `GAREUD_R` and `GAREUD_S`. The release includes real-world and synthetic subsets, raw event streams, RGB frames, event-frame representations for the synthetic subset, labels, and synchronization metadata. Documentation describing the data structure and annotation format is also provided.
