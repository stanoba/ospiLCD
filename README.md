# ospiLCD


This is OpenSprinkler pi I2C LCD python script which gets data from OpenSprinkler API and sends to I2C LCD.

**features:**
* 16x2 and 20x4 I2C LCDs are supported (PCF8574T based, after some changes MCP23008 is supported too)
* first two lines are identical to LCD on OpenSprinkler 2.x (with icons)
* third and fourth lines are displaying information based on ospi status (remaining watering time, water level in %, E1 stations status)
* LCD backlight is controlled from OpenSprinkler GUI (Brightness = 0 ->> OFF, Brightness > 1 ->> ON)
* LCD is refreshed in one minute interval (can be changed in cron)
* this script in combination with Raspberry pi and I2C LCD can be used as remote OpenSprinkler LCD


![ospiLCD](/img/ospilcd1.jpg)
![ospiLCD](/img/ospilcd9.jpg)


Installation instructions
=====

Install RPLCD library directly from [PyPI](https://pypi.python.org/pypi/RPLCD/) using pip:

    $ sudo pip install RPLCD

Intall smbus and i2c tools:

    $ sudo apt-get install python-smbus i2c-tools

Intall ospiLCD script:

    $ cd /home/pi/
    $ wget  https://raw.githubusercontent.com/stanoba/ospiLCD/master/ospiLCD.py
    $ chmod +x ospiLCD.py
    
Solder 2x3 pin header to ospi board:

![pin header](/img/ospilcd2.jpg)

Remove two 4K7 pull-up resistors from I2C LCD backpack:

![remove pull-ups](/img/ospilcd4.jpg)

Resistors are feeding 5V to Raspberry pi GPIO pins = not safe.

Connect I2C LCD to ospi pin header:

![gpio pins](/img/ospilcd3.jpg)

Run I2C scanner to detect all available address:

    $ sudo i2cdetect -y 1

You should see I2C LCD at address 0x27:
![i2c scan](/img/ospilcd8.jpg)

Edit parameters (osAddress, osPort, md5hash, LCDcols, LCDrows) according your ospi and LCD in /home/pi/ospiLCD.py:

    $ nano /home/pi/ospiLCD.py

Test the script if is working:

    $ /home/pi/ospiLCD.py

If the script is working without error, schedule it via cron:

    $ crontab -e
    
Add folowing line into cron:

    */1 * * * * python /home/pi/ospiLCD.py
    
Note: Script is executed every minute.

HW - I2C LCD bracket
=====
You can find connection PCB in HW folder.

![PCB1](/HW/ospiLCD_PCB.jpg)
![PCB2](/img/ospilcd8.jpg)
![PCB3](/img/ospilcd10.jpg)

PCB can be ordered [here](https://PCBs.io/share/zM39D).

3D Printed case
=====
STL files:https://www.thingiverse.com/thing:2576148

![case_bottom](/img/ospilcd11.jpg)
![case_top](/img/ospilcd12.jpg)


Output examples:
=====
Blue LCD 16x2:
![16x2 lcd](/img/ospilcd5.jpg)

Green LCD 20x4:
![20x4 lcd](/img/ospilcd6.jpg)

Green LCD 20x4 and ospi with expansion board (E1):
![20x4 lcd exp.](/img/ospilcd7.jpg)
