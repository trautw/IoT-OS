
# IoT-OS

Operating system for ESP8266 IoT Devices

## Preface

IoT has a long history. The name is new but the idea to connect embedded system is not. (See e.g.: electronic modules in cars, ) What's new today is the number of connected devices. The number of devices increases because the price per device dropped sharply. There is a strong connection between the price and the number of connected devices. To maximise the number of devices the single device has to be as cheap as possible. Even a small price drop makes a big difference. This is an experiment to produce a platform for very cheap IoT device.

## Design goals

### Cheap Hardware

- Low memory foorprint
- Low CPU usage
- Standard Hardware

### Modular Software Design

- No design from scratch
- Easy software update

## Idea

- Use ESP8266 as hardware platform
ESP8266 is much cheaper than Pi
- Design an operating system for IoT
Porting operating systems from larger devices is not a good idea. Think of BS2000 on PCs, Windows on a phone or Android on your watch. We need an operating system for IoT

## Concept

The memory footprint should be very low. Communication is possible. So why not transfering all the code that has to be executed at every communication event?

## Communication flow

1. Initialization
2. Connect with internet
3. Subscribe to device specific MQTT channel
4. Loop: 
5. Execute code received by MQTT
6. Send result via MQTT

## Example messages

From MQTT channel

    { 
      "action": [       
        "local pin = gpioid[5]",
        "gpio.mode(pin,gpio.OUTPUT)",
        "gpio.write(pin, gpio.HIGH)",
        "return 'ON'" ]
    }

To MQTT channel

    { 
      "result": "ON"
    }


