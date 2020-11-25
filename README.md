## MyEMS MQTT Publisher Service

### Introduction
This service is a component of MyEMS to publish data to MQTT broker.

[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/myems/myems-mqtt-publisher/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/myems/myems-mqtt-publisher/?branch=master)

### Prerequisites
simplejson

paho-mqtt

mysql.connector

### Installation

Download and Install simplejson
```
    $ cd ~/tools
    $ git clone https://github.com/simplejson/simplejson.git
    $ cd simplejson
    $ sudo python3 setup.py install 
```

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
```
    $ cd ~
    $ git clone https://github.com/myems/myesm-mqtt-publisher.git
    $ sudo git checkout master (or the release tag)
    $ sudo cp -R ~/myesm-mqtt-publisher /myesm-mqtt-publisher
```
    Eidt the config
```
    $ sudo nano /myems-myesm-mqtt-publisher/config.py
```
    Setup systemd service:
```
    $ sudo cp /myems-myesm-mqtt-publisher/myems-myesm-mqtt-publisher.service /lib/systemd/system/
    $ sudo systemctl enable myems-myesm-mqtt-publisher.service
    $ sudo systemctl start myems-myesm-mqtt-publisher.service
```

### Topic
topic_prefix in config and point_id

Example:
```
'myems/point/3'
```

### Payload
data_source_id, the Data Source ID.

point_id, the Point ID.

object_type, the type of data, is one of 'ANALOG_VALUE'(decimal(18, 3)) , 'ENERGY_VALUE'(decimal(18, 3)) and 'DIGITAL_VALUE'(int(11)).

utc_date_time, the date time in utc when data was acquired. The full format looks like 'YYYY-MM-DDTHH:MM:SS'.

value, the data value in Decimal or Integer.

Example:
```
{"data_source_id": 1, "point_id": 3, "object_type": 'ANALOG_VALUE', "utc_date_time": "2020-09-28T03:23:06", "value": Decimal('591960276.000')}
```

### References
  [1]. http://myems.io
  
  [2]. https://www.eclipse.org/paho/clients/python/
  
  [3]. https://simplejson.readthedocs.io/

