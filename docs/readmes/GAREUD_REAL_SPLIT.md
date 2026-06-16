# GAREUD-Real Train/Test Split

This file records the train/test split for the real-world GAREUD release. The original split used scene-task folder names such as `1.4/4_todo`; these names have been converted to the released sequence folders using the sequence-name mapping from dataset construction.

The split is sequence-level: all frames from one sequence folder are assigned to either the training set or the test set.

## Summary

| Split | Sequences | Images | Share |
|---|---:|---:|---:|
| Train | 54 | 299,659 | 67.4% |
| Test | 28 | 144,808 | 32.6% |
| Total | 82 | 444,467 | 100.0% |

## Scene Summary

| Scene | Train images | Test images | Total images |
|---|---:|---:|---:|
| 1.4 | 35,320 | 36,854 | 72,174 |
| 1.4.5 | 6,957 | 0 | 6,957 |
| 1.5 | 97,413 | 37,698 | 135,111 |
| 1.6 | 2,119 | 926 | 3,045 |
| 1.7 | 3,523 | 3,677 | 7,200 |
| 1.15 | 21,559 | 11,526 | 33,085 |
| 1.19 | 23,470 | 24,716 | 48,186 |
| 1.19.5 | 18,780 | 0 | 18,780 |
| 1.20 | 20,967 | 0 | 20,967 |
| 3.12 | 2,284 | 2,441 | 4,725 |
| 3.17 | 22,134 | 10,123 | 32,257 |
| 3.18 | 22,933 | 10,803 | 33,736 |
| 3.18.5 | 22,200 | 6,044 | 28,244 |
| **Total** | **299,659** | **144,808** | **444,467** |

## Training Sequences

| Sequence folder | Images | Original split id |
|---|---:|---|
| **Scene 1.4** | **35,320** |  |
| `GAREUD_R_000001` | 9,285 | `1.4-4` |
| `GAREUD_R_000003` | 25,603 | `1.4-6` |
| `GAREUD_R_000006` | 432 | `1.4-9` |
| **Scene 1.4.5** | **6,957** |  |
| `GAREUD_R_000008` | 6,957 | `1.4.5-11` |
| **Scene 1.5** | **97,413** |  |
| `GAREUD_R_000009` | 17,295 | `1.5-12` |
| `GAREUD_R_000010` | 2,582 | `1.5-13` |
| `GAREUD_R_000011` | 5,856 | `1.5-14` |
| `GAREUD_R_000013` | 4,498 | `1.5-16` |
| `GAREUD_R_000015` | 9,942 | `1.5-18` |
| `GAREUD_R_000016` | 1,176 | `1.5-19` |
| `GAREUD_R_000017` | 5,990 | `1.5-20` |
| `GAREUD_R_000018` | 3,921 | `1.5-21` |
| `GAREUD_R_000021` | 9,250 | `1.5-25` |
| `GAREUD_R_000023` | 10,439 | `1.5-27` |
| `GAREUD_R_000024` | 7,268 | `1.5-28` |
| `GAREUD_R_000025` | 1,509 | `1.5-29` |
| `GAREUD_R_000026` | 7,945 | `1.5-30` |
| `GAREUD_R_000027` | 9,742 | `1.5-31` |
| **Scene 1.6** | **2,119** |  |
| `GAREUD_R_000028` | 2,119 | `1.6-1` |
| **Scene 1.7** | **3,523** |  |
| `GAREUD_R_000031` | 838 | `1.7-4` |
| `GAREUD_R_000032` | 2,685 | `1.7-5` |
| **Scene 1.15** | **21,559** |  |
| `GAREUD_R_000037` | 10,162 | `1.15-3` |
| `GAREUD_R_000038` | 412 | `1.15-4` |
| `GAREUD_R_000039` | 6,707 | `1.15-5` |
| `GAREUD_R_000040` | 4,278 | `1.15-7` |
| **Scene 1.19** | **23,470** |  |
| `GAREUD_R_000041` | 8,964 | `1.19-1` |
| `GAREUD_R_000044` | 3,987 | `1.19-5` |
| `GAREUD_R_000046` | 6,170 | `1.19-10` |
| `GAREUD_R_000047` | 4,349 | `1.19-11` |
| **Scene 1.19.5** | **18,780** |  |
| `GAREUD_R_000048` | 9,911 | `1.19.5-7` |
| `GAREUD_R_000049` | 7,742 | `1.19.5-8` |
| `GAREUD_R_000050` | 1,127 | `1.19.5-9` |
| **Scene 1.20** | **20,967** |  |
| `GAREUD_R_000051` | 5,792 | `1.20-1` |
| `GAREUD_R_000052` | 7,646 | `1.20-2` |
| `GAREUD_R_000053` | 7,529 | `1.20-3` |
| **Scene 3.12** | **2,284** |  |
| `GAREUD_R_000054` | 1,022 | `3.12-6` |
| `GAREUD_R_000055` | 1,262 | `3.12-7` |
| **Scene 3.17** | **22,134** |  |
| `GAREUD_R_000058` | 1,475 | `3.17-1` |
| `GAREUD_R_000059` | 4,441 | `3.17-2` |
| `GAREUD_R_000061` | 5,312 | `3.17-4` |
| `GAREUD_R_000062` | 4,386 | `3.17-5` |
| `GAREUD_R_000063` | 1,886 | `3.17-6` |
| `GAREUD_R_000065` | 2,771 | `3.17-8` |
| `GAREUD_R_000067` | 1,863 | `3.17-10` |
| **Scene 3.18** | **22,933** |  |
| `GAREUD_R_000068` | 4,937 | `3.18-1` |
| `GAREUD_R_000069` | 7,544 | `3.18-2` |
| `GAREUD_R_000071` | 7,600 | `3.18-4` |
| `GAREUD_R_000074` | 2,852 | `3.18-7` |
| **Scene 3.18.5** | **22,200** |  |
| `GAREUD_R_000075` | 8,505 | `3.18.5-8` |
| `GAREUD_R_000076` | 2,433 | `3.18.5-9` |
| `GAREUD_R_000077` | 3,025 | `3.18.5-10` |
| `GAREUD_R_000078` | 4,225 | `3.18.5-11` |
| `GAREUD_R_000081` | 3,436 | `3.18.5-14` |
| `GAREUD_R_000082` | 576 | `3.18.5-15` |

## Test Sequences

| Sequence folder | Images | Original split id |
|---|---:|---|
| **Scene 1.4** | **36,854** |  |
| `GAREUD_R_000002` | 14,398 | `1.4-5` |
| `GAREUD_R_000004` | 16,687 | `1.4-7` |
| `GAREUD_R_000005` | 4,017 | `1.4-8` |
| `GAREUD_R_000007` | 1,752 | `1.4-10` |
| **Scene 1.5** | **37,698** |  |
| `GAREUD_R_000012` | 4,396 | `1.5-15` |
| `GAREUD_R_000014` | 8,549 | `1.5-17` |
| `GAREUD_R_000019` | 8,728 | `1.5-22` |
| `GAREUD_R_000020` | 5,341 | `1.5-24` |
| `GAREUD_R_000022` | 10,684 | `1.5-26` |
| **Scene 1.6** | **926** |  |
| `GAREUD_R_000029` | 926 | `1.6-2` |
| **Scene 1.7** | **3,677** |  |
| `GAREUD_R_000030` | 2,488 | `1.7-3` |
| `GAREUD_R_000033` | 443 | `1.7-12` |
| `GAREUD_R_000034` | 746 | `1.7-14` |
| **Scene 1.15** | **11,526** |  |
| `GAREUD_R_000035` | 10,097 | `1.15-1` |
| `GAREUD_R_000036` | 1,429 | `1.15-2` |
| **Scene 1.19** | **24,716** |  |
| `GAREUD_R_000042` | 8,797 | `1.19-2` |
| `GAREUD_R_000043` | 4,558 | `1.19-4` |
| `GAREUD_R_000045` | 11,361 | `1.19-6` |
| **Scene 3.12** | **2,441** |  |
| `GAREUD_R_000056` | 866 | `3.12-8` |
| `GAREUD_R_000057` | 1,575 | `3.12-9` |
| **Scene 3.17** | **10,123** |  |
| `GAREUD_R_000060` | 4,382 | `3.17-3` |
| `GAREUD_R_000064` | 2,076 | `3.17-7` |
| `GAREUD_R_000066` | 3,665 | `3.17-9` |
| **Scene 3.18** | **10,803** |  |
| `GAREUD_R_000070` | 1,867 | `3.18-3` |
| `GAREUD_R_000072` | 2,753 | `3.18-5` |
| `GAREUD_R_000073` | 6,183 | `3.18-6` |
| **Scene 3.18.5** | **6,044** |  |
| `GAREUD_R_000079` | 4,968 | `3.18.5-12` |
| `GAREUD_R_000080` | 1,076 | `3.18.5-13` |

## Notes

- Image counts are copied from the original split record and then rechecked by summing the sequence entries.
- `Original split id` is kept only for traceability. Users should use the `GAREUD_R_000xxx` sequence folders in the released dataset.
- The processed real-world dataset layout is documented in the root README.
