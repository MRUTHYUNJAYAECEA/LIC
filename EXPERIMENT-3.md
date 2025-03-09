### **Differential Amplifier**

A differential amplifier is a key circuit in analog electronics that amplifies the difference between two input signals while rejecting common-mode signals (noise). It is widely used in operational amplifiers (op-amps), instrumentation amplifiers, and analog circuits.
A basic MOSFET differential amplifier consists of:

Two matched MOSFETs (M1 and M2) forming a differential pair

A current source I<sub>SS</sub> as a tail current

Two drain resistors R<sub>D</sub>

When the inputs V<sub>in1</sub> and V<sub>in2</sub> are equal, the circuit is balanced, and the current splits equally.

When V<sub>in1</sub> increases while V<sub>in2</sub> decreases, M1 conducts more current, and M2 conducts less, creating a voltage difference at the outputs.

The circuit rejects common-mode signals (same voltage at both inputs) and only amplifies the differential component

### **Question:**

**V<sub>DD</sub>=2 V , p<=1 mW , V<sub>ICM</sub>=1 V, V<sub>ocm</sub>=1.1 V , V<sub>P</sub>=0.4 V**

### **Circuit 1** <br>

<img width="452" alt="Circuit-I" src="https://github.com/user-attachments/assets/34f319e8-8b00-47b3-bd04-3f0ad9fdd641" />

**Step 1:Dc analysis design Rd and Rss**

![WhatsApp Image 2025-03-09 at 15 43 32_4474c216](https://github.com/user-attachments/assets/7a0a5a62-1ced-4a08-b16c-006833ec4240)

From the calculation we have finded I<sub>SS</sub>value as 0.5 mA <br>
I<sub>D1</sub> and I<sub>D2</sub> as 0.25 mA <br>
R<sub>D</sub> as 3.6 kohm <br>
R<sub>SS</sub> as 0.8 kohm <br>
V<sub>GS</sub>=V<sub>G</sub> - V<sub>p</sub> = 1 V - 0.4 V = 0.6 v <br>
V<sub>OV</sub> = V<sub>GS</sub> - V<sub>th</sub> = 0.6 V - 0.366 V = 0.234 V <br>

### **DC Analysis**

To set the operating point go to Configure Analysis and select Dc operating Point <br>

<img width="513" alt="C-I DC" src="https://github.com/user-attachments/assets/c768a8b6-de48-4a30-8920-4de8de6b0085" />

to set correct operating point vary width and length values 
width = 19.363 um <br>
length = 180 nm <br>


### **Calculate Gain**

![WhatsApp Image 2025-03-09 at 15 55 36_e70d9735](https://github.com/user-attachments/assets/2fafeb79-9a88-47ba-80d3-f5e1d58c42d9)


### **Calculate maximum input and output Swing**


![WhatsApp Image 2025-03-09 at 15 55 36_4789b603](https://github.com/user-attachments/assets/233944a5-54e3-43de-a21a-ab9ea20f2cc0)


### **TRANSIENT ANALYSIS**
Go to configure Analysis and select transient analysis then <br>
stop time as 1m ,time to start saving data as 0 <br>

• Waveform Type: Sine Wave
• DC Offset: 1 V
• Amplitude: 25 mV
• Frequency: 1 kHz

put the same values for V2 but change the phase angle.

And in V2 phi(deg) as 180


<img width="955" alt="C-I transient" src="https://github.com/user-attachments/assets/a38d4a53-045a-4b8b-9090-828521c14cc9" />



### **AC Analysis**
• Type of sweep: Decade
• Number of points per decade: 10
• Start frequency: 0.1 Hz
• Stop frequency: 1 THz
AC Amplitude as 1 and AC Phase as 0 in V1 <br>
AC Amplitude as 1 and AC Phase as 180 in V2 <br>


<img width="950" alt="C-I ac" src="https://github.com/user-attachments/assets/7a08fb93-1f6f-413f-834a-c2c51bd67aee" />



### **Circuit 2** <br>

Replace the resistor with a current source=0.5 mA.


![C-II](https://github.com/user-attachments/assets/1d964318-e86f-4ab8-976c-8372ea4efb08)


### **DC Analysis**


<img width="513" alt="C-I DC" src="https://github.com/user-attachments/assets/011236a2-740f-41ee-8623-d103e92ab3c1" />



### **TRANSEINT ANALYSIS**

![C-II trans](https://github.com/user-attachments/assets/5c02d638-bb15-423a-a87c-47ec30fa9cbb)


### **AC ANALYSIS**


![C-II ac](https://github.com/user-attachments/assets/078c69d4-3264-4a59-82d5-680744cad17a)


### **Circuit 3** <br>

Replace current Source with N-Channel MOSFET .


![C-III](https://github.com/user-attachments/assets/2374e071-158a-4a97-8a4d-d6b7b107266b)



### **DC Analysis**

Set the operating point of M3 such that it is in saturation state.


![WhatsApp Image 2025-03-09 at 16 12 41_080c0dab](https://github.com/user-attachments/assets/7346fac1-95f3-40d7-9f85-63e21d0ef603)

### **TRANSIENT ANALYSIS**


![C-III trans](https://github.com/user-attachments/assets/a49721ff-846a-4219-b98f-5a455711ab96)


### **AC Analysis**


![C-III ac](https://github.com/user-attachments/assets/7e696927-3b36-495b-8f07-15616d7df9f7)



# **Result**
| **Parameter** | **Circuit 1** | **Circuit 2** | **Circuit 3** |
|--------------|--------------|--------------|--------------|
| **V(out)**  | 1.1 V  | 1.1 V  | 1.0999 V  |
| **V(vp) (Common Mode Voltage)** | 0.400001V | 0.400001V | 0.4V |
| **Id(M1)** | 0.000250001 A | 0.000250001 A | 0.000250028 A |
| **Id(M2)** | 0.000250001 A | 0.000250001 A | 0.000250028 A |
| **Id(M3) (Tail Current Source)** | Not present | 0.0005 A (set with ideal current source) | 0.000500056 A |
| **Total Tail Current** | 0.000500002 A | 0.0005 A | 0.000500056 A |


# **Inference**


- **Circuit 1:** Basic differential pair with a resistive current source. Good for simple analysis but lacks precise biasing control.
- **Circuit 2:** Uses an **ideal current source**, which improves biasing and stability.
- **Circuit 3:** Implements an **active current source using NMOS**, providing **best stability** and is more **practical** for real applications.
- **Circuit 3 is the preferred design** for real-world implementations.









