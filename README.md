# Quantum Computing and Algorithms Lab

Six hands-on experiments in Qiskit, from a single qubit on the Bloch sphere to factoring 15 with Shor's algorithm. Every experiment is a fully executed Jupyter notebook: the problem statement, the code, the real simulator output and the observations sit together, so you can read results without running anything.

The complete lab record is included as a typeset PDF: [`Ritesh_Roshan_Sahoo_DL.AI.U4AID24036_QCA_Lab_Record.pdf`](Ritesh_Roshan_Sahoo_DL.AI.U4AID24036_QCA_Lab_Record.pdf).

## Experiments

| # | Experiment | Tasks | Notebook |
|---|---|---|---|
| 1 | Quantum state evolution on the Bloch sphere | 5 | [`Exp1_Bloch_Sphere.ipynb`](Exp1_Bloch_Sphere.ipynb) |
| 2 | Deutsch algorithm | 5 | [`Exp2_Deutsch_Algorithm.ipynb`](Exp2_Deutsch_Algorithm.ipynb) |
| 3 | Bernstein-Vazirani algorithm | 5 | [`Exp3_Bernstein_Vazirani.ipynb`](Exp3_Bernstein_Vazirani.ipynb) |
| 4 | Simon's algorithm | 5 | [`Exp4_Simons_Algorithm.ipynb`](Exp4_Simons_Algorithm.ipynb) |
| 5 | Grover's search algorithm | 5 | [`Exp5_Grovers_Search.ipynb`](Exp5_Grovers_Search.ipynb) |
| 6 | Shor's algorithm | 6 | [`Exp6_Shors_Algorithm.ipynb`](Exp6_Shors_Algorithm.ipynb) |

### 1. Quantum state evolution on the Bloch sphere

Prepares |1⟩ three different ways and lets the transpiler prove that H Z H and H S S H collapse to a single gate. Reverse engineers a circuit that outputs |+⟩, and shows that two circuits can give the same output for one input while being different operations. Characterises X, Y, Z, H, S and T purely by experiment, including rotation axis, angle, phase and whether each is self-inverse. An exhaustive search finds six optimal 4-gate paths through a five-state navigation challenge. The final task shows where the Bloch sphere breaks down: for Bell, GHZ and W states the single-qubit vectors shrink toward the origin.

### 2. Deutsch algorithm

Builds all four one-bit oracles and classifies each as constant or balanced with a single query, on every one of 1024 shots. Preparing the ancilla as |0⟩, |1⟩, |+⟩ and |−⟩ shows that only |−⟩ produces phase kickback. A depolarizing noise sweep shows the correct answer falling from 97 to 60 percent as noise grows. Three different gate sequences turn out to implement the same oracle unitary.

### 3. Bernstein-Vazirani algorithm

Recovers hidden strings such as 1011 and 11001 on every shot with one oracle query, against one query per bit classically. The phase kickback study compares all four ancilla preparations. Under noise, accuracy drops from about 94 to 86 percent as the string grows from 2 to 6 bits, while the hidden string stays the dominant outcome.

### 4. Simon's algorithm

Every measured string satisfies y · s = 0 (mod 2), and solving the resulting equations over GF(2) recovers the hidden XOR period. A black-box oracle with a secret string is reverse engineered and verified on random inputs. A classical collision search is compared with the quantum attack: for six bits the classical search needed 15 queries against 5. A noise and scaling study covers n = 2 to 6.

### 5. Grover's search algorithm

A single Grover iteration finds the marked state with certainty in a four-item search, for every possible target. Sweeping the iteration count for N = 4, 8 and 16 confirms the optimum of ⌊(π/4)√N⌋, followed by the drop from over-rotation. With two marked states the iteration count falls, and with M = N/2 no iteration helps. Under noise, success falls from 91 percent at 2 qubits to 3 percent at 5, because the circuit depth grows quickly.

### 6. Shor's algorithm

Factors 15 with base 7. The classical sequence 1, 7, 4, 13 gives the period 4. Modular multiplication gates are built as permutation matrices and checked for unitarity. The period-finding circuit, with controlled multiplications and an inverse QFT, puts its measurements on 0, 4, 8 and 12. Continued fractions and a GCD step then recover and verify 15 = 3 × 5. The record also compares the classical and quantum approaches and studies noise and control-register size.

## Running the notebooks

The notebooks already contain their outputs. To re-run them, use Python 3.10 or later:

```bash
pip install qiskit qiskit-aer matplotlib pylatexenc
jupyter notebook
```

Each notebook also installs its own dependencies in its first cell, so they run as-is on Google Colab.

The results were produced with Qiskit 2.6 and Qiskit Aer 0.18. Most circuits use 1024 shots. Simulator counts are random, so a re-run will shift histograms by a few shots, but every conclusion in the notebooks holds across runs.

## Conventions

- **Bit order.** Measured bit strings follow Qiskit's convention, with qubit 0 on the right. Oracles read hidden strings from the right, so a measured string reads exactly as the hidden string is written.
- **Noise models.** Noise is illustrative depolarizing error, typically 1 to 2 percent on single-qubit gates and 3 to 5 percent on CX. It does not model any calibrated device.
- **Speedup claims.** A classical simulator cannot show a quantum speedup. The query counts here demonstrate each algorithm's mechanism, not wall-clock advantage.

## Author

Engineered by **Ritesh Roshan Sahoo** (DL.AI.U4AID24036) for the course *23AID303 Quantum Computing and Algorithms* at Amrita Vishwa Vidyapeetham. The course faculty is Dr. Mrittunjoy G. Majumdar, and the lab instructor is Sakshi.

Contact: riteshroshansahoo01@gmail.com
