# Scents of Connection 


<img width="340" alt="image" src="https://github.com/user-attachments/assets/05eb9e95-22e4-46cc-80e3-f44aa842a445">
<img width="270" alt="image" src="https://github.com/user-attachments/assets/93e50bf4-4f4c-4227-a463-79ce3e7627f7">

This research project explores the intersection of mindfulness, olfaction, and interpersonal neural synchronization (INS) using an adapted EEG headset and a custom-built diffuser device. This repository contains the code, designs, and data necessary to reproduce the study.


## Research Objectives 
- Develop a device capable of inducing and measuring meditative states through EEG and olfactory stimuli.
- Investigate the impact of shared sensory experiences on interpersonal neural synchronization (INS).
- Assess user satisfaction and emotional engagement with the device.

## Components required:

- 2 x Mind Flex
- 6 x AAA batteries for the headsets
- 2 x 12" lengths of solid core hookup wire (around #22 or #24 gauge is best).
- Heat gun + Heat shrink tubing
- Solder gun

- 1 x Raspberry Pi 3 (any variety with Bluetooth), with USB cable
- 1 x MicroSD Card 
- 2 x [ESP32](https://wiki.dfrobot.com/FireBeetle_Board_ESP32_E_SKU_DFR0654) boards
- [Flexible LED strip](https://shop.pimoroni.com/products/flexible-rgbw-led-strip-neopixel-ws2812-sk6812-compatible?variant=30260032733267)
- [Ultrasonic Mist Maker](https://www.amazon.co.uk/dp/B0CY2FSGDD?psc=1&ref=ppx_yo2ov_dt_b_product_details)
- [MOSFET](https://cdn.sparkfun.com/datasheets/Components/General/FQP30N06L.pdf)
- Piezoelectric Ultrasonic Disk
- 1K ohm Resistor 
- Power Supply (matching the voltage requirement of the piezoelectric disk)
- Breadboard and Wires
- Device (PC or Mac) to monitor the serial data and send to MQTT

## Software required:

Use the [Arduino Brain Library](https://github.com/kitschpatrol/Brain) to capture the raw data as a CSV. 

Optional: Processing Brain Visualizer (download here, it might help to have Processing as well)

## Headset Guide 
Follow this [Hardware Tutorial](https://frontiernerds.com/brain-hack) for modifying the headset - it's as simple as putting the batteries in, unscrewing a panel on the headset, and soldering two leads. 

<img width="400" alt="image" src="https://github.com/user-attachments/assets/b0a89b63-d8c0-4972-a707-ffe83aa565f5">

## Diffuser Guide
### Pinout Diagram  
<img width="800" alt="image" src="https://github.com/user-attachments/assets/09533962-a25a-4786-bbec-89ba633fe305">

Be sure to extend the wires on the Ultrasonic Atomizer, and solder a wire across the button to toggle on. 

The 1k ohm resistor is connected between the gate of the MOSFET and ground and acts as a pull-down resistor. It ensures that the MOSFET gate is pulled to a known low state (0V) when the digital pin is not actively driving it. 

### 3D Model 
<img width="800" alt="rhino mock-up" src="https://github.com/user-attachments/assets/76588905-08d9-483c-a3fc-3ec6f3cebd6f">

### Setting up the Raspberry Pi 
Follow [this](https://www.tomshardware.com/reviews/raspberry-pi-headless-setup-how-to,6028.html) tutorial to set up your Raspberry Pi. 

## Connecting the Headset
Update your information and test the MQTT connection using the Headset1.ino and Headset2.ino scripts in the Final Scripts folder. 

## Usage Instructions
### Setting Up the Device
1. Power Up the System: Ensure that all components are connected and powered on.
2. Connect to the MQTT Broker: Make sure the Raspberry Pi is connected to the same network as the ESP32 microcontrollers and can receive data via MQTT.
3. Initialize the Diffuser and LEDs: Run the test scripts on the Raspberry Pi. To test the LEDs before you have the headsets running, use the fake_mqtt_data.ino in the archived foler.

### Running Experiments
#### Individual Meditation Study

1. Start by having the participant wear the EEG headset and sit in front of the diffuser.
2. Run the script single_headset_csv.py on the Raspberry Pi and provide the participant number to begin data collection.
3. The LEDs will provide real-time feedback as the participant reaches different meditative states. Once a "Very High" state is achieved, the diffuser will release the scent.

#### Paired Meditation Study

1. Set up both participants with their respective EEG headsets.
2. Follow the same procedure as the individual study, but monitor both sets of data to achieve synchronized meditative states.

### Collecting Data
1. Raw Data Collection: All EEG data will be automatically saved in the folder where you ran the script with participant IDs and timestamp details.
2. Questionnaire Responses: After each session, participants should fill out the surveys. A pdf is included in the Data file - use these questions in any survey software of your choice.

## Acknowledgements

I would like to thank my dissertation supervisors, Leah Lovett and Andy Hudson-Smith, for their guidance and support. Special thanks to Stephen Grey, Duncan Wilson, Simon Gosling, and Aude Vuilliomenet for their assistance with prototyping, device assembly, and schematic reviews. Lastly, I extend my gratitude to my CASA peers who participated in the study.




