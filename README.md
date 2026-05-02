# Edge-LLM-Bench

Reproducible benchmarking framework for generative AI inference on the
**Raspberry Pi 5 + Hailo-10H NPU (Raspberry Pi AI HAT+ 2)**, comparing
NPU-offloaded inference against CPU-only inference across throughput,
latency, energy, thermal stability, and concurrent-workload impact.

This repository accompanies the paper:

> *Edge-LLM-Bench: Characterising LLM Inference on Raspberry Pi 5 with
> Hailo-10H NPU Acceleration.*
> Proceedings of the 7th International Workshop on Embedded and Mobile
> Deep Learning (EMDL '26), Cambridge, UK, June 25, 2026.

## Status

**Code release in progress.** This repository currently serves as the
permanent landing page referenced in the camera-ready paper. The full
benchmarking framework (run scripts, prompt suite, power-meter logger,
analysis notebooks, and figure-generation code) will be pushed here in
**June 2026** after a clean-up and documentation pass.

If you would like early access for review or replication, please open an
issue or contact the corresponding author.

## Planned contents

| Path | Description |
|------|-------------|
| `scripts/run_hailo_bench.sh` | Hailo-10H benchmark driver |
| `scripts/run_cpu_bench.sh`   | Ollama / llama.cpp CPU benchmark driver |
| `scripts/run_thermal.sh`     | 30-minute sustained-load thermal test |
| `scripts/run_concurrent.sh`  | NPU + stress-ng concurrent-workload test |
| `analysis/analyze.py`        | Throughput, TTFT, memory aggregation |
| `analysis/energy_analysis.py`| FNB58 power-log → energy-per-query / per-token |
| `analysis/plot_thermal.py`   | Thermal-stability figure |
| `analysis/plot_frontiers.py` | Quality–energy Pareto frontier figure |
| `prompts.json`               | 30-prompt evaluation suite |
| `results/`                   | Raw JSONL measurement logs |

## Hardware requirements

- Raspberry Pi 5 (16 GB recommended)
- Raspberry Pi AI HAT+ 2 (Hailo-10H, 8 GB on-module LPDDR4X)
- Fnirsi FNB58 USB power meter (or compatible) for energy measurements
- Active cooler on Pi 5; passive heatsink on AI HAT+ 2

## Software requirements (planned)

- Raspberry Pi OS Trixie (64-bit)
- HailoRT driver and `hailo-ollama` server
- Ollama (CPU baseline, llama.cpp backend)
- Python 3.11+

## Citing

If you use this framework, please cite:

```bibtex
@inproceedings{edgellmbench2026,
  title     = {Edge-LLM-Bench: Characterising LLM Inference on
               Raspberry Pi 5 with Hailo-10H NPU Acceleration},
  author    = {Duc V. Le and Ozlem Durmaz Incel},
  booktitle = {Proceedings of the 7th International Workshop on
               Embedded and Mobile Deep Learning (EMDL '26)},
  year      = {2026},
  publisher = {ACM},
}
