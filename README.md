# Week4

Id vs Vds curve for diferent values of Vgs
---
<img width="1274" height="1071" alt="Screenshot 2025-10-15 at 3 44 00 PM" src="https://github.com/user-attachments/assets/099eff07-0d44-49bc-8a4c-474a581540f5" />


Here when i check for Vds = 1.2 n Vgs= 1.6(taking 0.2 step) the drift urrent is nearly 19uA. 

---
Zooming ou the cutoff region, it looks we're seeing a Id of nearly 2uA which is at when Vgs 0.6. That's interesting why not before 0.6? 


<img width="1724" height="1109" alt="Screenshot 2025-10-15 at 4 11 37 PM" src="https://github.com/user-attachments/assets/2547d49e-023a-4e36-ad1f-bdecf6784749" />


It's essentially coz, for this NMOS transistor to be on we need the Vgs to be atleat equal to the threshold voltage Vt which is 0.55 in this case. In other words can be said as the absence of strong inversion which can be seen below

<img width="3364" height="1304" alt="image" src="https://github.com/user-attachments/assets/251efdb1-5497-4759-b801-997c535d1ef4" />

