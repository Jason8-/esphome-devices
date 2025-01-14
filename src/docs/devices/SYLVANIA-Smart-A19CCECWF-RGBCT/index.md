---
title: SYLVANIA Smart+ A19CCECWF RGBCT Light
date-published: 2025-01-14
type: light
standard: us
board: bk27xx
---

Product ID: A19CCECWF

Firmware v1.0.9 can be exploited via tuya-cloudcutter
Firmware v1.1.4 appears to have AP mode disabled, tuya-cloudcutter does not work, tuya-convert fails to exploit

## Product Images

![SYLVANIA SmartPlus A19CCECWF RGBCT Light](SYLVANIA-Smart-A19CCECWF-RGBCT.jpg "SYLVANIA Smart+ A19CCECWF RGBCT Light")

## GPIO Pinout

| Function   | GPIO-Pin |
| ---------- | -------- |
| PWM_red    | P7       |
| PWM_green  | P8       |
| PWM_blue   | P9       |
| PWM_white  | P24      |

## Basic Configuration

```yaml
esphome:
  name: SYLVANIA-Smart-A19CCECWF-RGBCT
  comment: SYLVANIA Smart+ A19CCECWF RGBCT Light
  friendly_name: SYLVANIA Smart+ A19CCECWF RGBCT Light

bk72xx:
  board: generic-bk7231t-qfn32-tuya

# Make sure logging is not using the serial port
logger:
  baud_rate: 0
  
# Enable Home Assistant API
api:

ota:
  - platform: esphome

# WiFi connection
wifi:
  ap:

captive_portal:

# Enable Web server
web_server:

output:
  - platform: libretiny_pwm
    id: output_green
    pin: P8
  - platform: libretiny_pwm
    id: output_blue
    pin: P9
  - platform: libretiny_pwm
    id: output_red
    pin: P7
  - platform: libretiny_pwm
    id: output_white
    pin: P24

light:
  - platform: rgbw
    id: light_rgbw
    name: None
    color_interlock: true
    red: output_red
    green: output_green
    blue: output_blue
    white: output_white
    effects:
      - random:
          name: "Random"
      - flicker:
          name: "Flicker"
```