

# Week 4: Transistor and Inverter Characterization

## Intro

This report details a series of SPICE experiments conducted to characterize the behavior of individual MOSFETs and a standard CMOS inverter. The purpose of these experiments is to build a foundational understanding of how transistor-level physics influences circuit-level performance metrics relevant to digital design and Static Timing Analysis (STA).

The experiments cover:

* **NMOS I-V Curve Analysis:** To understand the fundamental operating regions (cutoff, linear, saturation) of a transistor and observe effects like velocity saturation in short-channel devices. This is crucial for modeling how a transistor acts as a switch.
  
* **CMOS Inverter VTC Analysis:** To determine the inverter's switching threshold ($V_M$) and noise margins. The Voltage Transfer Characteristic (VTC) defines the static behavior and robustness of the logic gate.
  
* **Transient Analysis:** To measure the rise and fall propagation delays, which are fundamental parameters for calculating the speed of digital circuits in STA.
  
* **Variation Analysis:** To observe the impact of power supply and process variations on the inverter's static and dynamic characteristics, demonstrating why margins are critical for reliable circuit operation.

###  NMOS I-V Characteristics


Figure 1: Long-Channel $I_{d}$ vs. $V_{ds}$ 

<img width="1274" height="1071" alt="Screenshot 2025-10-15 at 3 44 00 PM" src="https://github.com/user-attachments/assets/099eff07-0d44-49bc-8a4c-474a581540f5" />

---
*Figure 2: Long-Channel Cutoff Region Detail*

<img width="1724" height="1109" alt="Screenshot 2025-10-15 at 4 11 37 PM" src="https://github.com/user-attachments/assets/a450c6a0-f52d-44e1-84e6-4f37a268e4ca" />

---
 Figure 3: Short-Channel $I_{d}$ vs. $V_{ds}$ 
 
<img width="1086" height="1122" alt="Screenshot 2025-10-16 at 11 48 03 AM" src="https://github.com/user-attachments/assets/b775ec41-a5ac-4ebf-85f1-3f47d55bcb9e" />

---
Figure 4: Short-Channel $I_{d}$ vs. $V_{gs}$

<img width="931" height="1122" alt="Screenshot 2025-10-16 at 12 21 11 PM" src="https://github.com/user-attachments/assets/044c07d9-d891-40fd-91e8-cc1f37dc369d" />

---

| Parameter | Extracted Value | Notes |
| :-- | :-- | :-- |
| Threshold Voltage ($V_{t}$) | ~0.55V | Extracted from the long-channel device cutoff behavior. |

#### Observations \& Analysis

* **What:** For the long-channel device, the $I_{d}$ vs. $V_{ds}$ curves show clear quadratic behavior in saturation. The transistor turns on noticeably after $V_{gs}$ exceeds the threshold voltage of ~0.55V, which is required to form a strong inversion layer.
  
* **Why:** This follows the classical square-law model for long-channel transistors. Below $V_t$, the device is in cutoff with only minimal subthreshold leakage current.
  
* **STA Connection:** The short-channel device exhibits velocity saturation, causing the drain current to become more linear with $V_{gs}$ at higher gate voltages and reducing the total current. This deviation from the ideal model is captured in modern timing libraries (like `.lib` files) to accurately model cell delay.

***

### CMOS Inverter VTC \& Transient Characteristics


 Inverter VTC with Switching Threshold ($V_{m}$) 

<img width="1036" height="1122" alt="Screenshot 2025-10-17 at 11 29 36 AM" src="https://github.com/user-attachments/assets/b5777ec8-8f97-46b4-94c0-b8b73c0319e5" />

---
* Transient Response for Rise Delay Measurement*

<img width="1157" height="1122" alt="Screenshot 2025-10-16 at 7 34 46 PM" src="https://github.com/user-attachments/assets/f9e8d84f-3518-4d33-83ea-b6aa5c3659f5" />

---
* Transient Response for Fall Delay Measurement*

<img width="941" height="1122" alt="Screenshot 2025-10-16 at 7 43 47 PM" src="https://github.com/user-attachments/assets/fbdb6345-8eee-476d-b785-d53434377b3f" />

---

 VTC Noise Margins ($V_{IL}, V_{IH}, V_{OL}, V_{OH}$) Annotated

<img width="1214" height="1055" alt="Screenshot 2025-10-17 at 4 25 07 PM" src="https://github.com/user-attachments/assets/1a73c7b2-06af-4bb9-b0f7-e23860cc1331" />

---

| Parameter | Extracted Value |
| :-- | :-- |
| Switching Threshold ($V_{m}$) | 0.87V |
| Rise Propagation Delay ($t_{p,LH}$) | 338ps |
| Fall Propagation Delay ($t_{p,HL}$) | 284ps |
| Noise Margin Low ($NM_{L}$) | 0.63V |
| Noise Margin High ($NM_{H}$) | 0.74V |

#### Observations \& Analysis

* **What:** The inverter has a sharp transition, indicating high gain. The switching threshold is at 0.87V, and the noise margins are robust. The fall time is slightly faster than the rise time.
  
* **Why:** The switching point occurs where the NMOS and PMOS currents are equal. The propagation delay is determined by how quickly the pull-up (PMOS) or pull-down (NMOS) network can charge/discharge the output load capacitance. A stronger NMOS relative to the PMOS would result in a faster fall time.
  
* **STA Connection:** The rise and fall delays ($t_{p,LH}, t_{p,HL}$) are fundamental building blocks of timing analysis. These values, along with load- and slew-dependent derating factors, are used in STA tools to calculate path delays. Noise margins determine the circuit's tolerance to signal integrity issues like crosstalk and voltage droop, which can impact setup/hold timing.

***

###  Variation Analysis



* VTC Under Power Supply (VDD) Variation*
<img width="1300" height="1166" alt="Screenshot 2025-10-17 at 7 09 06 PM" src="https://github.com/user-attachments/assets/d58260ba-e424-4f23-8fce-bd87131eefd9" />

---
* Transient Failure at Low VDD (0.8V)*
<img width="1151" height="781" alt="Screenshot 2025-10-17 at 7 33 39 PM" src="https://github.com/user-attachments/assets/a999926e-884c-4a7e-a10e-372676318f26" />

---
* VTC Under device Variation*
<img width="1220" height="1162" alt="Screenshot 2025-10-18 at 10 26 41 AM" src="https://github.com/user-attachments/assets/2641d34b-ae58-42e5-93c7-034316b14caa" />

---

| Variation Type | Effect |
| :-- | :-- |
| Power Supply (VDD = 0.8V) | Failed to achieve full output swing; severe performance degradation. |
| Process Corners | ~42mV shift in switching threshold ($V_{M}$). |

#### Observations \& Analysis

* **What:** Lowering the power supply drastically hurts performance, preventing the output from reaching the supply rails within the given time. Process variations (from "fast" to "slow" transistors) shift the VTC, but the overall impact on the switching threshold is minimal (~42mV).
  
* **Why:** Transistor drive strength is heavily dependent on the supply voltage ($I_d \propto V_{DD}$). At low VDD, the current is too weak to charge the load capacitor quickly, causing large delays and incomplete swings. The inherent symmetry of CMOS design provides excellent robustness against process variations, as both NMOS and PMOS devices tend to shift together, keeping their ratio and thus the switching point relatively stable.
  
* **STA Connection:** This is why STA is performed across multiple Process, Voltage, and Temperature (PVT) corners. The "slow" corner (slow devices, low voltage, high temp) determines the worst-case setup time, while the "fast" corner (fast devices, high voltage, low temp) determines the worst-case hold time. These analyses ensure the chip functions reliably despite manufacturing and environmental variations.


## Conclusions

These experiments demonstrate the direct link between transistor-level physics and high-level digital circuit performance. Key takeaways include:

* **Transistor Behavior Constrains Timing:** The current-driving capability of transistors, influenced by effects like velocity saturation and supply voltage, directly sets the propagation delay of logic gates. These delays accumulate along critical paths and determine the maximum operating frequency of a circuit.
  
* **Variation Mandates Margins:** The observed shifts in VTC and delay due to process and voltage variations highlight why STA must be performed across multiple corners. The noise margins and timing slack calculated by STA tools must be sufficient to absorb these variations and ensure reliable operation in a real-world silicon environment. The robustness of the CMOS inverter design against these variations is a primary reason for its widespread use.













