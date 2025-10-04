
VSDBabySoC is a compact yet highly capable System on Chip (SoC) based on the RISC-V architecture. The primary objective of designing this small-scale SoC is to facilitate the simultaneous testing of three open-source intellectual property (IP) cores for the first time while also calibrating its analog components. The VSDBabySoC incorporates an RVMYTH microprocessor, an 8x phase-locked loop (PLL) for generating a stable clock signal, and a 10-bit digital-to-analog converter (DAC) that enables communication with various analog devices.



   <div align="center">
      <img src="Week2/VSDBabySOC/VSDbabySoc.png" alt="VSDBabySOC" width="700"/>
   </div>
   


### BabySoC components

   - **RVMYTH (RISC-V CPU)**: RVMYTH is the brain of BabySoC, based on the open-source RISC-V design. It's a simple, customizable CPU that handles processing tasks and communicates with other parts of the SoC. This flexibility makes RVMYTH ideal for learning and experimenting with CPU architecture.

   - **Phase-Locked Loop (PLL)**: 

      - A Phase-Locked Loop (PLL) is a control system that generates an output signal whose phase is synchronized with an input signal. Both signals will have the same frequency and can either have no phase difference or a constant phase difference.
     
     - PLL in VSDBabySoc :
      The PLL generates a stable clock signal to keep everything in BabySoC running in sync. It matches the SoC's clock with a reference frequency, ensuring reliable timing for RVMYTH and DAC. PLLs are widely used to keep signals aligned in communication and timing circuits.

     
   <div align="center">
      <img src="assets/PLL.png" alt="PLL" width="700"/>
   </div>
   
**Block Diagram**

A PLL typically consists of three main components:
   - **Phase Detector:** Compares the input signal (reference) with the output signal from the oscillator and generates an error signal based on the phase difference.
   - **Loop Filter:** Usually a low-pass filter that processes the error signal to produce a control voltage.
   - **Voltage-Controlled Oscillator (VCO):** Adjusts its frequency based on the control voltage to match the input frequency.

**Functionality:**
   - The PLL aims to lock the output frequency to the input frequency, maintaining a constant phase relationship between the two signals.
   - In some cases, a frequency divider may be used in the feedback loop to produce an output that is a multiple of the reference frequency.

**Why Can’t Off-Chip Clocks Always Be Used?**

   1. Clock Distribution Delays:
      - Using a single clock source for an entire chip can lead to delays due to long wiring distances, which can affect timing.
   2. Clock Jitter:
      - Off-chip clocks may experience variations in signal timing, known as jitter, which can disrupt synchronization.
   3. Different Frequency Requirements:
      - Various blocks within the same chip may require different clock frequencies. For example, one block might need 200 MHz while another needs 100 MHz.
   4. Crystal Frequency Deviations:
      - When quartz crystals are used as clock sources, they come with a frequency error measured in parts per million (ppm).
      - A higher ppm error means that the frequency can deviate more from the desired value, affecting timing precision.
   5. Frequency Stability:
      - The stability of a crystal’s frequency can vary with temperature. Crystals with higher ppm errors are more likely to exhibit larger frequency variations when temperature changes.
   6. Total Frequency Error:
      - The overall frequency error of a crystal includes contributions from:
         - Frequency Tolerance: The initial error in frequency.
         - Frequency Stability: Variation over temperature.
         - Aging: Changes in frequency over time.
      - Higher ppm errors in any of these factors can lead to larger total frequency errors, impacting the accuracy of timing references in electronic systems.
   
   
  - **Digital to Analog Converter**:

   - A Digital to Analog Converter (DAC) is an electronic device that converts a digital input signal (represented in binary code) into an analog output signal.
   1. Digital Signal Representation:
      - The digital input is composed of bits, specifically 0s and 1s, which represent the digital information.
   2. Structure:
      - A DAC typically has multiple binary inputs and a single analog output.
      - The number of binary inputs is usually a power of two (e.g., 2, 4, 8, 16).
   3. Types of DACs:
      - There are primarily two common types of DACs:
         - Weighted Resistor DAC: Uses resistors with different weights to convert the digital signal into an analog voltage.

         - R-2R Ladder DAC: Uses a repeating network of resistors to achieve the same effect, allowing for simpler design and easier scaling.
  

   4. In VSDBabySoC:
      - In the VSDBabySoC design, we are utilizing a 10-bit DAC, which means it can take a digital input represented by 10 bits and convert it into an analog output.
       
       
      - The DAC turns digital signals from RVMYTH into analog output, like sound or video. This allows BabySoC to connect with external devices that use analog signals, such as speakers or displays.
</details>


---

This document outlines the structure and components of BabySoC. By mastering these concepts and understanding how BabySoC operates, one gains a solid foundation in modern embedded systems design and digital-to-analog interfacing.
