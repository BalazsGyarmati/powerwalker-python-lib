## About
There was no Linux software available for the PowerWalker PDU and ATS, but the [manufacturer](https://powerwalker.com/) was kind enough to supply me with what I needed to make my own library.

![PowerWalker PDU and ATS in my homelab](media/homelab.jpg)

I'm using a Raspberry Pi as my power manager, it is connected to both the PDU and ATS. I'm planning to use MQTT to communicate with it, and report power usage etc. to things like Home Assistant. For graphing I'll be storing values in Elasticsearch and displaying the data using Kibana.

**Beta!** This library is still very much in beta, and the ATS support is not yet implemented, I'm working on it.

## PowerWalker PDU RC-16A IEC
![PowerWalker PDU RC-16A IEC](media/powerwalker_pdu_rc-16a.jpg)

PowerWalker PDU RC-16A is designed to distribute AC power from a single source to 8 outputs with advanced load monitoring and local or remote ON/OFF switching control of individual outlets.

### Output status codes
0. Off
1. On
2. Shutdown active
3. Shutdown imminent (S01-S08 code)
4. Restore active
5. Overload alarm (F01-F08 code)
6. Locked (L01-L08 code)

https://powerwalker.com/?lang=en&page=product&item=10133001

## PowerWalker ATS
![PowerWalker ATS](media/powerwalker_ats.jpg)

ATS (Automatic Transfer Switch) supports connection of two independent power sources. If primary power source fails, the secondary will automatically back up the connected load without any interruption. 

https://powerwalker.com/?page=product&item=10120543&lang=en

## Scripts
* `status.py`: Get and print statuses
* `info.py`: Get and print device information
* `mqtt.py`: Publishing values to a MQTT broker