# Grover's algorithm

From simple linear algebra to quantum gates — let's see how a phase flip turns into a high probability of finding the marked state!

In this notebook, I implement Grover's algorithm twice: first with NumPy matrices, then with a Qiskit circuit. The idea is to make the oracle, inversion about the average, and amplitude amplification visible step by step.

**[Open the notebook →](grover_algorithm_basic.ipynb)**

## What's inside

| Implementation | Qubits | Grover iterations | Execution |
| --- | ---: | ---: | --- |
| Linear algebra | 5 | 4 | Explicit state vector and diffusion matrix |
| Quantum circuit | 10 | 24 | Qiskit Aer, 1,000 measurement shots |

Both examples include minimal plots of the probability distribution at the start, midpoint, and end, plus the marked state's probability after every iteration. The simulation is compared with the theoretical curve. Since the outcomes are discrete basis states, these distributions are **probability mass functions (PMFs)**.

## Run it

Install the dependencies in the Python environment used by your notebook:

```bash
python -m pip install numpy matplotlib qiskit qiskit-aer
```

Open `grover_algorithm_basic.ipynb` in Jupyter or VS Code and run all cells from top to bottom. The plots are also saved in the notebook, so they can be viewed directly on GitHub. No IBM Quantum account is needed.

The Qiskit example chooses a new marked state each time, and the sampled counts can vary. Its plots use exact statevector probabilities before measurement.

## A few things to keep in mind

The oracle is given a marked state so we can study the amplification. For an actual search problem, the oracle would encode a condition that recognizes valid solutions.

Both implementations run locally on a classical computer. They illustrate Grover's algorithm, but do not demonstrate a runtime speedup over classical search. Full statevector simulation stores $2^n$ amplitudes; the dense matrices in the NumPy example store $4^n$ entries each. Recording the circuit's evolution adds simulation work, so keep the examples small.

My next step is to try a small circuit on IBM hardware and see how noise affects the result.

## References

- [Grover's original paper](https://arxiv.org/abs/quant-ph/9605043)
- [IBM's Grover tutorial](https://quantum.cloud.ibm.com/docs/en/tutorials/grovers-algorithm)
- [Qiskit's bit-ordering guide](https://quantum.cloud.ibm.com/docs/en/guides/bit-ordering)
