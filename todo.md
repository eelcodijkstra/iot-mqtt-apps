## To Do

### mqttt

* [ ] remove (most) console log messages
* [ ] window for broker settings - a.o. to avoid broker id and password in source code.
* [ ] indication of broker connection (green/red)
    * (re)connect-button with connected-indication
* [ ] keep track of last settings (iot-node, broker settings) using `localStorage`    
* [x] clear inmessage-area button
* [x] no automatic clear for publish-area

Suggestion:

* mqtt0.html - for raspberrypi.local
* mqtt1.html - for arbitrary broker, with window for brokername, username,
password

### iotnode-app

* [ ] generate random node-id (i.s.o. fixed one: gives conflicts with multiple nodes running.)
* [ ] add: light level sensor (slider)
