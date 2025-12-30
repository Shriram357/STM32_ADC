# STM32 Timer Triggered ADC with DMA and UART

## Overview
This project implements a hardware-driven data acquisition system on the STM32F303RE.
A timer running at 100 Hz triggers ADC conversions. ADC results are transferred to memory
using DMA, and on DMA transfer completion the data is transmitted via UART and displayed
on a serial terminal (PuTTY).

## Hardware Used
- STM32F303RE (Nucleo / Blackpill compatible)
- On-board ST-LINK Virtual COM Port
- PC with PuTTY for serial monitoring

## Functional Flow
1. TIM2 is configured to overflow every 10 ms (100 Hz).
2. Timer update event (TRGO) triggers ADC conversion.
3. ADC performs 12-bit conversion on the selected analog channel.
4. DMA transfers ADC result directly to RAM.
5. DMA transfer-complete interrupt occurs.
6. ADC value is transmitted over UART.
7. Serial terminal displays ADC values in real time.

## Sampling Details
- ADC Resolution: 12-bit (0–4095)
- Reference Voltage: 3.3 V
- Sampling Rate: 100 Hz
- Data Transfer: DMA (Circular mode)

## Example Output (PuTTY)
ADC: 293  
ADC: 297  
ADC: 300  

## Tools Used
- STM32CubeIDE
- HAL drivers
- PuTTY (serial terminal)

## How to Run
1. Open the `.ioc` file using STM32CubeIDE.
2. Build the project.
3. Flash the code to the board.
4. Open PuTTY at 115200 baud on the ST-LINK COM port.

## Notes
- The ADC input was left floating during testing; hence small variations in readings.
- Timer-triggered ADC with DMA ensures deterministic sampling and minimal CPU usage.
