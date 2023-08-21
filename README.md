# # 
<img src="https://i.imgur.com/rTWAT7X.jpg">


# The_Wifydra
This is a fork from https://github.com/lozaning/The_Wifydra 

Multi-headed 802.11 panopticon

The Wifyrda is a wardriving tool for the simulanious monitoring all 2.4Ghz wifi channels for network beacons, and includes the ability to geotag the location of found networks and write all this data to an SD card for uploading to Wigle.net

![image](https://github.com/miami6/The_Wifydra-2023/blob/main/IMG_9117.JPG)

![image](https://github.com/miami6/The_Wifydra-2023/blob/main/IMG_9139.JPG)

https://github.com/miami6/The_Wifydra-2023/blob/main/IMG_9139.JPG

 

# Build Note 1
  
 | Build| Purpose |
| --- | --- | 
| Build Note 1 |  Two bodge cables are needed with the current revision of this PCB. |
|         |  The Second goes from one of the +3v out from the ESP32-S3 and into the VIN of either the SD Card or the GPS |
|         |  This is due to using +VCC for all the VIN net on the sub nodes and mistakenly using +5v for the VIN net on the ESP-32S3 and the peripherals connected to it.  |
|         |  It should have all been the same net|
|         |    
 

# Build Note 2
  
 | Build | Purpose |
| --- | --- | 
| Build Note 2| To ensure that home built feel for every wifydra, I made sure to not check the footprint of the seed xaio esp32-C3 that I used in this, |
|         | resulting in the board having a larger footprint for these modules than should have been used |
|         | The chips themselves have castilated edges, and both power and ground are on the same side, |
|         | so just scooch 'em over a bit and make sure you get those pins connected up to the board                                                     |
|         |                                                                  |
 
# What to flash with what
  
 | flash | Purpose |
| --- | --- | 
| Dom.ino |  file goes on the main esp32-s3 that has the tft screen |
|         |                                                         |
| Sub.ino | file goes on all of the sub seed xaio radios. Each of the sub nodes only scans a single channel for networks |
|         | YOU MUST MANUALLY CHANGE THE BOARD ID FOR EVERY SUB 14 channels |
|         |                                                                  |

If you dont change the Board ID all your radios will all just scan channel 1. There are 14 wifi channels, so iterate through those as you flash each sub

# Powering the Wifydra
The four holes above the Wifydra are labled ground and VCC are where the power is designed to be put into the board.
The board expects to get 5v from its power source. There are a variety of options available to accomplish this. I've got an 18650 battery pack that outputs over usb c, but also has 5v and 3.3v outlets. I connect the 5v and ground from that to the VCC and ground on the board and it works great. You could also solder a USB C decoy trigger set to out put 5 volts and use a standard power bank. I've also had luck with power the entire thing by plugging in the USB C powert of the Dom ESP32-S3 feather TFT, but im not sure this is advisable as Im unclear on how much power draw this puts on the TFT feather to power all the Subs.  


 
 # Required Libraries 
  
 | Library | Purpose |
| --- | --- | 
| WiFi | This library is used for connecting to Wi-Fi networks |
| esp_now | This library provides an API for simple and secure communication between ESP32 modules using the ESP-NOW protocol |
| Adafruit_GFX |  This library is used for controlling a TFT display (probably a ST7789-based display) to show information |
| Adafruit_ST7789 |  library for OLED display |
| SPI  | This library is used to communicate with devices using the Serial Peripheral Interface (SPI) protocol, which is commonly used to communicate with displays and other peripherals |
| HardwareSerial | This library is used to handle serial communication, likely for GPS module communication |
| TinyGPS++ | This library is used to parse and extract data from GPS modules|
| SD  | This library is used to interact with SD cards for data storage |
 

 
 # Required Components 
  
 | Component | Purpose |
| --- | --- | 
| Adafruit ESP32-S2 TFT Feather 	 	"4264"	 | Gather WiFi data & control hardware modules | Qty 1 |
| Adafruit 5v ready Micro-SD | Breakout board store data that we can analyze with WiGLE / Python | Qty 1 |
| Adafruit Ultimate GPS Breakout | 66 channel w/10 Hz updates - Version 3 | Qty 1 |
| Seeedstudio XIAO  esp32-c3 | individual channel radio| Qty 14 |
| Seeedstudio XIAO  esp32-s3 | individual channel radio| Qty 2 |




  
**Required Components:**
| Component | Purpose |
| --- | --- | 
| Adafruit ESP32-S2 TFT Feather 	 	"4264"	 | Gather WiFi data & control hardware modules | Qty 1 |
| Adafruit 5v ready Micro-SD | Breakout board store data that we can analyze with WiGLE / Python | Qty 1 |
| Adafruit Ultimate GPS Breakout | 66 channel w/10 Hz updates - Version 3 | Qty 1 |
| Seeedstudio XIAO  esp32-c3 | individual channel radio| Qty 14 |
| Seeedstudio XIAO  esp32-s3 | individual channel radio| Qty 2 |

**Optional Components:**
| Component | Purpose | 
| --- | --- |
| UF.L TO SMA | Add external RP SMA antenna                      |
| SMA Antenna  | 8 dbi RPSMA Antenna                            |
| LiPo Battery | Power your ESP32-S3 for portable applications |
| Clear case | Harbor Freight Apache 500 series clar case |
   
## Hardware Setup

**SD Reader Module** 
| SD Reader Pin | ESP32-S3 GPIO | Pin |
| --- | --- | --- |
| MISO | GPIO37 | MISO |
| MOSI | GPIO35 | MOSI |
| SCK | GPIO14 | SCK |
| CS | GPIO10 | D10 |

**GPS Module** 
| GPS Pin | ESP32-S3 GPIO |  Pin |
| --- | --- | --- |
| TX | GPIO1 | TX |
| RX | GPIO2 | RX |

 
 <img src="https://raw.githubusercontent.com/miami6/The_Wifydra-2023/main/Adafruit%20ESP32-S3%20TFT%20Feather%20Pinouts.jpg">
 

## Acknowledgements

 - [Awesome Readme Templates](https://awesomeopensource.com/project/elangosundar/awesome-README-templates)
  

## Badges

 

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit/) 
 
 
 <img src="https://github.com/miami6/ESP8266-Mini-Wardriver/blob/main/b_gWKr0k_400x400.jpeg">
