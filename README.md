# Matrix Product States and DMRG

A pedagogical implementation of **Matrix Product States (MPS)** and the **two-site Density Matrix Renormalization Group (DMRG)** algorithm for a finite spin-½ Heisenberg chain.

The project uses **exact diagonalization (ED)** as a benchmark to study MPS representations, bond-dimension truncation, DMRG convergence, and physical observables.

## Overview

The notebook develops the calculation progressively:

1. **Exact diagonalization**

   * Constructs the open-boundary spin-½ Heisenberg Hamiltonian.
   * Obtains the exact ground state and ground-state energy.

2. **Matrix Product States**

   * Converts the exact ground state into an MPS using successive singular value decompositions (SVDs).
   * Examines bond dimensions, Schmidt coefficients, and entanglement entropy.
   * Reconstructs the state from its MPS representation.

3. **Bond-dimension truncation**

   * Studies the effect of truncating the MPS to a finite bond dimension.
   * Compares the resulting energies with the exact diagonalization result.

4. **Two-site DMRG**

   * Constructs the Hamiltonian as a matrix product operator (MPO).
   * Implements two-site DMRG sweeps using local effective Hamiltonians and Lanczos diagonalization.
   * Performs SVD-based truncation after each two-site update.

5. **Observables**

   * Calculates local magnetization and spin-spin correlation functions.
   * Compares DMRG results with exact diagonalization.

## Model

The project considers the antiferromagnetic spin-½ Heisenberg chain with open boundary conditions,

$$
H = J \sum_{i=1}^{N-1}
\left(
S_i^x S_{i+1}^x +
S_i^y S_{i+1}^y +
S_i^z S_{i+1}^z
\right),
$$

with \(J=1\).

For the main calculations, a chain of \(N=10\) sites is used, allowing the DMRG results to be directly benchmarked against exact diagonalization.

## Results

For \(N=10\), exact diagonalization gives the ground-state energy

$$
E_0 = -4.258035207283.
$$

Using a maximum MPS bond dimension of \(\chi=16\), the two-site DMRG calculation gives

$$
E_{\mathrm{DMRG}} = -4.258035204616,
$$

with an absolute energy error of approximately

$$
2.7\times10^{-9}.
$$

The notebook also demonstrates that increasing the bond dimension substantially improves the MPS approximation and compares observables obtained from the MPS/DMRG state with the exact results.

## Contents

* `MPS-DMRG.ipynb` — Complete implementation, calculations, visualizations, and discussion.

## Requirements

The notebook uses standard Python scientific-computing libraries, including:

* NumPy
* SciPy
* Matplotlib

The notebook can be run in Jupyter Notebook or JupyterLab.

## Purpose

The main purpose of the project is to develop an understanding of the underlying numerical techniques rather than to study large systems. The relatively small system size makes it possible to compare every stage of the MPS/DMRG calculation with exact diagonalization.
