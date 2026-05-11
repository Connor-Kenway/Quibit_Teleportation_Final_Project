# Quantum Teleportation — Computer Architecture Final Project

Jupyter notebook project for **CPP Spring 2026 — Computer Architecture**. It builds and studies quantum circuits in **Qiskit**: entangled Bell pairs, **quantum teleportation** (with classical feed-forward using `if_test`), optional **arbitrary single-qubit preparation** via `UGate`, and comparison between **local simulation** and **IBM Quantum** hardware.

## Contents

| Topic | Description |
|--------|-------------|
| Bell state | Two-qubit circuit (Hadamard + CNOT), measurement statistics on `AerSimulator`. |
| Teleportation | Three-qubit protocol: Bell pair, Alice’s basis change and measurement, Bob’s **conditional X/Z** corrections, measurement of Bob’s qubit. |
| General states | Preparation with `UGate`, inverse for verification, histograms of outcomes. |
| IBM Quantum | `QiskitRuntimeService`, pick a least-busy real backend, `transpile` with optimization, `SamplerV2` job, result histograms and a simple **teleportation fidelity** estimate from counts. |

Main notebook: **`quantum_circuit.ipynb`**.

## Requirements

- **Python** 3.10+ (notebook metadata references Python 3.13; any recent 3.x used with Qiskit is fine).
- **Jupyter** (e.g. JupyterLab or VS Code with Jupyter support).

Python packages:

- `qiskit`
- `qiskit-aer`
- `qiskit-ibm-runtime`
- `matplotlib`
- `numpy`

Install (example):

```bash
pip install qiskit qiskit-aer qiskit-ibm-runtime matplotlib numpy notebook
```

## How to run

1. Open a terminal in this folder.
2. Start Jupyter: `jupyter notebook` or `jupyter lab`.
3. Open **`quantum_circuit.ipynb`** and run cells top to bottom.

Early cells use only **`AerSimulator`** and do not need an IBM account. Sections that call **`QiskitRuntimeService`** require a saved IBM Quantum API token and network access.

## IBM Quantum (optional)

To run on real hardware:

1. Create an account at [IBM Quantum](https://quantum.ibm.com/) and create an API token.
2. Save credentials once (see commented cell in the notebook using `QiskitRuntimeService.save_account`, or use the Qiskit CLI / documented login flow).
3. Run the cells that instantiate `QiskitRuntimeService()`, select `least_busy` operational non-simulator backend, transpile, and submit via `SamplerV2`.

Queue time, noise, and calibration vary by device; measured distributions will differ from noiseless simulation.

## Repository layout

```
Final Project/
├── quantum_circuit.ipynb   # Main lab / report notebook
└── README.md               # This file
```

## Notes

- Do **not** commit API tokens or `save_account` calls with real secrets; keep tokens in environment variables or local config ignored by git.
- The notebook may contain large embedded plot outputs; clearing outputs before version control keeps diffs smaller if you prefer.

## License / course use

This repository is for coursework (Computer Architecture final project). Adapt attribution and license to your course policy if you redistribute the work.
