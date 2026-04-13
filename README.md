# SPI Slave with RAM Wrapper – Verilog RTL Design

A complete Verilog implementation of an **SPI slave interface connected to single-port RAM**, designed as a modular RTL system with command decoding, memory read/write transactions, and serial data transmission over MISO.

This project demonstrates **protocol-based digital design, FSM implementation, memory interfacing, and verification using a directed testbench**.

---

## 📌 Overview
The design integrates three main RTL blocks:

- **SPI Slave Controller**
- **Single-Port RAM**
- **Top Wrapper Module**

The SPI slave receives serial commands on **MOSI**, decodes the operation, and communicates with RAM for:

- Write Address
- Write Data
- Read Address
- Read Data

Read data is serialized back through **MISO**.

---

## 🏗️ RTL Architecture

### 1) SPI Slave (`slave.v`)
Implements the SPI protocol receive/transmit logic using an FSM.

### FSM States
- `IDLE`
- `CHK_CMD`
- `WRITE`
- `READ_ADD`
- `READ_DATA`

### Responsibilities
- Serial-to-parallel conversion
- Command decoding
- Address/data packet capture
- Generating `rx_valid`
- Sending RAM data serially on `MISO`

---

### 2) RAM (`RAM.v`)
A synchronous single-port memory with command-based access.

### Supported Commands
| Command | Function |
|---|---|
| `00` | Store write address |
| `01` | Write data |
| `10` | Store read address |
| `11` | Output read data |

---

### 3) Wrapper (`Spi_Wrapper.v`)
Top-level integration of:
- SPI slave
- RAM
- handshake signals
- serial output path

This module represents the complete system-level SPI memory peripheral.

---

## 🔄 Data Flow
1. Master sends serial command through `MOSI`
2. SPI slave decodes packet
3. `rx_valid` triggers RAM transaction
4. RAM performs read/write
5. Read data returned as `tx_data`
6. SPI slave serializes output on `MISO`

---

## 🧪 Verification
A dedicated testbench validates:

- Write address transaction
- Write data transaction
- Read address transaction
- Read data transaction
- Multiple consecutive read operations
- RAM initialization using `$readmemh`

### Testbench Features
- Fully clock-driven
- Directed stimulus
- Memory preload from file
- Internal memory access checks
- Sequential SPI transaction validation

---

