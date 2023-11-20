# Qiskit-IonQ Transpilation Bug Fix Repository

## Overview
This repository demonstrates a transpilation bug encountered when using Qiskit with IonQ quantum computing machines. The bug affects the transpilation of quantum circuits into IonQ's native gateset.

## Setup
Before using the code in this repository, ensure that you have the necessary packages installed. Run the following command:

```bash
pip install -U qiskit \
    qiskit_ionq \
    matplotlib \
    pylatexenc
```

Then to test the bug fix, use the `qiskit-ionq` submodule:

```bash
git submodule init
git submodule update
git pull --recurse-submodules
```

## Usage
To recreate this bug, open `demo.ipynb` or follow these steps:

1. **Import Required Libraries**: Ensure you import the necessary libraries, including `qiskit_ionq` and `os`.

2. **API Key**: Obtain your IonQ API key from [IonQ Cloud](https://cloud.ionq.com/settings/keys). The code checks for the API key in your environment variables and prompts for it if not found.

3. **Backend Specification**: Set up the backend using `qiskit_ionq.IonQProvider` and specify the `ionq_qpu.aria-1` backend with the `native` gateset.

4. **Quantum Circuit**: Create your quantum circuit using Qiskit. An example circuit with two qubits is included.

5. **Transpilation**: Attempt to transpile the circuit to IonQ's native gateset. If the bug is encountered, an error will be raised.

6. **Running the Circuit**: Once the transpilation issue is resolved, you can send the job to the backend and plot the results.

## Bug Description and Fix
The bug is triggered during the transpilation of certain quantum gates (like 'barrier', 'h', 'cx', 'measure') to IonQ's target basis gates. The fix should involve updating the IonQ gate definitions or adjusting the transpilation process to accommodate IonQ's native gateset correctly.
