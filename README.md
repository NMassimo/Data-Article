# MoT-Zb Profiling Dataset

This repository accompanies the data article **A Comprehensive Dataset for Device Fingerprinting and Traffic Classification in Zigbee and Matter over Thread Networks**.

It contains the raw captures, metadata, and ground truth used in the study. It also includes Python notebooks that reproduce the feature extraction and classification workflow described in the article.

## Dataset Summary

- 6 continuous captures, 12 hours each
- 2 protocols: Matter over Thread and Zigbee
- 3 topology settings: A, B, and C
- Ground truth artifacts for each capture:
  - packet capture files (`.pcapng`)
  - capture metadata and device tables (`CaptureX_description.md`)
  - state-change logs (`CaptureX_log.csv`)
  - command logs (`CaptureX_output.csv`)
  - topology snapshots

## Topology Mapping

- Topology A: baseline full-mesh layout
- Topology B: distributed residential layout 1 (multi-hop)
- Topology C: distributed residential layout 2 (multi-hop)

## Reproducibility Workflow

The notebooks are organized as follows:

1. `Feature_Extraction.ipynb` reads the packet captures and produces 5-second window feature tables.
2. `Classification.ipynb` loads the extracted features and runs the Random Forest classification example used in the paper.

## Notes on Metadata

- `CaptureX_description.md` is the primary human-readable source for each capture.
- For Matter over Thread, the capture description includes the device table, capture start time, decryption key, and embedded topology snapshots.
- For Zigbee, topology snapshots are exported separately as JSON files using `zha_toolkit`.
