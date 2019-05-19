## To Do

### mqttt

* [ ] remove (most) console log messages
* [ ] window for broker settings - a.o. to avoid broker id and password in source code.
* [ ] indication of broker connection (green/red)
    * (re)connect-button with connected-indication
* [ ] keep track of last settings (iot-node, broker settings) using `localStorage`
    * [x] iot-node
* [x] clear inmessage-area button
* [x] no automatic clear for publish-area
* [x] responsive/mobile-friendly version
* [ ] world-hello verwijderen?

### iotnode-app

* [x] generate random node-id (i.s.o. fixed one: gives conflicts with multiple nodes running.)
    * [x] and keep node-id in localStorage
* [x] add: light level sensor (slider)
* [ ] how to activate 2 buttons at the same time?
* [x] keep "sensor settings" in localStorage (to assist "refresh")
* [x] responsive/mobile layout.
* [ ] window for broker settings
* [ ] indication of broker connection
