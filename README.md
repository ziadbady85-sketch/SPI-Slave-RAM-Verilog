# SPI Slave with RAM Interface

Simple SPI Slave RTL design in Verilog connected to an internal RAM.

## Project Structure

* rtl/slave.v
* rtl/RAM.v
* rtl/Spi_Wrapper.v
* tb/Spi_Wrapper_tb.v

## Features

* 10-bit SPI frame
* FSM controller
* RAM read/write
* MISO transmission
* Testbench included

## FSM States

* IDLE
* CHK_CMD
* WRITE
* READ_ADD
* READ_DATA

## Tools

* Verilog HDL
* ModelSim / QuestaSim
* Vivado

## Status

RTL Completed
Testbench Verified
Read/Write Working
