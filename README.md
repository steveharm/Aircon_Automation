# Aircon Automation
#### Blueprint for Homeassistant.
[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fsteveharm%2FAircon_Automation%2Fblob%2Fmain%2Faircon_automation.yaml)

This Blueprint sets target temperature depending on second temperature sensor and changes HVAC mode between HEAT, COOL, and DRY adjusting the fan speed from medium to auto.

![Aircon Automation](https://github.com/steveharm/Aircon_Automation/blob/main/airconautomationblueprint.png?raw=true)

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
### Logs
As it sucks to not see what’s going on, this blueprint will log:

* info message that it has set an offset.
* debug message with all the values
You can set the debuglevel in your configuration.yaml like so:
```
logger:
  default: info
  logs:
    blueprints.steveharm.aircon_automation: debug
```  

#
  * If anyone has any sugestions to improve the script I'll gladly look at them.
  
#### Disclaimer
This is the first time I have used Github so I would welcome help to set it up properly.
