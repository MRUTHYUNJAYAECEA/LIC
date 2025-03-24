# Design and Analysis of Current Mirror Circuit

### AIM:

**Design Question :**  
Design and analyze the current mirror circuit with the following specifications:
- **Voltage Gain (Av)** > -10 V/V
- **V<sub>DD</sub>** = 1.8 V
- **Power consumption (P)** ≤ 1 mW

Perform the DC analysis, transient analysis, and AC analysis while maintaining the same (W/L) ratio for different values of Length (L). Additionally, calculate the maximum output swing and bandwidth.

### 2. THEORY:

A **current mirror** is a circuit used to replicate a reference current across a different branch, maintaining a constant current regardless of load variations. It is widely used for biasing circuits and active loads in amplifiers.


- A reference current **I<sub>REF</sub>** is set through **M1**, setting its gate-source voltage **V<sub>GS</sub>**.
- The gates of **M1** and **M2** are connected, ensuring that both transistors share the same **V<sub>GS</sub>**.
- As both transistors are identical, **M2** will conduct a current equal to **I<sub>REF</sub>**.
- The output current remains constant, independent of load changes.

### 3. CIRCUIT DESIGN:

<img width="300" alt="image" src="https://github.com/user-attachments/assets/d704f45f-412a-4603-af62-702fedc6eeda" />


#### Step 1: Determine Total Current (I<sub>TOTAL</sub>)
- **I<sub>TOTAL</sub>** = P/V<sub>DD</sub> = 1 mW / 1.8 V = 0.555 mA

#### Step 2: Determine Reference Current (I<sub>REF</sub>)
- For a **1:1 ratio**:
  - **I<sub>REF</sub>** = I<sub>TOTAL</sub>/2 = 0.555 mA / 2 = 0.2775 mA
 
![image](https://github.com/user-attachments/assets/0649d851-dfb6-4162-84c4-1ffdc10c0633)
 
  
For a **1:2 ratio**:
  - **I<sub>REF</sub>** = I<sub>TOTAL</sub>/3 = 0.555 mA / 3 = 0.185 mA
  - **I<sub>D</sub>** = 2 * I<sub>REF</sub> = 0.37 mA

![image](https://github.com/user-attachments/assets/f6371f01-9c69-4de6-9c90-fde983918384)



#### 3.1 **1:1 Ratio Current Mirror:**
##### Circuit Parameters:

| **Parameter**  | **PMOS (M1)** | **PMOS (M2)** | **NMOS (M3)** |
|----------------|---------------|---------------|---------------|
| Length         | 180 nm        | 180 nm        | 180 nm        |
| Width          | 2.35 µm        | 2.35 µm        | 2.9 µm        |

#### DC Analysis Results:

![R1_1](https://github.com/user-attachments/assets/a50c858f-22f5-4d15-b670-1d9a564a0269)

Change i length of MOSFET we will observe change in V<sub>out</sub> and I<sub>D</sub>

| **Length (L)** | **Width (W1)** | **Width (W2)** | **Width (W3)** | **I<sub>REF</sub>** | **I<sub>D</sub>** | **V<sub>out</sub>** |
|----------------|----------------|----------------|----------------|--------------------|------------------|--------------------|
| 180 nm         | 2.35 µm         | 2.35 µm         | 2.9 µm         | 0.277 mA           | 0.27711 mA       | 0.552 V            |
| 500 nm         | 2.35 µm         | 2.35 µm         | 8.37 µm       | 0.277 mA           | 0.284 mA         | 0.289 V            |
| 1 µm           | 2.35 µm         | 2.35 µm         | 19.11 µm       | 0.277 mA           | 0.285 mA         | 0.213 V            |

##### Transient Analysis:

![image](https://github.com/user-attachments/assets/edeba8c8-251b-47ad-b4b9-4b16a21c471e)

- **Gain (Av)** = -300 mV / 25 mV = -12 V/V

##### AC Analysis:

![image](https://github.com/user-attachments/assets/7d2621a9-57d7-4648-863d-f748e7732f27)

- **Gain (Av)** = 21.6 dB
- **-3 dB Bandwidth Frequency** = 770.570 MHz

#### 3.2 **1:2 Ratio Current Mirror:**
##### Circuit Parameters:

| **Parameter**  | **PMOS (M1)** | **PMOS (M2)** | **NMOS (M3)** |
|----------------|---------------|---------------|---------------|
| Length         | 180 nm        | 180 nm        | 180 nm        |
| Width          | 2.5 µm        | 5 µm          | 3.897 µm      |

#### DC Analysis Results:

![image](https://github.com/user-attachments/assets/8fdc2223-f361-4b75-a34a-a2b1a26ec5a9)


| **Length (L)** | **Width (W1)** | **Width (W2)** | **Width (W3)** | **I<sub>REF</sub>** | **I<sub>D</sub>** | **V<sub>out</sub>** |
|----------------|----------------|----------------|----------------|--------------------|------------------|--------------------|
| 180 nm         | 2.5 µm         | 5 µm           | 3.897 µm       | 0.185 mA           | 0.370 mA         | 0.682 V            |
| 500 nm         | 2.5 µm         | 5 µm           | 10.825 µm      | 0.185 mA           | 0.380 mA         | 0.288 V            |
| 1 µm           | 2.5 µm         | 5 µm           | 21.65 µm       | 0.185 mA           | 0.382 mA         | 0.212 V            |

##### Transient Analysis:

![image](https://github.com/user-attachments/assets/1cf0bd13-b2df-4e3f-b8fc-6d3d11b21ccd)

- **Gain (Av)** = -280 mV / 25 mV = -11.2 V/V

##### AC Analysis:

![image](https://github.com/user-attachments/assets/9235b7dd-2f3e-48e2-8204-7926f8caaa73)

- **Gain (Av)** = 21 db  (20.984 dB) 
- **Bandwidth Frequency** = 815.968 MHz

### 4. DESIGN B: Differential Amplifier

Using the same design specifications:
- **V<sub>DD</sub>** = 3.3 V
- **P** ≤ 3 mW
- **V<sub>ICM</sub>** = 1.65 V
- **V<sub>ocm</sub>** = 1.7 V
- **V<sub>P</sub>** = 0.5 V

#### Circuit Parameters:

| **Parameter** | **PMOS (M3)** | **PMOS (M4)** | **NMOS (M1)** | **NMOS (M2)** | **NMOS (M5)** | **NMOS (M6)** |
|---------------|---------------|---------------|---------------|---------------|---------------|---------------|
| Length        | 180 nm        | 180 nm        | 180 nm        | 180 nm        | 1 µm          | 1 µm          |
| Width         | 2.214 µm      | 2.214 µm      | 1.82 µm       | 1.82 µm       | 200 µm        | 100 µm        |

#### DC Analysis Results:

![image](https://github.com/user-attachments/assets/c86ec858-5f5d-4636-87f8-10492e8f7805)



#### Transient Analysis Results:

![image](https://github.com/user-attachments/assets/57c7b767-d19f-4bb3-9cd9-43514a6cab93)

- **Gain (Av)** = -65 mV / 2 mV = - V/V

#### AC Analysis Results:

![image](https://github.com/user-attachments/assets/1cb91b94-ca65-4fa8-b988-378302523f9f)

- **Gain (Av)** = 8.299 dB

### 5. INFERENCE:

- **Length Increase**: When the length of the NMOSFET is increased, keeping the W/L ratio constant:
  - **V<sub>out</sub>** decreases.
  - **Drain current (I<sub>D</sub>)** increases slightly.
  - **Output resistance** increases due to reduced channel-length modulation.
  - Longer **L** improves **current matching** and **stability** in the current mirror.

#### Comparison of Features between 1:1 and 1:2 Ratio Current Mirror:

| **Feature**                  | **1:1 Ratio Current Mirror** | **1:2 Ratio Current Mirror** | **Inference** |
|------------------------------|-----------------------------|-----------------------------|--------------|
| **Current Accuracy**          | Higher accuracy            | Slight mismatch              | 1:1 provides better current matching |
| **Transistor Sizing**         | Smaller uses less area         | Larger uses more area            | 1:1 is more efficient in chip  |
| **Power Consumption**         | Lower, due to smaller devices | Higher, due to larger devices | 1:2 uses more power. |


- The **differential amplifier** performs better with a **current mirror** instead of a resistor load.
- Using **current mirrors** enhances the **gain and stability** of the amplifier and **reduces offset variations**.

---

This structured format allows for clarity and consistency while discussing the key steps in the design, analysis, and simulations for both current mirror configurations and their impacts on the differential amplifier.
