# FETI-SAW: An Efficient Domain Decomposition Solver for FE Simulation of SAW Devices

This repository contains the source code associated with the **FETI-SAW** paper.

## ⚠️ Notice

To protect intellectual property, **only limited demo examples are provided prior to the official publication of the paper**. The core implementation and all configurable algorithmic parameters will be released after the paper is formally published.

---

## 📦 Repository Contents

Currently, this repository provides **two MATLAB demo examples** that can be executed directly:

- **Demo 1**  
  - Substrate: 128° YX-cut LiNbO₃ (128YXLN)  
  - Electrode: Cu  

- **Demo 2**  
  - Substrate: 42° YX-cut LiTaO₃ (42YXLT)  
  - Electrode: Al  

Both demos correspond to a **SAW resonator operating at 400 MHz**, with the following configuration:

- 41 IDT fingers  
- 20 reflecting gratings  
- 2 bare regions  

---

## ▶️ How to Run

Simply run the provided MATLAB demo scripts. No additional configuration is required.

---

## 📊 Output

Running each demo will produce:

1. **`result.mat` file**, containing:
   - `runtime`: timing information for each stage of the algorithm
   - `res`: relative residuals of each GCR iteration step

2. **Visualization outputs**:
   - Displacement field in the device
   - Electric potential distribution

---

## ⏱️ Runtime Breakdown

The `runtime` variable records execution time for each major computational stage:

| Stage Name                  | Description |
|---------------------------|-------------|
| `InitModel`               | Initialize substructure objects |
| `discreteSubregion`       | Assemble finite element stiffness matrices and load vectors for subregions |
| `subregionLUDecomposition`| Perform LU decomposition for subregion matrices |
| `InitPrecond`             | Initialize Dirichlet preconditioner |
| `genCoarseMat`            | Construct the SAW coarse space |
| `computeQFQ`              | Form the global coarse problem matrix |
| `LUtoQFQ`                 | Perform LU decomposition of the coarse matrix |
| `iterationMethod`         | Solve the Lagrange multiplier system using GCR iteration |
| `computeSourceSol`        | Recover displacement and electric potential from Lagrange multipliers |

---

## 📈 Iterative Solver Output

- The variable `res` stores the **relative residual at each iteration step** of the GCR solver.
- This allows detailed analysis of convergence behavior.

---

## 🔒 Future Release Plan

After the official publication of the paper:

- All **tunable algorithmic parameters** will be exposed
- The **core implementation of the algorithm** will be fully open-sourced

---

## 📄 Citation

If you use this code in your research, please cite the corresponding FETI-SAW paper (to be updated after publication).

---

## 📬 Contact

For questions or collaboration inquiries, please open an issue or contact the authors.

---
