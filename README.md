# 101-Sequence-Detector-Verilog
Implementation of a 101 sequence detector using Verilog (Mealy FSM) including overlapping and non-overlapping designs with testbench verification.
# 101 Sequence Detector using Verilog HDL

## Introduction

This project implements a **101 sequence detector** using **Verilog HDL** and a **Mealy Finite State Machine (FSM)**.
The detector monitors a serial input stream and produces an output when the pattern **101** is detected.

Two versions of the detector are implemented:

* **Overlapping Sequence Detector**
* **Non-Overlapping Sequence Detector**

Testbenches are included to simulate and verify the functionality of the design.

---

## Concepts Used

* Verilog Hardware Description Language (HDL)
* Finite State Machine (FSM) Design
* Mealy Machine Architecture
* Sequential Logic Design
* Digital State Encoding
* Simulation and Waveform Analysis

---

## Repository Structure

```text
101-Sequence-Detector-Verilog/
│
├── 01overlapping_detector.v
├── 02tb_overlapping.v
├── 03overlap.jpeg
│
├── 04non_overlapping_detector.v
├── 05tb_non_overlapping.v
├── 06non_overlap.jpeg
│
└── README.md
```

* **Design files** contain the FSM implementation in Verilog.
* **Testbench files** apply input sequences and verify detector outputs.

---

## Working Principle

The detector is implemented using a **Mealy FSM**, where the output depends on both the **current state** and the **input signal**.

### States

| State | Binary | Description   |
| ----- | ------ | ------------- |
| S0    | 00     | Initial state |
| S1    | 01     | Detected `1`  |
| S2    | 10     | Detected `10` |

### Detection Logic

When the FSM is in state **S2** and the input is **1**, the sequence **101** is detected and the output becomes **1**.

### Overlapping Detector

After detecting **101**, the FSM transitions to **S1**, allowing the last `1` to start a new sequence.

Example:

```
Input : 10101
Output: 00101
```

### Non-Overlapping Detector

After detecting **101**, the FSM resets to **S0**, preventing reuse of bits from the previous sequence.

Example:

```
Input : 10101
Output: 00100
```

---

## Simulation

Simulation was performed using **EDA Playground**.

The testbench:

* Generates the clock signal
* Applies input sequences (e.g., `10101`)
* Displays signal values using `$monitor`
* Produces waveform outputs for verification

Key signals observed during simulation:

```
clk
rst
x
state
out
```

Waveforms help visualize the **state transitions** and confirm correct detection of the sequence.

---

## Tools Used

* **Verilog HDL**
* **EDA Playground**
* **EPWave (Waveform Viewer)**
* **GitHub** for version control and project hosting

---

## Author

**KUMARACHAR . M**
Electronics and Communication Engineering
