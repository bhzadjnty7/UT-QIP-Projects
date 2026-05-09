<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:0f2027,50:203a43,100:2c5364&height=200&section=header&text=Quantum%20Information%20Processing%20Projects&fontSize=35&fontColor=ffffff&animation=fadeIn&fontAlignY=35"/>
</p>

# UT-QIP-Projects
Quantum Information Processing course projects (Fall 1403) at the University of Tehran under the supervision of Prof. Ahmad Khonsari. Implementation of quantum circuits, Bloch sphere visualization, measurement techniques, and Grover's search algorithm for solving a 2×2 binary Sudoku puzzle using Qiskit.

# Quantum Information Processing Projects

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Qiskit](https://img.shields.io/badge/Qiskit-1.3.1-blue)](https://qiskit.org/)
[![Python](https://img.shields.io/badge/Python-3.12+-green)](https://www.python.org/)

This repository contains the implementation of three hands-on projects for the **Quantum Information Processing** course taught by **Professor Ahmad Khonsari** at the **University of Tehran (Fall 1403)**. Each project is implemented using **Qiskit** within a **Jupyter Notebook** environment, covering fundamental concepts of quantum computing from basic circuit design to Grover's search algorithm.

---

## Table of Contents

1. [Abstract](#abstract)
2. [Key Features](#key-features)
3. [Project Workflow](#project-workflow)
4. [Technical Architecture](#technical-architecture)
5. [Installation and Setup](#installation-and-setup)
6. [Project 0: Environment Setup and Qiskit Introduction](#project-0-environment-setup-and-qiskit-introduction)
7. [Project 1: Quantum Circuits, Bloch Sphere, and Measurement](#project-1-quantum-circuits-bloch-sphere-and-measurement)
8. [Project 2: Grover's Algorithm for 2×2 Sudoku](#project-2-grovers-algorithm-for-22-sudoku)
9. [Usage](#usage)
10. [Results](#results)
11. [References](#references)
12. [Acknowledgements](#acknowledgements)
13. [License](#license)

---

## Abstract

Quantum Information Processing (QIP) is a rapidly advancing field that leverages the principles of quantum mechanics for information processing tasks. This course, taught by **Professor Ahmad Khonsari** at the **University of Tehran (Fall 1403)** , provides a comprehensive introduction to quantum computing concepts, algorithms, and their implementation using the **Qiskit** framework. The three projects in this repository are designed to bridge theoretical knowledge with practical implementation, covering key topics such as:

- **Project 0:** Setting up a complete quantum development environment (Anaconda, Jupyter Notebook, Qiskit) and running a simple introduction to quantum circuits.
- **Project 1:** Designing quantum circuits with **Hadamard** and **CNOT** gates, visualizing qubit states on the **Bloch sphere**, performing measurements, and analyzing quantum state evolution.
- **Project 2:** Implementing **Grover's search algorithm** using phase‑kickback oracles and amplitude amplification to solve a constraint satisfaction problem — a 2×2 binary Sudoku puzzle.

All projects are delivered as **Jupyter Notebooks** (`.ipynb` files) with integrated explanations, code, and visual outputs, together with a brief report summarising the key findings.

---

## Key Features

* **Complete Quantum Development Environment**  
  Step‑by‑step instructions for setting up **Anaconda**, **Jupyter Notebook**, and **Qiskit**, including kernel configuration for project‑specific runs.

* **Quantum Circuit Construction**  
  Implementation of fundamental quantum gates (Hadamard, CNOT, etc.) and multi‑qubit circuits, demonstrating superposition and entanglement.

* **State Visualization**  
  Use of Qiskit’s `plot_bloch_multivector` to display qubit states on the Bloch sphere, providing intuitive insight into quantum state evolution.

* **Measurement and Statistical Analysis**  
  Integration of classical bits to store measurement results and execution of multiple shots (`qasm_simulator`) to produce histogram outputs, highlighting the probabilistic nature of quantum mechanics.

* **Grover’s Search Algorithm**  
  Complete implementation of Grover’s algorithm — including oracle design using **phase kickback**, the **diffusion operator**, and simulation — to efficiently find all valid solutions to a 2×2 binary Sudoku puzzle (a small‑scale constraint satisfaction problem).

* **Modular and Educational**  
  The code is structured for clarity, with detailed comments and explanations, making it suitable for students and researchers new to quantum computing.

---

## Project Workflow

The end‑to‑end workflow for the projects is illustrated in the figure below. It covers environment setup, circuit design, simulation, visualisation, and submission.
```
[Environment Setup] → [Anaconda + Jupyter + Qiskit Installation]
↓
[Project 0] → [Basic quantum circuit: Hadamard + CNOT]
↓
[Project 1] → [Circuit expansion, Bloch sphere, measurements, statistical analysis]
↓
[Project 2] → [Oracle construction, phase kickback, Grover’s algorithm, simulation]
↓
[Reporting] → [.ipynb notebooks + summary report → compressed as .zip]

```
---

## Technical Architecture

The technical architecture consists of the following key components:

* **Development Environment:** **Anaconda** distribution to manage Python packages, **Jupyter Notebook** for writing and executing code with integrated markdown cells, and a dedicated kernel named `qipCourse` for this project.
* **Quantum Computing Framework:** **Qiskit** — an open‑source SDK for working with quantum computers at the level of circuits, pulses, and algorithms.
* **Simulation Backends:**  
  * `Statevector` simulator for exact state visualisation (Bloch spheres).  
  * `qasm_simulator` for measurement statistics over many shots.
* **Oracle Construction:** Custom classical logic circuits (checking Sudoku row/column uniqueness) embedded into a quantum oracle using the **phase‑kickback** technique.
* **Amplitude Amplification:** The **diffusion operator** (Grover’s iterator) to amplify the probability amplitudes of valid solution states.

---

## Installation and Setup

To set up the environment and run these projects, follow the steps below.

### 1. Clone the Repository
```bash
git clone https://github.com/bhzadjnty7/UT-QIP-Projects.git
cd project0
```
### 2. Install Anaconda (if not already installed)
Download and install Anaconda from the official website.

### 3. Create and Activate a New Conda Environment (Optional but Recommended)
```bash
conda create -n qip-course python=3.12
conda activate qip-course
```
### 4. Install Jupyter Notebook and Qiskit
```bash
pip install jupyter notebook
pip install qiskit[visualization] --use-feature=2020-resolver
```
### 5. Register the Kernel for the Project
```bash
pip install --user ipykernel
python -m ipykernel install --user --name=qipCourse
```
### 6. Launch Jupyter Notebook
```bash
jupyter notebook
```
After launch, select the qipCourse kernel from the Kernel → Change kernel menu.

### 7. Verify the Installation
Run the following code in a new notebook cell to confirm that everything is set up correctly:

``` python
import numpy as np
from qiskit import *
%matplotlib inline

circ = QuantumCircuit(3)
circ.h(0)
circ.cx(0, 1)
circ.cx(0, 2)
circ.draw('mpl')
```
You should see a three‑qubit circuit diagram.

---
## Project 0: Environment Setup and Qiskit Introduction
### **Objective:**

Set up a fully functional quantum development environment and run a basic quantum circuit.

Key tasks:

* Install Anaconda, Jupyter Notebook, and Qiskit.

* Create and configure a custom kernel (qipCourse).

* Execute a simple circuit that applies a Hadamard gate on qubit 0 and two CNOT gates to create a GHZ‑like state.

* Verify the installation by generating and capturing the circuit output.

### **Deliverable:**
A screenshot of the executed circuit (as shown in the project description) together with a working .ipynb notebook.

---
## Project 1: Quantum Circuits, Bloch Sphere, and Measurement
Objective:
Build and analyse quantum circuits that demonstrate superposition, entanglement, measurement, and statistical behaviour.

### **Key tasks:**

* Define a quantum circuit with 3 qubits and 2 classical bits.

* Apply Hadamard gates to qubits 0 and 1 to create superposition states.

* Apply a CNOT gate between qubits 1 (control) and 2 (target) to generate entanglement.

* Use Statevector.from_instruction and plot_bloch_multivector to visualise the qubit states on the Bloch sphere.

* Measure qubits 1 and 2, storing the results in the two classical bits.

* Run the circuit on the qasm_simulator for 1000 shots and plot a histogram of the measurement outcomes.

* Analyse the observed Bloch sphere and histogram outputs.

### **Analysis questions (included in the report):**

1. Why are the Bloch spheres for qubits 1 and 2 featureless (no information) after applying the Hadamard and CNOT gates?

2. In which basis are the measurements performed? How can you change the measurement basis?

3. Extend the circuit to include qubit 0 in a |+⟩ state and qubits 1,2 in the GHZ state (generalisation of Bell state to three qubits). Extract the statevector and explain the result.

### **Deliverable:**
A .ipynb notebook containing all code, outputs, and answers to the questions, along with a brief report (max 2 pages).

---
## Project 2: Grover's Algorithm for 2×2 Sudoku
### **Objective:**
Implement **Grover’s search algorithm** to solve a 2×2 binary Sudoku puzzle.

### **Problem definition:**
We have a 2×2 grid where each cell can be 0 or 1. The puzzle must satisfy two simple rules:

* No row may contain the same value twice.

* No column may contain the same value twice.
```table
v0	v1
v2	v3
```
We need a quantum circuit that finds all valid assignments to the four binary variables.

### **Key tasks:**

* Oracle design:
Build a classical checking circuit (using auxiliary qubits) that outputs 1 if the current assignment violates the Sudoku rules (i.e., if a row or column contains identical values). Then convert this check into a quantum **oracle** using the **phase‑kickback** trick: instead of flipping an auxiliary qubit, we flip the phase of the entire computational basis state when the check fails (or equivalently, when it passes). This oracle marks the valid solution states with a negative phase.

* Diffusion operator:
Implement the Grover diffusion operator that performs inversion about the mean, amplifying the amplitude of the marked (valid) states.

* Grover’s algorithm:
Combine the oracle and the diffusion operator into Grover’s iterator. Determine the optimal number of iterations and run the circuit on the qasm_simulator.

### **Analysis:**
Verify that the output probability distribution peaks at the valid Sudoku solutions. The solutions for the 2×2 binary Sudoku are the assignments where each row and each column contains exactly one 0 and one 1.

### **Deliverable:**
A .ipynb notebook implementing the oracle, the diffusion operator, and Grover’s search, together with simulation results and a short explanation of the oracle’s working principle.

---
## Usage
After completing the installation steps, open the desired project notebook:

```bash
jupyter notebook Project0_Environment_Setup.ipynb
jupyter notebook Project1_Quantum_Circuits.ipynb
jupyter notebook Project2_Grover_Sudoku.ipynb
```
Run each cell sequentially. The notebooks include markdown cells that explain the purpose of each code block and the expected outputs.

---
## Results
### **Project 0**
* Successful installation and execution of a three‑qubit circuit with Hadamard and CNOT gates, producing a clear circuit diagram.

### **Project 1**
* The Bloch sphere plots show that qubits 1 and 2 are entangled and do not have a definite individual state – hence they appear as spheres without information.

* The measurement histogram for 1000 shots shows that the classical bits (c0, c1) are always found in the states 00 or 11 (or analogous patterns depending on the circuit), confirming the expected correlated behaviour.

* Extension to the three‑qubit GHZ state yields a statevector with equal superposition of |000⟩ and |111⟩.

### **Project 2**
* The oracle correctly marks the valid Sudoku solutions (e.g., v0v1v2v3 = 0110 and 1001 — check the exact constraints). The phase‑kickback mechanism is successfully demonstrated.

* After applying Grover’s iterator the appropriate number of times, the measurement probabilities for the valid states are significantly amplified, and the simulation outputs the correct solutions with high probability.

---
## References
**1. Anaconda Distribution**

https://www.anaconda.com/download

**2. Qiskit** – Open‑Source Quantum Development

https://qiskit.org/

**3. Grover, L. K. (1996)**. “A fast quantum mechanical algorithm for database search.” Proceedings of the 28th Annual ACM Symposium on Theory of Computing, pp. 212–219.

DOI:10.1145/237814.237866

**3. IBM Quantum Learning** – Qiskit Textbook

https://github.com/Qiskit/textbook

**4. Nielsen, M. A., & Chuang, I. L. (2010)**. Quantum Computation and Quantum Information: 10th Anniversary Edition. Cambridge University Press.

**5. Soham Chatterjee – Qiskit Quantum Algorithms**

https://github.com/sohamch08/Qiskit-Quantum-Algo (reference for the 2×2 Sudoku problem statement)

---
## Acknowledgements
* Professor Ahmad Khonsari for his insightful lectures and guidance throughout the Quantum Information Processing course.

* Teaching Assistants (Mehrinezhad and Mardin Neichi) for providing detailed project descriptions and helpful hints.

* IBM Qiskit Team for developing and maintaining the Qiskit framework, which made these projects possible.

* Open‑Source Community for the tools and libraries that support quantum computing education.

---
## License
This project is licensed under the **MIT License**. You are free to use, modify, and distribute this code for educational and research purposes. See the LICENSE file for more details.

<div align="center"> <sub>Built with ❤️ using Qiskit and Jupyter Notebooks</sub> </div> 
