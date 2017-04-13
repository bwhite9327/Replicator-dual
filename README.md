# Manifest 
This repository is to provide the community with the appropiate settings to use a Replicator 3D machine with Slic3r.  
It will contain all the configuration needed regaring the printer settings, and the filament settings.  
This settings were obtained from the Makerbot Markerware software .json file.  
This is my personal setup for a Monoprice Dual machine working in San José, Costa Rica with the filament bought from www.CrCibernetica.com  

---

## Printer settings  
This section will list the general settings of the machine and also the Start G-Code and End G-Code  
### Replicator dual Settings  
Nozzle diameter: 0.4  

Platform size:
  * x: 225 
  * y: 145 
  * z: 150
  
Start_position:
  * x: -112 
  * y: -73 
  * z: 0
  
Printer size:
  * x: 449 
  * y: 291 
  * z: 150
  
Feedrate:
  * x: 12450 
  * y: 12450 
  * z: 1170 
  * A: 1600 
  * B: 1600
  
Steps per mm:
  * x: 94.139704 
  * y: 94.139704 
  * z: 400 
  * A: -96.275 
  * B: -96.275
  
### Material settings
#### PLA
Feed diameter: 1.77  
Max fill speed: 90  
Max flow rate: 4.0  
Restart rate: 25  
Retract distance: 1.3  
Retract rate: 25  
Temperature: 230  

#### ABS
Feed diameter: 1.77  
Max fill speed: 90  
Max flow rate: 4.0  
Restart rate: 25  
Retract distance: 1.3  
Retract rate: 25  
Temperature: 230  

#### HIPS
Feed diameter: 1.77  
Max fill speed: 90  
Max flow rate: 4.0  
Restart rate: 25  
Retract distance: 1.3  
Retract rate: 25  
Temperature: 250  

### G-Code 
#### Start G-Code - Right extruder ABS 
(replicator_begin)  
M136 (enable build progress)  
M73 P0  

(replicator_homing)  
G162 X Y F2000(home XY axes maximum)   
G161 Z F900(home Z axis minimum)  
G92 X0 Y0 Z-5 A0 B0 (set Z to -5)  
G1 Z0.0 F900(move Z to '0')  
G161 Z F100(home Z axis minimum)  
M132 X Y Z A B (Recall stored home offsets for XYZAB axis)  

(replicator_start_position)  
G92 X152 Y75 Z0 A0 B0  
G1 X-112 Y-73 Z150 F3300.0 (move to waiting position)  
G130 X20 Y20 A20 B20 (Lower stepper Vrefs while heating)  

(heat_platform)  
M109 S50 T0 M134 T0  

(heat_tools)  
M135 T1  
M104 S215 T1  
M133 T1  

(replicator_end_start_sequence)  
G130 X127 Y127 A127 B127 (Set Stepper motor Vref to defaults)  

#### End G-Code - Right extruder ABS 
(replicator_end_position)  
M18 A B(Turn off A and B Steppers)  
G1 Z155 F900 G162 X Y F2000 M18 X Y Z(Turn off steppers after a build)  

(cool_platform)  
M109 S0 T0  

(cool_tools)  
M104 S0 T0  
M104 S0 T1  

(replicator_end)  
M70 P5 (We <3 Making Things!)  
M72 P1 ( Play Ta-Da song )  
M73 P100 (end build progress)  
M137 (build end notification)  