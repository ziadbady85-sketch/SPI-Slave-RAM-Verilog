# SPI Slave with Single-Port RAM

A synthesizable RTL implementation of an **SPI Slave** interfaced with a **Single-Port RAM**, developed in **Verilog HDL**. The design allows an SPI Master to perform memory read and write transactions through a standard SPI interface.

---

## Overview

This project implements an SPI Slave controller that receives serial commands from an SPI Master through the MOSI line, decodes them using a finite state machine (FSM), and communicates with an internal Single-Port RAM.

Write operations store data into memory, while read operations retrieve stored data and transmit it back to the master through the MISO line.

The project is fully synthesizable and follows a modular RTL design methodology.

---

## Features

- FSM-based SPI Slave Controller
- Standard SPI Serial Communication
- Single-Port RAM Interface
- Memory Read Operation
- Memory Write Operation
- Serial-to-Parallel Data Reception
- Parallel-to-Serial Data Transmission
- Parameterized Memory Depth
- Modular RTL Architecture
- Synthesizable Verilog Design

---

## Block Diagram

<p align="center">
  <img src="images/block_diagram.png" width="700">
</p>

---

## Architecture

```
                +---------------------+
                |     SPI Master      |
                +----------+----------+
                           |
                 MOSI / MISO / SS_n
                           |
                           v
                +---------------------+
                |      SPI Slave      |
                |   FSM Controller    |
                +----------+----------+
                           |
                 rx_data / tx_data
                           |
                           v
                +---------------------+
                |   Single-Port RAM   |
                +---------------------+
```

---

## FSM States

| State | Description |
|--------|-------------|
| IDLE | Waits for Slave Select |
| CHK_CMD | Decodes incoming command |
| WRITE | Receives write address/data |
| READ_ADD | Receives read address |
| READ_DATA | Sends requested data through MISO |

---

## Project Structure

```
SPI_Slave_With_Single_Port_RAM/
│
├── RTL/
│   ├── slave.v
│   ├── RAM.v
│   └── Spi_Wrapper.v
│
├── TB/
│   └── spi_tb.v
│
├── Simulation/
│   ├── Waveforms
│   └── Screenshots
│
├── Vivado/
│   ├── Elaboration
│   ├── Synthesis
│   └── Implementation
│
├── Lint/
│   └── Lint_Report.pdf
│
├── Images/
│   ├── block_diagram.png
│   ├── fsm.png
│   └── waveform.png
│
└── README.md
```

---

## Verification

The design was verified using a dedicated Verilog testbench covering multiple operating scenarios, including:

- Memory Write Transactions
- Memory Read Transactions
- FSM State Transitions
- SPI Data Reception
- SPI Data Transmission
- RAM Read/Write Operations

Simulation was performed using **Xilinx Vivado**.

---

## Design Flow

```
RTL Design
      │
      ▼
Testbench Development
      │
      ▼
Functional Simulation
      │
      ▼
RTL Linting
      │
      ▼
RTL Elaboration
      │
      ▼
Logic Synthesis
      │
      ▼
Implementation
```

---

## Tools

- Verilog HDL
- Xilinx Vivado
- Questa Lint

---

## Applications

- FPGA-Based Systems
- Embedded Systems
- Memory Interfaces
- Digital Communication
- RTL Design Practice

---

## Future Improvements

- Support for all SPI Modes (CPOL/CPHA)
- Configurable Data Width
- Configurable Memory Depth
- Burst Read/Write Transactions
- SPI Timing Optimization

---

## Author

**Ziad Mohamed**

RTL Design | Digital Design | FPGA | IC Design

---

## License

This project is available for educational and learning purposes.
