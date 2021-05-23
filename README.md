# MySharebotNg

This is my 2nd approach to Git and project sharing.

This confiuguration work for me!

Based on first Sharebot NG firmware https://github.com/Sharebot3D/Marlin

The original PSU was dead, I've changed it with a FTX PSU (from a dead 1U server ) I've implemented the PSU_CONTROL

I've added a filament runout sensor.

I'm trying to add a bltouch sensor. (may the sensor will be with me....) 

Config NG Sharebot 1 estruder.
erial Speed rised from 115200 to 250k (Octoprint) - 500k (Pc connection)
Some hw changed made (FTX PSU -NB - endstop X and Y reverted to original (Sharebot standard) Photo Giaupau gioloky MauroB 

Some news on https://www.stampa3d-forum.it/forum/forum/124-sharebot/


00-01
+ S_CURVE_ACCELERATION          
+ PSU_CONTROL                    // Printer shutdown +12V after print (ATX-FTX PSU needed!)
+ HOST_KEEPALIVE_FEATURE         // Disable this if your host doesn't like keepalive messages
+ BUSY_WHILE_HEATING             // Some hosts require "busy" messages even during heating

03
+ NOZZLE_PARK_FEATURE  
+ NO_MOTION_BEFORE_HOMING
+ UNKNOWN_Z_NO_RAISE       

04
+ MESH_BED_LEVELING
+ G26_MESH_VALIDATION
+ LEVEL_BED_CORNERS

 04-02
+ FILAMENT_RUNOUT_SENSOR        
+ FIL_RUNOUT_PIN    32  
+ FIL_RUNOUT_INVERTING true (instead false) 
+ POWER_TIMEOUT from 30 to 300

Config ADV
00-01
+ ADAPTIVE_FAN_SLOWING              // Slow part cooling fan if temperature drops 
+ WATCH_TEMP_PERIOD 80              // (To be reduced!)
+ WATCH_TEMP_INCREASE 4             // (To be reduced!)
+ FAN_MAX_PWM
+ FAN_MIN_PWM
+ E0_AUTO_FAN_PIN 8                //I use FAN pin 8 to cool down the ESTRUDER MOTOR!!

03
+ HOST_ACTION_COMMANDS              
+ HOST_PROMPT_SUPPORT               
+ ADVANCED_PAUSE_FEATURE  
+ HOME_BEFORE_FILAMENT_CHANGE           // Ensure homing has been completed prior to parking for filament change

Stepper Drivers changed:
#define X_DRIVER_TYPE  DRV8825  // Lan Step mode switch 001  was A4988 switch 111
#define Y_DRIVER_TYPE  DRV8825  // Lan Step mode switch 001  was A4988 switch 111 
#define Z_DRIVER_TYPE  DRV8825  // Lan Step mode switch 001  was A4988 switch 111 

[...]

#define E0_DRIVER_TYPE A4988

Removed since now 
1) Original sharebot leveling - there is a BLTouch and manual configuration from Marlin.
2) Original Sharebot filament change - done by Marlin software.

