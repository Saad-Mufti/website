## Status Screen on an MCU
*View the source on [GitHub](https://github.com/Saad-Mufti/arduino-status-screen)*
Lately I've felt that I haven't done anything "fun" on an embedded device, since much of my projects on MCUs have mainly been focused on meeting some kind of goal to solve a problem that I find important. 

For example, a while back I made a prototype for a wearable device with sensors to attempt to detect when the wearer might be in danger, and the onboard GPS module would send a text via SMS to any trusted contacts, along with the local authorities. It ended up looking something like this:
![wearable device prototype](/img/wearable.jpg)

That was one of my first endeavors with embedded devices, and although the design presented significant challenges with my limited resources available, it was what really got me into building small but powerful things with tiny computers.

Building this wearable prototype was also a tangible way of attacking a problem that otherwise seems difficult for me to take on otherwise: automating 911 calls. 

This time, however, I decided instead to skip the "big problem" portion of the design. 

**Put simply, I wanted a device that, when plugged into my PC, would display some information in a dashboard-like manner.**

Specifically, I was looking to display metrics like: 
- My typing speed (in WPM)
- Ambient temperature (or my internal PC temp.)
- CPU/RAM usage

I also considered displaying information of the MCU itself, like:
- Current SSID (Network name)
- WiFi Signal strength (in dB)
- Input voltage

Finally, if I would have sufficient screen space at the end, I also wanted to pull some data from a REST API to show other potentially useful metrics:
- Local weather info
- Stock tickers
- Unread emails (I'd have to look more into if this would be possible or not)

These metrics vary in difficulty to implement, so as of the time of writing, I only have a subset of these indicators figured out. *Stay tuned for further updates*.

Here's what my dashboard looks like so far:
![status screen](/img/status.jpg)

Regardless, there are clearly three sources where I can pull data from:
1. My PC (connected to the MCU via USB)
2. The device itself (through its internal API)
3. The web (through a protocol like HTTP)

I have features from the first two categories so far, but I'll describe how one can pull this data from any of these sources.

#### Pulling data from my PC
The MCU would be connected to my PC via USB, which is a form of (serial communication)[https://en.wikipedia.org/wiki/Serial_communication]. Most MCUs have a relatively straightforward way of reading and sending serial data, so this didn't end up being a significant challenge, except for the fact that I would have to provide the data I wanted by myself. There isn't anything built into Windows et. al., as far as I know, that allows me to collect the data I want. 

My solution was to write a simple Python script to periodically send serial data 

#### Pulling data from the MCU
This is the most straightforward of the three sources. 

#### Pulling from the web
I haven't gotten around to pulling data from the web, 