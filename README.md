# Aircon Automation
#### Blueprint for Homeassistant.

This Blueprint sets target temperature depending on second temperature sensor and changes HVAC mode between HEAT, COOL, and DRY adjusting the fan speed from medium to auto.
#
### Requirements
 - External temperature sensor
 - External humidity sensor
 - You will need to create a toggle helper for an override switch
 
 *** Please note that your air conditioner needs dry mode
 *** Currently it is only in degrees celcius but am intending to and a selection for fahrenheit
 #
 ### What it does
 
 The script will trigger every 10 mins and then test if
  * The override switch is ON
  * If the HVAC's current mode is not OFF
  * If the calculated temperature difference between the target setpoit and the actual temperature in the room.
  
  Then it chooses between the actual temp and the target temp + or - 0.3 degrees and changes the mode to either HEAT, COOL, or DRY. 
  
  For DRY mode it will have a +2 degrees variant as if it is at the setpoint it tends to cool down too quick. If the mode is DRY it sets the fan speed to Medium else the fan is set to Auto and the temperature is calculated and set as required to maintain a constant temp.
  
  eg. if the target setpoint is 24 then the script will bypass any setting of mode, fan and temp if the sensor temperature is between 23.7 and 24.3
  
  
#
  * If anyone has any sugestions to improve the script I'll gladly look at them.
  
#### Disclaimer
This is the first time I have used Github so I would welcome help to set it up properly.
