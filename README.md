# Bell State Noise Simulation

This project is based on my bachelor’s monograph at Nangarhar University.

I used Qiskit Aer to compare a custom noise model with the FakeVigoV2 noise model. The aim was to see how the two models change the results of a Bell-state circuit.

## Bell-State Circuit

The circuit prepares this Bell state:

|Φ+⟩ = (|00⟩ + |11⟩) / √2

It uses a Hadamard gate on the first qubit, followed by a CNOT gate.

## Noise Models

I tested the circuit with two noise models:

- **Custom model:** uses T1, T2, depolarizing noise, and readout errors.
- **FakeVigoV2 model:** uses saved information from the FakeVigoV2 backend.

FakeVigoV2 is not a live IBM quantum computer. It is a fake backend made from saved device information.

## Simulation

I ran each model 10 times with 10,000 shots in every run.

In my monograph, I used this value:

P(00) + P(11)

I called it Bell Measurement Fidelity, or BMF. It shows how often the circuit gives the expected |00⟩ and |11⟩ outcomes.

This value is not full quantum-state fidelity because it only checks the measurement results in the computational basis.

## Results

| Model | P(00) + P(11) | Standard Deviation | P(01) + P(10) |
|---|---:|---:|---:|
| Custom model | 0.8040 | ±0.0034 | 0.1960 |
| FakeVigoV2 model | 0.9018 | ±0.0030 | 0.0982 |

In this simulation, the FakeVigoV2 model gave more |00⟩ and |11⟩ results than the custom model.

## Figure

![Simulation results](figures/Bell_state_bmf_analysis.png)

The figure compares the results of both noise models.

## Run the Code

Install the required packages:

```bash
pip install -r requirements.txt
