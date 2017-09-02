# ospiLCD


This is OpenSprinkler pi I2C LCD python script which gets data from ospi API and sends to I2C LCD.



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

![pin header](/img/ospilcd4.jpg)

Resistors are feeding 5V to Raspberry pi GPIO pins = not safe.

Connect I2C LCD to ospi pin header:

![pin header](/img/ospilcd3.jpg)

Run I2C scanner to detect all available address:

    $ sudo i2cdetect -y 1

You should see I2C LCD at address 0x27:

Schedule script via cron:

    $ crontab -e
    
Add folowing line into cron:

    */1 * * * * python /home/pi/ospiLCD.py
    
Note: Script is executed every minute.

Output examples:
=====
Blue LCD 16x2:
![pin header](/img/ospilcd5.jpg)

Green LCD 20x4:
![pin header](/img/ospilcd6.jpg)

Green LCD 20x4 and ospi with expansion board (E1):
![pin header](/img/ospilcd7.jpg)
