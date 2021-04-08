# PiWiFi
Semi auto wifi vendo using esp8266
An upgrade version of the previous code which has removed LCD display and the button was used as a hard reset button.
Reset button must be pressed for 3 seconds during starting up the esp in order to reset it to default values.
It will start in an open Access Point mode with SSID = "PiWiFi". Settings defaul username and password = "admin".
Basic settings for vendo and network settings can be then accessed.
Most important things to remember are;
1. set your ip address,
2. ip address whould not be within the address pool of your mikrotik hotspot,
3. bind your esp8266 to your MT by copying the script code that can be found in the setting page of the vendo machine,
4. do the rest of the script,
5. follow the same schematics from the previous version just without the LCD.
Original hotspot html of mikrotik were used exept only for the login html. You need to copy *.jpg files in the /img folder.
Before copying the html file, open it with your favorite html editor, replace the ip address according to your esp8266 address in your network setup
