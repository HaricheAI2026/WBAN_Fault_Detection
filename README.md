# WBAN Fault Detection

> Lightweight ML model for detecting wireless body area network (WBAN) faults using ECG and RSSI features, quantized for edge deployment on ESP32 / Arduino Nano 33 BLE.

---

## Overview

<!-- TODO: 2-3 sentence summary of the problem and approach -->

## Repository Structure

```
WBAN_Fault_Detection/
├── data/
│   ├── raw/              # Raw acquired datasets (ECG, RSSI)
│   └── processed/        # Cleaned, labeled, split datasets + dataset card
├── notebooks/            # Jupyter notebooks for exploration & training
├── src/
│   ├── data_loader.py        # Raw data ingestion
│   ├── feature_extraction.py # Feature engineering & labeling
│   ├── train_model.py        # Training pipeline (single source of truth)
│   └── evaluate_model.py     # Evaluation & benchmarking
├── models/
│   ├── fault_detector.h5      # Saved Keras model (full precision)
│   ├── fault_detector.tflite  # Quantized TFLite model
│   └── model_metadata.json    # Architecture & training hyperparams
├── deployment/
│   ├── main.ino              # Arduino/ESP32 firmware stub
│   ├── esp32_fault_detection.py # MicroPython fallback
│   └── performance_log.txt    # On-device latency & RAM numbers
├── results/
│   ├── baseline_metrics.csv   # DT + SVM baseline results
│   ├── ablation_study.csv     # Feature-ablation results
│   ├── confusion_matrix.png   # Final model confusion matrix
│   ├── training_curves.png    # Loss / accuracy curves
│   └── metrics_summary.csv    # Consolidated numbers for paper
├── paper/
│   ├── manuscript.md          # Draft manuscript (all sections)
│   └── references.bib         # BibTeX reference list
├── docs/
│   └── related_work_brief.md  # 1-page condensed literature brief
└── requirements.txt
```

## Quick Start

<!-- TODO: Installation and reproduction steps -->

## Dataset

<!-- TODO: Link to dataset card (data/processed/DATASET_CARD.md) -->

## Model

<!-- TODO: Architecture summary, target constraints (>85% accuracy, <100 KB) -->

## Results

<!-- TODO: Key numbers (accuracy, F1, latency, model size) -->

## Citation

<!-- TODO: BibTeX entry once published -->

## License

<!-- TODO: Choose license -->
