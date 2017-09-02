# ospiLCD


This is OpenSprinkler pi I2C LCD python script which gets data from ospi API and sends to I2C LCD.



Installation instructions
=====

Install RPLCD directly from `PyPI
<https://pypi.python.org/pypi/RPLCD/>`_ using pip:

    $ sudo pip install RPLCD

Intall smbus and i2c tools:

    $ sudo apt install python-smbus i2c-tools

Intall ospiLCD script:

    $ cd /home/pi/
    $ wget  https://raw.githubusercontent.com/stanoba/ospiLCD/master/ospiLCD.py
    $ chmod +x ospiLCD.py
    
Solder pin header to ospi board:

![pin header](/img/ospilcd2.jpg)

Connect I2C LCD to ospi pin header:

![pin header](/img/ospilcd3.jpg)

Run I2C scanner to detect all available address:

    $ sudo i2cdetect -y 1

You should see I2C LCD at address 0x27:

Schedule scipt via cron:

    $ crontab -e
    
Add folowing line to cron:

    */1 * * * * python /home/pi/ospiLCD.py
    
Note: Script is executed every minute.
