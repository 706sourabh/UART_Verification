# UART_Verification
UART Verification Environment (SystemVerilog)

This repository contains a SystemVerilog Verification Environment for a UART (Universal Asynchronous Receiver Transmitter).  
The environment is built using transaction-level modeling with generator, driver, monitor, scoreboard, and environment class, following a UVM-style structure.

---

## Project Structure
- **design/** → RTL for UART (TX, RX, and Top module)  
- **tb/** → Testbench with SystemVerilog classes (generator, driver, monitor, scoreboard, environment)  
- **docs/** → Documentation and supporting material  

---

## Design Overview
- **UART Top (design/uart_top.sv)**  
  - Connects transmitter (`uarttx`) and receiver (`uartrx`) modules.  
  - Parameterized by `clk_freq` and `baud_rate`.  

- **Transmitter (uarttx)**  
  - Serializes 8-bit parallel data and transmits bit by bit.  
  - Generates done signal after transmission.  

- **Receiver (uartrx)**  
  - Deserializes incoming serial data into 8-bit parallel format.  
  - Generates done signal after reception.  

- **Interface (uart_if)**  
  - Bundles UART signals for testbench components.  

---

## Testbench Architecture
- **Transaction** → Defines UART operation (read/write) and data fields.  
- **Generator** → Creates randomized transactions.  
- **Driver** → Drives UART TX/RX operations into the DUT.  
- **Monitor** → Observes DUT activity and collects transmitted/received data.  
- **Scoreboard** → Compares expected vs actual data and reports results.  
- **Environment** → Connects all components and manages simulation flow.  

---

## Running the Simulation

### Option 1: Run on **EDA Playground**
- Copy `design/` files into the *Design* section.  
- Copy `tb/tb.sv` into the *Testbench* section.  
- Select **SystemVerilog** and a simulator (e.g., Icarus/Modelsim).  
- Run → View waveforms in the viewer.  

### Option 2: Run Locally with **Xilinx Vivado**
1. Open Vivado and create a new project.  
2. Add RTL files from `design/` and testbench files from `tb/`.  
3. Set the top module as `tb`.  
4. Run behavioral simulation and view waveforms.  
