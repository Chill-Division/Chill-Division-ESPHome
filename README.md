# Chill-Division-ESPHome

ESPHome YAML for the boards Chill Division makes, so you can get them going in Home Assistant with a copy and paste.

Each file is the part you add to the bottom of your device's YAML in ESPHome Device Builder. They're all set up for the M5Stack Unit PoE-P4, which is what we use for every sensor and controller. Plugging into something else? Change the pins to suit (see below).

Setting up Home Assistant for the first time? Start with the Home Assistant Setup Guide at [sops.chilldivision.co.nz](https://sops.chilldivision.co.nz/). It walks you through adding a PoE-P4 and an SHT45, step by step.

## Always check the pins

Every file has its pins near the top, with a comment saying which controller they're for. Before you install, check they match the controller you've plugged into:

| Grove wire | Unit PoE-P4 | PoESP32 | Atom Lite / Atom Echo |
| --- | --- | --- | --- |
| Yellow | GPIO53 | GPIO16 | GPIO26 |
| White | GPIO54 | GPIO17 | GPIO32 |
| Red | 5V | 5V | 5V |
| Black | GND | GND | GND |

On the I2C boards (the SHT45 and the 0-10V), yellow is `sda` and white is `scl`. For other M5Stack controllers, see the table in [M5Stack-ESPHome](https://github.com/Chill-Division/M5Stack-ESPHome).

The colours are for M5Stack's own Grove leads, which is what we supply. Seeed's leads swap the yellow and white wires, so go by position. Yellow here means the wire next to the red one.

## The boards

| File | Board | What shows up in Home Assistant |
| --- | --- | --- |
| [Chill Division SHT45 Environment Sensor.yaml](Chill%20Division%20SHT45%20Environment%20Sensor.yaml) | SHT45 temperature and humidity board | Temperature, Humidity, VPD |
| [Chill Division Solid State Relay.yaml](Chill%20Division%20Solid%20State%20Relay.yaml) | SSR-Lite, switches two 230 V loads | Load 1, Load 2 |
| [Chill Division Grove to PWM Adaptor.yaml](Chill%20Division%20Grove%20to%20PWM%20Adaptor.yaml) | Dims an LED light through its RJ11/RJ12 port | Light 1 |
| [Chill Division Grove to 0-10V Adaptor.yaml](Chill%20Division%20Grove%20to%200-10V%20Adaptor.yaml) | 0-10 V dimming for LED drivers and bars | Light 1 |
| [Chill Division XKC-Y26 Level Sensor Adaptor.yaml](Chill%20Division%20XKC-Y26%20Level%20Sensor%20Adaptor.yaml) | Two XKC-Y26-V tank level sensors | High level, Low level |
| [Chill Division Grove to Dallas 1-Wire Adaptor.yaml](Chill%20Division%20Grove%20to%20Dallas%201-Wire%20Adaptor.yaml) | DS18B20 temperature probe (read the warning in the file first) | Water temperature |

## Name things with a number

Number every device, even when there's only one of it so far. "GT1 Climate 1", not "GT1 Climate". When the second one turns up it slots straight in, and nothing needs renaming.

## Licence

Apache 2.0, see [LICENSE](LICENSE).
