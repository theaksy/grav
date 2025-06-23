---
title: 'Receiving ADS-B Signals Using RTL1090 and Virtual Radar Server on Windows 10'
media_order: 'spider antenna schematic.jpeg,My Spider Antenna.jpg,SDR Waterfall.png,Map.PNG,Server.PNG,1090.PNG'
---

**ADS-B **stands for Automatic Dependent Surveillance–Broadcast and is transmitted by planes equipped with ADS-B-Out. The signal is broadcast on 1090MHz and includes the aircraft's GPS and avionics systems:
- Plane's position
- Altitude
- Heading
- Speed
- Flight ID

I used the RTL-SDR Blog V4 receiver, RTL1090 decoder and Virtual Radar Server. See [https://www.rtl-sdr.com/adsb-aircraft-radar-with-rtl-sdr/](RTL-SDR Tutorial) for more details.

### Install RTL1090

I downloaded the RTL1090 - IMU (Installer and Maintenance Utility) from [https://rtl1090.com/](https://rtl1090.com/). This gathered the files needed as well as zadig for installing the RTL-SDR drivers.

For some reason RTL1090 didn't pick up my RTL-SDR and I needed to install the drivers again with zadig.

The RTL1090 software requires some additional files. 
- libusb-1.0.dll
- rtlsdr.dll
- msvcr100.dll

Whilst the website says the can be downloaded from [http://web.archive.org/web/20130121051904/http://sdr.osmocom.org/trac/attachment/wiki/rtl-sdr/RelWithDebInfo.zip] these were out of date now. The versions that worked could be downloaded from the [https://github.com/rtlsdrblog/rtl-sdr-blog/releases](RTL-SDR Blog Driver GitHub releases page). The files above are available in the **x86** directory - just copy them into the directory with RTL1090.

Once installed, run the application and allow the firewall access pop up (this will be needed for Virtual Radar Server to connect). Click the **START** button and it should connect to the RTL-SDR and tune to 1090. The port the application has opened up is shown at the bottom of the window (and will be needed in Virtual Radar Server).

Once running and some planes are close it will start to list them as below.
![1090](1090.PNG "1090")

### Install Virtual Radar Server

Download the Windows installer from [https://www.virtualradarserver.co.uk/Download.aspx](https://www.virtualradarserver.co.uk/Download.aspx) and install. 

Once installed, launch from the Start Menu and then click **Tools -> Options...** to add in the connection to RTL1090. Click on **Receiver** and then use the **Wizard** to configure a connection to the RTL device. If it doesn't find the device check the port listed by RTL1090 as mentioned above.

After this launch [http://127.0.0.1/VirtualRadar](http://127.0.0.1/VirtualRadar) to see the mapping.

I used [https://www.flightradar24.com/54.38,0.16/8](FlightRadar24) to see planes that were coming close, to test if I was receiving them.

This is what the server looked like once it started to detect signals.
![Server](Server.PNG "Server")

And here is a plot of some of the planes on the Virtual Radar mapping
![Map](Map.PNG "Map")

### Viewing in SDR#
Here's what the signal looks like on a waterfall spectrum.
![SDR%20Waterfall](SDR%20Waterfall.png "SDR%20Waterfall")


### Create a Spider Antenna

I followed the guidance [https://discussions.flightaware.com/t/three-easy-diy-antennas-for-beginners/16348/2](here) to create an antenna specifically tuned for 1090MHz.

I used this schematic, and built an 8-legged antenna.
![spider%20antenna%20schematic](spider%20antenna%20schematic.jpeg "spider%20antenna%20schematic")

Here's the finished antenna - much smaller than I expected!
![My%20Spider%20Antenna](My%20Spider%20Antenna.jpg "My%20Spider%20Antenna")


### Follow on
- Try feeding data into an online service