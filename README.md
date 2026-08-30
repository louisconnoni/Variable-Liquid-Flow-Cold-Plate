# Variable-Liquid-Flow-Cold-Plate

# Variable Liquid Flow cold Plate

**Personal Project**
<br>


<!-- Final image of testing -->
<img src="assets/CombatRobotCompImage.png" width="55%" />

## Overview

The scope of the project was not only to be introduced to fluid dynamics and transfer calculations, but to validate simulation data using Ansys Fluent. 

The first step was selecting several cold plate designs based on upon industry accepted designs. Hand calculations were then selected to determine the optimal geometry for a 100 Watt heat source which cannot exceed 40 Celsius. The four cold plates were evaluated in Ansys to map their performance including temperature, pressure loss and velocity. Different flow rates, # of fins and mesh quality were also evaluated.

The second aspect of the project was to design a PID loop to control the flow rate of the cold plates. A thermistor would serve as the input to maintain a constant temperature by adjusting the pump speed using pulse width modulation. The goal was to match pump energy with the power output of the heat source. 

## Bill of Materials
| Component | Function | Part | Photo |
|---|---|---|---|
| Pump | Sized to provide sufficient flow to pull heat away  | Kamoer 400ml/min | <img src="assets/WheelMotor.jpg" width="80" /> |
| Nozzle | Powers wheel drivetrain | sized to match outer diameter of pump  | <img src="assets/DriveMotor.webp" width="80" /> |
| Thermistor | changes resistance value based upon temperature | Vortex 80A ESC (Beetle Weapon / Big Bot Drive) | <img src="assets/WeaponsESC.webp" width="80" /> |
| Diode | Used to prevent energy build up from inductive load | 2" Alloy Steel Round Bar, 4140 Annealed, Cold Finish | <img src="assets/ESC.webp" width="80" /> |
| Arduino Nano | Used to run PID loop | 1/2" Alloy Steel Round Bar, 4140 Annealed, Cold Finish | <img src="assets/DeadShaft.jpg" width="80" /> |
| 20 AWG Wire | Used to safely transmit power to pump | Carbon Fiber Plate | <img src="assets/CarbonFiberPlate.jpg" width="80" /> |
| MOSFET | Used to control pump power | TRITAN Radial Ball Bearing 6000, Dbl Sealed, 10 mm Bore, 26 mm OD, 8 mm Wd | <img src="assets/BearingCombat.jpg" width="80" /> |


## Initial Calculations and Sizing
The initial sizing of the cold plates was calculated using equations provided by Advanced Thermal Solutions. Initial conditions were based upon common sizing and required conditions for electronic management. Many values such as density, thermal conductivity and specific heat were based upon the average fluid temperature as the water travels through the system. Ultimately using the maximum surface temperature, pump power and ease of manufacturing. channel width for the pin-fin was calculated to be 1.9 mm for the pin fin and straight fin and 6.0 mm for the serpentine plate. A fourth cold plate was designed using gyroids, a geometric shape with a high surface area while allowing fluid flow. The gyroid design was designed in MATLAB then converted to an STL file.


### Calculations
<img src="assets/Screenshot 2026-08-12 220451.png" width="56%" />

*Initial calculations used by Advanced Thermal Solutions*

### Plots
<img src="assets/Screenshot 2026-08-12 220451.png" width="56%" />

*Plots of straight and pin fin Cold Plate*

<img src="assets/Screenshot 2026-08-12 220451.png" width="56%" />

*Plots of serpentine cold plate*

<img src="assets/Screenshot 2026-08-12 220451.png" width="56%" />

*Gyroid Structure generated in MATLAB*

## Ansys Simulation

Afterwards the 4 cold plates were designed in Solidworks following the design specifications. The first simulations used initial conditions of .4 L/min, 100 watts and an aluminum construction with water as the working fluid. Further tests were done by evaluating how a different # of fins or fluid velocity affected the heat flux. Lastly a Mesh independence survey was done to verify the simulation was best representing the results.

### Simulation Results
<img src="assets/Screenshot 2026-08-12 220451.png" width="56%" />

*Initial Serpentine Results*

<img src="assets/Screenshot 2026-08-12 220451.png" width="56%" />

*Flow speed and changing fluid temperature*

<img src="assets/Screenshot 2026-08-12 220451.png" width="56%" />

*Mesh Independance Study Plot*

### Control Wiring

The control wiring for the project included 3 thermistors to measure the incoming water temperature, the plate temperature, and the outlet temperature. The plate temperature was used as the primary input to the PID loop. 

A second circuit was used for the PWM circuit. a 2.2k pulldown was used to protect the Arduino from high current flow. A flyback diode was used to prevent energy storage from induction. A power supply was connected to the drain and source ends of a MOSFET while the Arduino was connected to the switch end.


<!-- Circuit Board with Callouts -->
<img src="assets/CADCombatRobot.png" width="56%" />
<!-- Temperature Sensing code -->
<!-- <img src="assets/freedom-weapon-cad.png" width="49%" /> -->
<!-- PID Code -->
<!-- <img src="assets/freedom-weapon-cad.png" width="49%" /> -->

*Temperature sensing circuit and PID loop*

## Fabrication

<!-- PLA PROTOTYPE -->
<img src="assets/FREEDOMPLACROPPED.jpeg" width="56%" />

*prototypes were created in PLA to be used for flow testing evaluating working pressure drop and flow.*

## Future Work

- **Reprinting the cold plates**: The 3D printer used for manufacturing lost power to heated bed causing small deformities in the print making them incapable of holding a seal. Future 3D prints should not encounter the same issue allowing for further testing to validate CFD results. 
- **Further mesh refinement** Mesh Geometry was limited to Ansys student mesh sizes. Further mesh sizing could be done by adaptive mesh sizing or body of influence.  

## Lessons Learned

- **Be mindful of ease of manufacturability** Working on the project made me consider how the cold plate could be machined. The channels were sized in way to avoid breaking tools. Additionally the parts were designed to be manufactured using only a 3 axis CNC. 
- **create flow tight design** The design lacked some necessary mounting screws to ensure a sealed environment. Further mounting screws would ensure a better seal.
