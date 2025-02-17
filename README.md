# Experiment 1

## Objective
Conduct **DC analysis, Transient analysis, and AC analysis** of a **Common Source (CS) amplifier** circuit and extract key parameters using **LTSpice**.

## Required Components
- **MOSFET:** `nmos4`, `pmos4`
- **Resistor:** `22kΩ`
- **Voltage Supply:** `1.8V`, `0.9V`
- **Connecting Wires`

## Theoretical Background
**MOSFETs** play a crucial role in electronics due to their:
- Compact size  
- Low power consumption  
- Simple structure  
- Compatibility with **VLSI technology**

### MOSFET Configurations
MOSFETs can be connected in three configurations:
1. **Common Drain**
2. **Common Gate**
3. **Common Source** *(Most widely used)*

As an **amplifier**, the MOSFET operates in the **saturation region**, where:
- `Vgs > Vth`
- `Vgd < Vth`
- `Vds ≥ Vov` *(For N-channel MOSFET)*

In the **Common Source configuration**:
- A **180-degree phase shift** exists between input and output.
- The **input impedance is high** *(Ideally infinite, `Ig = 0`)*.

### Drain Current Expression
```
Id = (1/2) * kn * Vov^2
```
where:  
- **Vov = Vgs - Vth**
- **kn = μ_n * Cox * (W/L)**  

### Output Consideration
The **output is taken from the drain terminal** to maintain a **common ground reference**.


## Circuit - 1

### **Circuit Diagram**
![image](https://github.com/user-attachments/assets/0dc2fe6a-72bd-4bdf-8584-fae024369d56)

## Steps for Simulation

### **1. Design the Common Source Amplifier Circuit**  
- Label the **NMOS** as `CMOSN`.

### **2. DC Analysis**  
- Apply **DC voltage**:
  - `VDD = 1.8V`
  - `VGS = 0.9V`
- In **LTSpice**:
  1. Navigate to **Simulate → Edit Simulation Command**.
  2. Select **DC Analysis** and confirm.
  3. Click **Run** to obtain the **DC operating point (Vout)**.
- **Set the Length constant** and **adjust Width** to achieve `ID = 48.33μA`.

### **3. Transient Analysis**  
- Modify **VGS voltage source** to a **sine wave input**:
  - **DC level:** `0.9V`
  - **Amplitude:** `50mV`
  - **Frequency:** `1kHz`
- In **LTSpice**:
  1. Go to **Edit Simulation Command → Transient Analysis**.
  2. Set **Stop Time** to `5ms`, then confirm.

### **4. AC Analysis**  
- In **Edit Simulation Command**:
  1. Choose **AC Analysis**.
  2. Set **Type of Sweep** to **Decade**.
  3. Set **Points per Decade** to `10`.
  4. Define **Frequency Range** from `0.1Hz to 1THz`.
  5. Confirm and run the simulation.
- Extract **gain and frequency response**.

---

## **Calculations**

### **Power Calculation**
```
P = 100μW
```

### **Drain Equation**
```
VDD = VDS + ID * RD
P = I * V
```

- **Given:**  
  - `ID = 48.33μA`
  - `VDD = 1.8V`
- **Thus:**  
  ```
  VDS = Vout
  ```

### **Resistor and MOSFET Parameters**
- **Calculated RD:** `32.4kΩ` *(Used: `22kΩ`)*  
- **Length:** `180nm`  
- **Width:** `18μm` *(Determined while keeping Length constant)*  
- **VDS:** `0.735V`  

### **Q-Point**
```
Q = (0.735V, 48.33μA)
```

## **Results**

### **1. DC Analysis**

![image](https://github.com/user-attachments/assets/b1d4cfab-5994-4281-9c28-906d1a357782)

- **Drain Current:** `48.33 μA`
- **Vout:** `0.735V`
- **Width:** `18 μm` for `L = 180 nm`

### **2. Transient Analysis**

![image](https://github.com/user-attachments/assets/0fcb60b4-2b69-4822-8a1a-c940871c58b3)

- A **180-degree phase shift** occurs between input and output.

### **3. AC Analysis**

![image](https://github.com/user-attachments/assets/cdb0af04-12e1-40c9-9e7e-8a512d902f74)

- Gain and frequency response extracted successfully.

### **Observations**
1. Drain current varies with MOSFET width.
2. Adjusting MOSFET dimensions influences drain current.
3. A **180-degree phase shift** exists between input and output.
4. The **CS amplifier achieves a gain of 20 dB**, amplifying the output signal **20 times**.

## Circuit 2: CMOS Amplifier Simulation

### **Objective**  
Simulate **DC analysis, Transient analysis, and AC analysis** of a **CMOS amplifier** in LTSpice.

### **Circuit Diagram**  
![image](https://github.com/user-attachments/assets/add2aed4-a355-41ac-8a38-d584d3ad0616)

---

## **Findings**

- **DC Sweep Analysis:**

- ![image](https://github.com/user-attachments/assets/9ee697e8-7fc5-4518-aaa2-201fed10daad)

-
- **Vin = 0.8V** as the optimal bias point.
- 
- **DC Analysis:**
-
-![image](https://github.com/user-attachments/assets/7b1c334b-7169-4d2c-943a-28c7f82abb32)

-    **Vout = 1.67V** and **ID = 19.55μA**.
- **Transient Analysis:**
-
-![image](https://github.com/user-attachments/assets/b94ff0a7-e9f6-4488-a50f-ad5eff0872e7)

- **180-degree phase shift**.
- **AC Analysis:**
-
![image](https://github.com/user-attachments/assets/ca3bf1d5-8cfc-4070-9c42-9b540ba753ff)

-   **frequency response**.

## **Conclusion**

1. **MOSFET width directly affects drain current**.
2. **PMOS width has a minor impact**, while **NMOS width significantly alters** drain current.
3. **Larger MOSFET width increases gain**.
4. **A 180-degree phase shift** is observed between input and output signals.

   
