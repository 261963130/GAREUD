# Unprocessed Raw Data

This document describes the **Unprocessed raw data** release of GAREUD-Real. This version keeps the original RGB and event-camera recordings before rectification, ROI cropping, DVS-frame rendering, and synchronized processed packaging.

Use this version if you need to reproduce the dataset construction pipeline, inspect the original recordings, rerun calibration or alignment, generate custom event representations, or apply your own temporal slicing strategy.

## Download

| Version | Link |
|---|---|
| Unprocessed raw data | [Google Drive](https://drive.google.com/drive/folders/1WSdUVY31Msf_oUpoDQa9QQLj8btxbZYy?usp=drive_link) |

## Folder Layout

The unprocessed raw data is organized by real-world recording sequence:

```text
GAREUD_R/
|-- GAREUD_R_000001/
|   |-- rgbframe/
|   |   |-- 1415.670021592.jpg
|   |   |-- 1415.703367568.jpg
|   |   `-- ...
|   |-- 20260104_144809.hdf5
|   |-- calibration_info.txt
|   |-- params.json
|   `-- labels.txt
|-- GAREUD_R_000002/
|   `-- ...
|-- ...
`-- GAREUD_R_000082/
    `-- ...
```

Folder names use zero-padded sequence IDs:

```text
GAREUD_R_000001, GAREUD_R_000002, ..., GAREUD_R_000082
```

In the paper table, `R_01` corresponds to `GAREUD_R_000001`, `R_02` corresponds to `GAREUD_R_000002`, and so on.

## Sequence-Level Files

Each `GAREUD_R_xxxxxx/` folder contains the original RGB frames, raw event stream, calibration/alignment metadata, processing parameters, and labels.

| Path | Description |
|---|---|
| `rgbframe/` | Original RGB frames. File names are RGB acquisition timestamps. |
| `*.hdf5` | Original Prophesee event-camera recording. |
| `calibration_info.txt` | Stereo calibration and alignment information used for later rectification. |
| `params.json` | Manual alignment and ROI parameters used during processed-data construction. |
| `labels.txt` | Bounding-box annotations paired with RGB frame timestamps. |

## `rgbframe/`

The `rgbframe/` folder stores the original RGB frames extracted from the RGB camera recording.

Example:

```text
rgbframe/
  1415.670021592.jpg
  1415.703367568.jpg
  1415.736713136.jpg
  ...
```

Properties:

| Item | Description |
|---|---|
| File name | `<timestamp>.jpg` |
| Timestamp unit | seconds.nanoseconds-style string inherited from RGB acquisition |
| Image content | Original RGB frame before the refined dataset rectification and ROI crop |
| Typical raw resolution | `1280 x 720` |

The file stem is the RGB frame timestamp and is also used by `labels.txt`.

## Raw Event HDF5 File

Each sequence contains one original event-camera hdf5 file, for example:

```text
20260104_144809.hdf5
```

This file stores the raw event stream and external trigger stream recorded by the Prophesee event camera. The exact internal metadata may vary across recordings, but the relevant data groups are:

```text
<recording>.hdf5
  CD/
    events
  EXT_TRIGGER/
    events
```

### `CD/events`

The raw event stream is stored under:

```text
CD/events
```

Common fields:

| Field | Meaning |
|---|---|
| `x` | Raw event x coordinate |
| `y` | Raw event y coordinate |
| `p` | Event polarity |
| `t` | Event timestamp, in microseconds |

The raw coordinates are not yet stereo-rectified and are not ROI-cropped. Use the synchronized processed release if you want ready-to-use corrected coordinates.

### `EXT_TRIGGER/events`

The external trigger stream is stored under:

```text
EXT_TRIGGER/events
```

Common fields:

| Field | Meaning |
|---|---|
| `p` | Trigger level |
| `t` | Trigger timestamp, in microseconds |
| `id` | Trigger channel ID |

Trigger polarity convention:

| Trigger `p` | Meaning |
|---:|---|
| `0` | RGB exposure start |
| `1` | RGB exposure end |

A valid RGB exposure is represented by a `0 -> 1` pair. Some recordings may contain a leading useless `p=1` trigger before the first valid `p=0`. The first valid `0 -> 1` pair corresponds to the first RGB frame.

## `calibration_info.txt`

This file records the stereo calibration and alignment information used to transform raw RGB and event data into the synchronized processed release.

It may include:

- RGB camera intrinsic matrix `K1`
- event-camera intrinsic matrix `K2`
- event-camera rectification rotation `R2`
- translation vector `t2`
- manual RGB alignment offsets
- ROI origin and size

## `params.json`

This file stores per-sequence manual alignment and ROI parameters.

Example:

```json
{
  "offset_x": 2,
  "offset_y": -4,
  "crop_x": 184,
  "crop_y": 142,
  "crop_w": 1024,
  "crop_h": 576
}
```

Fields:

| Field | Description |
|---|---|
| `offset_x` | Horizontal shift applied to rectified RGB before cropping |
| `offset_y` | Vertical shift applied to rectified RGB before cropping |
| `crop_x` | ROI top-left x coordinate in the rectified common canvas |
| `crop_y` | ROI top-left y coordinate in the rectified common canvas |
| `crop_w` | ROI width |
| `crop_h` | ROI height |

The `offset_x` and `offset_y` values are applied to RGB before cropping. Event coordinates are rectified and ROI-cropped according to the event-camera calibration and ROI.

## `labels.txt`

The label file stores object annotations associated with RGB frame timestamps.

Typical annotation line:

```text
<timestamp> <class_id> <x_center> <y_center> <width> <height>
```

Example:

```text
1415.670021592 3 0.518131 0.381939 0.025136 0.026980
```

Fields:

| Field | Description |
|---|---|
| `timestamp` | RGB frame stem |
| `class_id` | Object class index |
| `x_center` | YOLO-normalized bounding-box center x |
| `y_center` | YOLO-normalized bounding-box center y |
| `width` | YOLO-normalized bounding-box width |
| `height` | YOLO-normalized bounding-box height |

Some lines may contain only a timestamp. Such lines indicate RGB frames without object annotations.

Class-name lines may also appear in the file:

```text
classes DJI M350RTK
classes DJI Mavic 4 Pro
classes DJI Air3
classes DJI Avata2
```

## Relation to Synchronized Processed Data

The synchronized processed release is derived from the unprocessed raw data by applying:

1. RGB stereo rectification.
2. Manual RGB translation using `offset_x` and `offset_y`.
3. event-camera coordinate rectification.
4. common ROI cropping.
5. DVS frame rendering for quick RGB-DVS pair browsing.
6. continuous corrected DVS h5 packaging.

Use the synchronized processed release for ready-to-use model training and evaluation. Use the unprocessed raw data when reproducing the processing pipeline or experimenting with alternative alignment and event slicing methods.
