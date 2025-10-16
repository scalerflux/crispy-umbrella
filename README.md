# Week4

Id vs Vds curve for diferent values of Vgs
---
<img width="1274" height="1071" alt="Screenshot 2025-10-15 at 3 44 00 PM" src="https://github.com/user-attachments/assets/099eff07-0d44-49bc-8a4c-474a581540f5" />


Here when i check for Vds = 1.2 n Vgs= 1.6(taking 0.2 step) the drift urrent is nearly 19uA. 

---
Zooming ou the cutoff region, it looks we're seeing a Id of nearly 2uA which is at when Vgs 0.6. That's interesting why not before 0.6? 
* more on linear
* saturation 
* cutoff region is when Vgs<Vt

<img width="1724" height="1109" alt="Screenshot 2025-10-15 at 4 11 37 PM" src="https://github.com/user-attachments/assets/a450c6a0-f52d-44e1-84e6-4f37a268e4ca" />




It's essentially coz, for this NMOS transistor to be on we need the Vgs to be atleat equal to the threshold voltage Vt which is 0.55 in this case. In other words can be said as the absence of strong inversion which can be seen below

<img width="3364" height="1304" alt="image" src="https://github.com/user-attachments/assets/251efdb1-5497-4759-b801-997c535d1ef4" />

---

We looked at the long channel transistor, Now let's take the short channel transistor
* Intresting! so for lower values of Vgs it shoes Quadraic behaviour conversely for higher values it's a linear behaviour 
* So esentially from Vgs = 1v it's showing the linear behaiour
* Also the peak current reducs as well due to the velocity saturation
* for the same W/L ratio(1.5) w'ere are getting different currents

<img width="1086" height="1122" alt="Screenshot 2025-10-16 at 11 48 03 AM" src="https://github.com/user-attachments/assets/b775ec41-a5ac-4ebf-85f1-3f47d55bcb9e" />

So in summary we can put it like this

<img width="2370" height="956" alt="image" src="https://github.com/user-attachments/assets/6b9d9dc4-8593-4b30-a5dd-c4e132b0cca8" />


***

Cool that was great i reckon let's now Id vs Vgs graph for this short channel transistor, for this we're keeping Vds constant. There we this one shows linear behaviour as well and the slope of this curve will give the threshold voltage

<img width="931" height="1122" alt="Screenshot 2025-10-16 at 12 21 11 PM" src="https://github.com/user-attachments/assets/044c07d9-d891-40fd-91e8-cc1f37dc369d" />

# Voltage transfer characteristicks
Claculating the output voltage Vout while sweeping the vaues of inpt volatage Vin
the switching threshold is coming around 0.87 fro W/L =?
<img width="1104" height="1122" alt="Screenshot 2025-10-16 at 7 22 19 PM" src="https://github.com/user-attachments/assets/f0fc6d31-b3d2-4e4a-b020-3d2987182389" />

# Trnsfer charateristicks 

## Rise delay

at point 0.9 which is half of the Vdd(2.0) we calculate Vout-Vin = 2.48- 2.14 = 0.34 

<img width="1157" height="1122" alt="Screenshot 2025-10-16 at 7 34 46 PM" src="https://github.com/user-attachments/assets/f9e8d84f-3518-4d33-83ea-b6aa5c3659f5" />

## Falling delay 

which is 4.33-4.05 = 0.28
<img width="941" height="1122" alt="Screenshot 2025-10-16 at 7 43 47 PM" src="https://github.com/user-attachments/assets/fbdb6345-8eee-476d-b785-d53434377b3f" />







