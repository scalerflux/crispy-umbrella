# Week4

Id vs Vds curve for diferent values of Vgs
---
<img width="1357" height="1164" alt="Screenshot 2025-10-15 at 3 44 00 PM" src="https://github.com/user-attachments/assets/e77210c3-81cb-4fe4-923b-25a08fd1e879" />

Here when i check for Vds = 1.2 n Vgs= 1.6(taking 0.2 step) the drift urrent is nearly 19uA. 

---
Zooming ou the cutoff region, it looks we're seeing a Id of nearly 2uA which is at when Vgs 0.6. That's interesting why not before 0.6? 


<img width="1920" height="1164" alt="Screenshot 2025-10-15 at 4 11 37 PM" src="https://github.com/user-attachments/assets/6c63592f-a70a-4798-a7cc-abf236affa12" />

It's essentially coz, for this NMOS transistor to be on we need the Vgs to be atleat equal to the threshold voltage Vt which is 0.55 in this case. In other words can be said as the absence of strong inversion which can be seen below

<img width="3364" height="1304" alt="image" src="https://github.com/user-attachments/assets/251efdb1-5497-4759-b801-997c535d1ef4" />

