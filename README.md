# QESEM quantum machine learning tutorial

This repository contains a hands-on Jupyter notebook that walks through **quantum kernel methods** for classification and shows how to estimate those kernels on (simulated) hardware using **QESEM** (Quantum Error Suppression and Error Mitigation) via the IBM Quantum platform.

## Google Colab

To run the notebook without setting up a local environment, open it in [Google Colab](https://colab.research.google.com/github/Qedma/qesem-qml-tutorial/blob/main/quantum_kernel_tutorial_with_QESEM.ipynb). The notebook includes a cell to install dependencies with pip; you still need IBM credentials for the QESEM sections.

## What you will learn

1. **Classical kernels**: Feature maps, the kernel trick, and kernel-based classifiers (e.g. SVC).

2. **Quantum kernels**: Encoding data with a unitary feature map, fidelity overlap , and the **projected quantum kernel** (PQK) from [Huang et al., *Nature Communications* (2021)](https://www.nature.com/articles/s41467-021-22539-9.pdf).

3. **Feature maps implemented in the notebook**
   - **ZZ feature map**
   - **Ising Trotter feature map**

4. **Dataset and pipeline**

5. **Classical simulation**

6. **Four worked combinations** (ideal kernels + SVC):
   - Fidelity + Ising Trotter  
   - Projected + Ising Trotter  
   - Fidelity + ZZ map  
   - Projected + ZZ map  

7. **QESEM on IBM Quantum** It covers:
   - **Empirical time estimation**: `options={"estimate_time_only": "empirical", ...}` before a full run.
   - **Full mitigation**: Same pattern without `estimate_time_only`, optional `max_execution_time` (seconds).
   - **Parameterized circuits**: Batching several fidelity kernel matrix elements in one job by passing multiple parameter sets for a single transpiled template circuit.
   - **Projected kernel**: QESEM job with Pauli-string observables for the PQK construction.

You must supply your **IBM Quantum API token** and **instance** where the notebook shows placeholders (`IBM_token`, `ibm_instance`).

## Dependencies

Install a recent **Python 3** environment with at least:

- `qiskit`
- `qiskit-ibm-catalog` (for `QiskitFunctionsCatalog` and QESEM access)
- `numpy`
- `scikit-learn`
- `matplotlib`
- `pylatexenc`

Exact versions are pinned in this repo.

Example:

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install qiskit qiskit-ibm-catalog numpy scikit-learn matplotlib jupyter pylatexenc
jupyter notebook quantum_kernel_tutorial_with_QESEM.ipynb
```

Working example for the dependencies:
```bash
pip install qiskit==2.4.1 qiskit-ibm-catalog==0.15.0 numpy==2.4.4 scikit-learn==1.8.0 matplotlib==3.10.9 pylatexenc==2.10 ipykernel
jupyter notebook quantum_kernel_tutorial_with_QESEM.ipynb
```

## Prerequisites for QESEM sections

- IBM Quantum account and credentials accepted by the catalog channel used in the notebook (`ibm_quantum_platform` in the example).
- Access to the **QESEM** function (`qedma/qesem`) as loaded through the catalog.