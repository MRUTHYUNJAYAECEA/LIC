# 555 Timer Monostable Multivibrator
### 1. AIM
Generate a waveform with pulse width of 0.5 ms under different trigger conditions using 555 timer IC.


### 2. THEORY
The NE555 timer is a versatile IC used in a variety of timing applications. It can be operate in three primary modes:       
- **Astable Mode**: No stable state; the timer continuously switches between HIGH and LOW, producing a square wave.
- **Monostable Mode**: One stable state (LOW); the timer produces a single output pulse in response to an external trigger.
- **Bistable Mode**: Two stable states, toggled by external signals.
In the monostable mode, when a **falling edge** is applied to the **Trig** pin, the output goes HIGH for a period defined by external resistor (R) and capacitor (C), then automatically returns to LOW.


### 3. CIRCUIT DESIGN AND CALCULATION

![image](https://github.com/user-attachments/assets/fe1f90b1-081c-4ba6-ae4c-3e3fc921cdec)

#### Target pulse width:

*T = 0.5 ms*

Using the monostable formula:

*T = 1.1 x R x C*

Assuming:
- C = 1 µF

Then:

*R = T/1.1 x C = 454.54 Ω*

Selected values:
- R = 454.54 Ω
- C = 1 µF

### 4. SIMULATION ANALYSIS
### <ins>Transient Analysis
Used to verify timing behaviour of the output signal in response to various trigger signals

### <ins>Procedure 
1. Open LTspice and create a new schematic.Set up the circuit as per the circuit diagram.
2. Select the Resistor (R) and Capacitor(C) as per the given specifcation.
3. Simulation Command
   - Go to **Simulate** -> *Edit Simulation Cmd*
   - Choose **Transient**, and set thime as needed per case.


 ### <ins>Case 1: Properly Spaced Triggers
- Trigger Pulse Source:
  VTrig PULSE(5 0 0.05m 0 0 0.01m 2m)
  - This generates a falling edge every 2 ms (well spaced).

- Run the simulation for 10 ms.
- **Expected Output**:
  - Each falling edge triggers the 555.
  - Output (VOUT) goes HIGH for approx. 0.5 ms on each trigger.
  - Multiple output pulses will be seen.

    ![image](https://github.com/user-attachments/assets/aa0898bb-c1df-4b4f-8704-0ff9bd493922)

### <ins>Case 2: Rapid Repeated Triggers
- Trigger Pulse Source:
  VTrig PULSE(5 0 0.05m 0 0 0.01m 0.2m)
  - This generates a falling edge every 0.2 ms (faster than output duration).

- Run the simulation for 2 ms.
- **Expected Output**:
  - First falling edge triggers the 555.
  - Output (VOUT) goes HIGH for 0.5 ms.
  - All triggers during this HIGH time are ignored.

![image](https://github.com/user-attachments/assets/655dfb41-dfd8-4a42-9358-80fecba61d1f)

### <ins>Case 3: Monostable Multivibrator(Virtual Lab)

![Screenshot 2025-05-21 220423](https://github.com/user-attachments/assets/a4eb0e00-9dff-442b-862d-c2406f4e2ff4)

  ### <ins>Output Waveforms

  ![image](https://github.com/user-attachments/assets/6d6ccfc7-9d76-4d5a-a3e3-14b32460d009)


### 5. INFERENCE
- The 555 timer in monostable mode correctly generates a 0.5ms output pulse when triggered.
- It does not respond to retriggering until the current pulse is complete, confirming non-retriggerable behaviour.
- Using an astable source and edge-filtering logic provides reliable triggering.

### 6. CONCLUSION
The NE555 timer configured in monostable mode provides accurate, predictable timing pulses when triggered by clean falling edges. In this simulation, a 0.5 ms output pulse was reliably generated using selected resistor-capacitor values, and its response under different trigger scenarios was analysed. The circuit performs well in digital timimg applications and can be extended using external logic for automated triggering.
