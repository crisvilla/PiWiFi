# PiWiFi
PiWiFi 103 - just set default button in flasher and upload the bin file.

PiWiFi 102 - trying to get rid of the EEPROM reset during startup.

PiWiFi 101 - Second bonus open, EEPROM reset was rectified, don't forget to create MT hotspot profile "vendo".

Semi auto wifi vendo using esp8266
An upgrade version of the previous code which has removed LCD display and the button was used as a hard reset button.
Reset button must be pressed for 3 seconds during starting up the esp in order to reset it to default values.
It will start in an open Access Point mode with SSID = "PiWiFi". Settings defaul username and password = "admin".
Basic settings for vendo and network settings can be then accessed.
Most important things to remember are;
1. set your ip address,
2. ip address whould not be within the address pool of your mikrotik hotspot,
3. bind your esp8266 to your MT by copying the script code that can be found in the setting page of the vendo machine,
4. open mikrotik terminal and paste:"/ip hotspot ip-binding add type=bypassed mac-address=(esp8266 MAC address)"
5. do the same: "/ip firewall filter add action=accept chain=input place-before=0 src-address=(esp8266 ip address)"
6. do the same: "/ip hotspot walled-garden ip add action=accept disabled=no dst-address=(esp8266 ip address)"
7. follow the same schematics from the previous version just without the LCD.
8. Create in mikrotik hotspot user profile = "vendo" and add the in script tab;
9. On login and On logout: 
    #removing user from hotspot
    :local x
    :foreach expired in [/ip hotspot user find profile="vendo"] do={
    :if ([/ip hotspot user get $expired uptime]>=[/ip hotspot user get $expired limit-uptime]) do={/ip hotspot user remove $expired}
    }
Original hotspot html of mikrotik were used exept only for the login html. You need to copy *.jpg files in the /img folder.
Before copying the html file, open it with your favorite html editor, replace the ip address according to your esp8266 address in your network setup
