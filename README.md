# Nonlinear-Sliding-Mode-Control (SMC)
Linear control architectures like: PID cannot successfully secure setling time, and reference tracking for a nonlinear system. Though if the nonlinearity is very weak, then linear control scheme might still work. 
---
In this repository a comparison between PID and SMC is studied in SIMULINK MATLAB. 
It is proved that PID cannot result in decent reference tracking and there is always an offset. While, SMC with smaller control gain (smaller control effort) can secure NO MAXIMUM PEAK OVERSHOOT and PERFECT TRACKING (NO OFFSET). 
In general, SMC is a type of Robust control that can take care of slight variations in the model which is normal due to unmodeled dynamics, internal/external disturbance (though if the variations are significant, then Adaptive control which entirely updates its parameters is a decent choice). 
In SMC, there are basically 2 control schemes: Reaching law and staying law. Reaching law ensures that system states are driven towards the switching/sliding surface. Staying law ensures that states are staying on the sliding surface. SMC is ideal for NONLINEAR systems as it sort of linearizes:
S (switching surface) = e_dot + lambda*e; e is error and lambda is determining the slope of the sliding surface. Increasing lambda makes the system states to converge towards the S faster, though it can easily lead to maximum peak overshoot!!! 
u_SMC = eta*sat_S - e_dot; sat_S is the saturated sliding surface which is determined via saturation or sigmoids or any other type of hyperbolic tangentials. Essentially, SMC wants to ensure that as long as the states are outside the Boundary Layer, it is okay to inject largevalues
of the eta (control gain) to overcome uncertainties. This is where robustness comes into play. Though if eta is very strong, then states will jitter back and forth around the sliding surface; this is called: Chattering, which is the cost of SMC and robust control techniques.
To address such chattering which is usually low-amplitude oscillations/vibrations at high frequencies; boundary layer is considered where outside the boundary layer injecting large control signals via large values of the eta is OK but inside the BL, eta and control signal are decreased to prevent
Chattering (Jittering). 
![image](https://github.com/user-attachments/assets/9c49c524-a7fb-4ef4-b337-40f1bae793ce)

![image](https://github.com/user-attachments/assets/518d8242-daad-46ad-8680-897d2cfb1334)
above shows that PID could not pass! 
![image](https://github.com/user-attachments/assets/5f2fc032-53ac-4f96-973e-b88fc0d54d96)
Above shows that SM successfully passed. 
