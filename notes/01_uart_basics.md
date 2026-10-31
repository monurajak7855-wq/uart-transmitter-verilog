# Lesson 01: Introduction to UART

**Project:** UART Transmitter Design using Verilog HDL  
**Learning Phase:** UART Fundamentals  
**Status:** Concepts Covered

---

## 1. What is UART?

UART stands for Universal Asynchronous Receiver/Transmitter.

It is a hardware communication mechanism used to transfer digital data between two electronic devices.

UART uses serial communication, meaning data bits are transmitted one after another through a communication line.

Examples of UART applications:
- Microcontroller-to-computer communication
- GPS modules
- Bluetooth modules
- Serial debugging interfaces
- Embedded systems

## 2. Why do we need UART?

Electronic devices process information in binary form (0s and 1s).

When two devices need to exchange information, they require a communication mechanism.

UART provides a simple way to transfer binary information between devices without requiring a shared clock signal.

## 3. Serial vs Parallel Communication

### Serial Communication

- Data bits are transmitted sequentially.
- Usually requires fewer data wires.
- UART uses serial communication.

Example:

`1 → 0 → 1 → 0 → 1 → 1 → 0 → 0`

### Parallel Communication

- Multiple data bits are transmitted simultaneously.
- Requires multiple data wires.
- An 8-bit parallel interface can transfer 8 bits at once.

## 4. UART Communication Pins

UART commonly uses three connections:

| Pin | Full form | Function |
|---|---|---|
| TX | Transmit | Sends data |
| RX | Receive | Receives data |
| GND | Ground | Common electrical reference |

For two-way communication:

- Device A TX connects to Device B RX.
- Device B TX connects to Device A RX.
- Both devices share GND.

## 5. What is a UART Frame?

A UART frame is the complete structure used to transmit one data unit.

For this project, we use the 8-N-1 configuration.

8-N-1 means:

- 8 data bits
- N = No parity bit
- 1 stop bit

The frame consists of:

1. Start bit
2. Eight data bits
3. Stop bit

### Start Bit

- The UART TX line is normally HIGH (logic 1) when idle.
- Transmission begins when TX goes LOW (logic 0).
- This LOW signal is called the start bit.
- It indicates the beginning of a new frame.

### Data Bits

- The actual information is transmitted in this section.
- Our project uses 8 data bits.
- UART transmits the least significant bit first.

### Stop Bit

- The stop bit is logic HIGH (1).
- It indicates the end of the frame.
- The TX line returns to its idle HIGH state.

## 6. Understanding LSB-First Transmission

LSB stands for Least Significant Bit.

Consider the ASCII character 'A'.

Decimal representation: 65  
Hexadecimal representation: 0x41  
Binary representation: 01000001

UART transmits the data bits starting from the least significant bit.

Therefore, the transmission order is:

`1 → 0 → 0 → 0 → 0 → 0 → 1 → 0`

Important: The order in which data bits are transmitted is different from how the binary number is normally written.

## 7. What is Baud Rate?

Baud rate describes the number of symbols transmitted per second.

In a basic binary UART, each symbol represents one bit, so baud rate and bit rate have the same numerical value.

Examples:

- 9600 baud
- 19200 baud
- 115200 baud

Bit duration:

T_bit = 1 / Baud Rate

For 9600 baud:

T_bit = 1 / 9600

T_bit ≈ 104.17 microseconds

This means each bit is transmitted over approximately 104.17 microseconds.

## 8. Why is UART Asynchronous?

UART does not use a shared clock signal between the transmitter and receiver.

Instead:

- Both devices agree on a baud rate.
- The receiver detects the start bit.
- The receiver uses its own clock to sample the incoming data bits at the expected times.

This is why UART is called asynchronous communication.

## 9. What I Learned

1. UART is used for serial data communication.
2. UART transmits data one bit at a time.
3. TX is used to transmit data and RX is used to receive data.
4. UART normally has an idle HIGH state.
5. A start bit indicates the beginning of transmission.
6. UART 8-N-1 contains eight data bits, no parity bit, and one stop bit.
7. Data is transmitted LSB first in our chosen configuration.
8. Baud rate determines the transmission symbol rate.
9. UART is asynchronous because there is no shared clock between devices.

## 10. Questions to Investigate in the Next Lesson

1. How does a UART receiver identify the beginning of a frame?
2. How does the receiver know when to read each data bit?
3. What is the relationship between clock frequency and baud rate?
4. How long does it take to transmit one complete UART frame?
5. What happens if transmitter and receiver use different baud rates?

## 11. References

- Analog Devices: UART communication protocol  
  https://www.analog.com/en/resources/analog-dialogue/articles/uart-a-hardware-communication-protocol.html

- EDA Playground  
  https://www.edaplayground.com/

- Icarus Verilog  
  https://steveicarus.github.io/iverilog/
