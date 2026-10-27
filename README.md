# Quantum Entanglement and Noise Analysis with Qiskit

This project investigates how different quantum noise channels affect a two-qubit Bell state. Using Qiskit and NumPy, I simulate noise acting on one or both qubits and compare its effects on state fidelity, purity, and entanglement.

The goal is to understand how different physical error mechanisms change quantum states and how these changes can be quantified.

## 1. Bell-State Preparation

The initial state is the maximally entangled Bell state:

$$
|\Phi^+\rangle = \frac{|00\rangle+|11\rangle}{\sqrt{2}}
$$

It is prepared by applying a Hadamard gate to the first qubit, followed by a CNOT gate.

The corresponding density matrix is

$$
\rho_{\mathrm{ideal}}=|\Phi^+\rangle\langle\Phi^+|
$$

## 2. Quantum Noise Models

Five noise channels are implemented using Kraus operators:

- **Depolarizing noise:** Random Pauli errors that affect the quantum state.
- **Amplitude damping:** Models energy relaxation from the excited state to the ground state.
- **Phase damping:** Reduces quantum coherence without changing computational-basis populations.
- **Bit-flip noise:** Applies a Pauli-X error with probability \(p\).
- **Phase-flip noise:** Applies a Pauli-Z error with probability \(p\).

The evolution of a density matrix under a quantum channel is described by

$$
\mathcal{E}(\rho)=\sum_k K_k\rho K_k^\dagger
$$

where the Kraus operators satisfy

$$
\sum_k K_k^\dagger K_k=I
$$

For each noise model, the channel is applied after Bell-state preparation, either to qubit 0 or independently to both qubits.

## 3. Quantum-State Characterization

Three quantities are calculated to characterize the noisy quantum states.

### State Fidelity

Fidelity measures the similarity between the noisy state and the ideal Bell state:

$$
F=\langle\Phi^+|\rho|\Phi^+\rangle
$$

### State Purity

Purity measures how mixed a quantum state is:

$$
P=\mathrm{Tr}(\rho^2)
$$

For a two-qubit system, a pure state has \(P=1\), while the maximally mixed state has \(P=1/4\).

### Concurrence

Concurrence quantifies entanglement in a two-qubit state:

$$
C(\rho)=\max(0,\lambda_1-\lambda_2-\lambda_3-\lambda_4)
$$

where the \(\lambda_i\) are the eigenvalue-derived quantities in Wootters' concurrence formula, arranged in descending order.

Concurrence ranges from 0 for separable states to 1 for maximally entangled states.

## 4. Numerical Experiments

The notebook contains the following experiments:

1. Prepare a Bell state and calculate its ideal density matrix.
2. Implement and verify five noise channels.
3. Apply each noise channel to one qubit and both qubits.
4. Calculate fidelity, purity, and concurrence for different noise strengths.
5. Plot the three quantities as functions of noise strength.
6. Examine amplitude damping in more detail.
7. Visualize the real parts of selected density matrices.
8. Verify normalization, Hermiticity, positivity, and selected limiting cases.

The noise parameter is varied from \(p=0\) to \(p=1\), using 51 values.

## 5. Physical Interpretation

The simulations allow us to compare several important properties of noisy quantum states.

Fidelity, purity, and concurrence describe different aspects of a quantum state. A decrease in fidelity does not necessarily imply that entanglement has disappeared.

Comparing noise on one qubit with noise on both qubits also shows how local noise processes affect a shared entangled state.

The results depend on the physical noise mechanism. In particular, bit-flip and phase-flip channels need not produce monotonically decreasing quantities across the full parameter range, because \(p=1\) corresponds to a deterministic Pauli operation.

## 6. Implementation

The simulations use density matrices and Kraus operators to calculate the action of idealized quantum noise channels directly.

This approach avoids finite-shot sampling uncertainty and allows the effects of different noise channels to be compared independently of measurement statistics.

Readout errors, hardware calibration, and quantum error mitigation are outside the scope of this project.

## 7. Repository Contents

- **`Quantum_Entanglement_and_Noise.ipynb`** — Bell-state preparation, noise simulation, entanglement analysis, plots, and numerical checks.
- **`README.md`** — Project description and methodology.

## 8. Requirements

- Python 3
- Qiskit
- NumPy
- Matplotlib
- Jupyter Notebook

Install the main dependencies with:

```bash
pip install qiskit numpy matplotlib jupyter
```

Open `Quantum_Entanglement_and_Noise.ipynb` in Jupyter Notebook or VS Code and run the cells sequentially.

## 9. Conclusion

This project explores how different noise channels affect entangled quantum states and compares their effects using fidelity, purity, and concurrence.

It provides a numerical framework for studying quantum decoherence, entanglement degradation, and the differences between single-qubit and two-qubit noise exposure.
