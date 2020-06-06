## MyEMS MQTT Publisher Service

### Introduction
This service is a component of MyEMS to publish data to MQTT broker.



### Prerequisites

paho-mqtt

mysql.connector

### Installation

Download and install MySQL Connector:
```
    $ cd ~/tools
    $ wget https://dev.mysql.com/get/Downloads/Connector-Python/mysql-connector-python-8.0.20.tar.gz
    $ tar xzf mysql-connector-python-8.0.20.tar.gz
    $ cd ~/tools/mysql-connector-python-8.0.20
    $ sudo python3 setup.py install
```

Download and install paho-mqtt:
```
    $ cd ~/tools
    $ git clone https://github.com/eclipse/paho.mqtt.python.git
    $ cd ~/tools/paho.mqtt.python
    $ sudo python3 setup.py install
```

Install myems-mqtt-publisher service
```bash
    $ cd ~
    $ git clone https://github.com/myems/myesm-mqtt-publisher.git
    $ sudo cp -R ~/myems-mqtt-publisher /myems-mqtt-publisher
    $ cd /myems-mqtt-publisher
    $ sudo git checkout master (or the release tag)
```
Open config file and edit database configuration
```bash
    $ sudo nano config.py
```
Setup systemd service:
```bash
    $ sudo cp myems-mqtt-publisher.service /lib/systemd/system/
```
Enable the service:
```bash
    $ sudo systemctl enable myems-mqtt-publisher.service
```
Start the service:
```bash
    $ sudo systemctl start myems-mqtt-publisher.service
```


### References
  [1]. http://myems.io
  
  [2]. https://www.eclipse.org/paho/clients/python/

