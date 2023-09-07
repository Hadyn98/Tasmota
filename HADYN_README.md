15-nov-22

2-dec-22
its D5  sda
d6  scl
d1  vindriktning

==


programmed with tasmota-allsensors.v10.0.0.4bin.gz

attached:
i2c   bme680
vindriktning
IAQ-Core eCo2n


taken from https://blakadder.com/vindriktning-tasmota/


trying - DIDNT WORK
IO0/IO2->SCL/SDA with pull-ups






trying   from https://tasmota.github.io/docs/devices/Sonoff-Basic-and-BME280/#connect-bme280-to-sonoff-basic-based-on-the-gpio-locations
failed
TX GPIO1   SCL
RX GPIO3 SDA




try mentioned in comments on blackadders page
failed
D3 GPIO0 	I2C SDA
D4 GPIO2 	I2C SCL


PIN D1 GPIO5 VINDRIKTNING for data from air sensor


DEFINITELY
D1 GPIO5 	VINDRIKTNING




interesting mention here of tasmotizer
https://arnowelzel.de/en/ikea-vindriktning-with-tasmota-and-scd30


7-jun-2023
soldered new board up, with air sensor and temp/humidity sensor
not vindrinkting just yet
i2c scl green   d4
i2c sda brown   d5

program using chrome and https://web.esphome.io/
you will see USB2.0-Ser!   , I think use that 

update: from webpage above, I 'm using tamotizer , saved in 
C:\Users\HaydenVanderBerg\Documents\personal\projects\20221202 ESP32-tasmota program

now programmed with ESP-Flasher-Windows-x64.exe  from above directory, dated 4-dec-2021
but this shows in INFORMATION, prog flash size=4mb, flash size=4mb, but only 1MB available (700kb program, 300kb free)
so dont use esp-flasher-windows-x64

try with  tasmotizer
also FS = PFS = 4mb,  PS=700kb, and free=300kb



now programming with https://tasmota.github.io/install/ on chrome,   tasmota all sensors english, presumably latest version as of today  12.5.0.4(allsensors)
this has done different. fs = 4mb, prog fs=1mb (smaller), ps = 740kb, and free=260kb. 


7-sept-23
now formally have a github account. forked the tasmota project, and linked it to gitpod.  I will modify the user settings files to include the 2 i2c devices, and try to force 4MB program size. as of 7-sept-23, the tasmota version is  
http://ota.tasmota.com/tasmota/release/
These binaries are built using core 2.7.4.9
Release binaries for Tasmota firmware 13.1.0 on ESP8266


have modified  these 2 files:
* tasmota/user_config_override.h 
* /platformio_override.ini


built 4M program size, with filesystem support

programmed with tasmotizer  ver1.2 , then rebooted, then send-config with wifi details 
running i2cscan gives

17:29:39.490 CMD: i2cscan
17:29:39.510 RSL: RESULT = {"I2CScan":"Device(s) found at 0x5a 0x76"}

STATE = {"Time":"1970-01-01T00:00:16","Uptime":"0T00:00:11","UptimeSec":11,"Heap":23,"SleepMode":"Dynamic","Sleep":50,"LoadAvg":1191,"MqttCount":0,"Wifi":{"AP":1,"SSId":"asus_2.4g","BSSId":"30:5A:3A:6D:F8:C8","Channel":4,"Mode":"11n","RSSI":86,"Signal":-57,"LinkCount":1,"Downtime":"0T00:00:03"}}
17:29:16.650 CMD: 

00:00:00.087 Project tasmota - Tasmota Version 13.1.0.2(tasmota)-2_7_4_9(2023-09-07T16:04:47)
00:00:00.528 WIF: Connecting to AP1 asus_2.4g Channel 4 BSSId 30:5A:3A:6D:F8:C8 in mode 11n as tasmota-03921F-4639...
00:00:01.754 WIF: Connected
00:00:02.008 HTP: Web server active on tasmota-03921F-4639 with IP address 192.168.1.21
00:00:08.656 RSL: INFO1 = {"Info1":{"Module":"Generic","Version":"13.1.0.2(tasmota)","FallbackTopic":"cmnd/DVES_03921F_fb/","GroupTopic":"cmnd/tasmotas/"}}
00:00:08.661 RSL: INFO2 = {"Info2":{"WebServerMode":"Admin","Hostname":"tasmota-03921F-4639","IPAddress":"192.168.1.21"}}

D3 GPIO0	     SDA
D4 GPIO2      SCL

BME280 Temperature	26.6 °C
BME280 Humidity	53.1 %
BME280 Dew point	16.2 °C
BME280 Pressure	1012.6 hPa
iAQ-Core	Start

working well , although after a short time, IAQ still says start.?!
didn't solder it to vindrikting module





TODO check vindrikting works
TODO see an update from IAQ (instead of start)
TODO set the module and auto set the pins for i2c sda scl
