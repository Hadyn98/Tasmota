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




