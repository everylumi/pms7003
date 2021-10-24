# PMS7003 sensor

The code reads PM values from serial port. Tested on Raspberry Pi, but it should work on any machine with Python and serial port.

Device description: <https://aqicn.org/sensor/pms5003-7003/>

## Installation

```sh
cd ~/Downloads/ && sudo rm -rf pms7003 
git clone https://github.com/everylumi/pms7003.git
cd pms7003/  
sudo python3 setup.py install #Python3  
```

## Uninstallation

```sh
sudo pip3 uninstall pms7003 #Python3  
```


## Usage example

```python
from pms7003 import Pms7003Sensor, PmsSensorException

if __name__ == '__main__':

    sensor = Pms7003Sensor('/dev/ttyUSB0')

    while True:
        try:
            print(sensor.read())
        except PmsSensorException:
            print('Connection problem')

    sensor.close()
```

The read function has an option of returning values as a dict or OrderedDict.

```python
sensor.read(ordered=True)
```


## License

This project is licensed under the terms of the MIT license.
