# ospiLCD


This is OpenSprinkler pi I2C LCD python script which gets data from ospi API and sends to I2C LCD.



Install instructions
=====

Install RPLCD directly from `PyPI
<https://pypi.python.org/pypi/RPLCD/>`_ using pip:

    $ sudo pip install RPLCD

Intall smbus and i2c tools:

    $ sudo apt install python-smbus i2c-tools
    
Run I2C scanner to detect all available address:

    $ sudo i2cdetect -y 1

You should get output similar to this:
