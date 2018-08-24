## MQTT test (mqttt)

Deze (statische) web-app is bedoeld om het MQTT-protocol (via websockets) in de browser te testen en te demonstreren:

* bewaken (monitoring) en besturen van een op te geven IoT-knoop;
* subscribe voor een op te geven topic (mogelijk met wildcards);
* publish voor een op te geven topic.

Deze toepassing moet gebruikt worden met een MQTT-broker (bijv. mosquitto) die MQTT over websockets ondersteunt.
Het is handig als deze broker ook als http-server gebruikt kan worden.

Voor het testen van deze toepassing is een (lokale) *http-server* nodig.
Dit kan bijvoorbeeld via de ingebouwde webserver van **Brackets**, of met Live server (Atom).

Interfacebeschrijving:

* http://www.eclipse.org/paho/files/jsdoc/Paho.MQTT.Client.html
* http://www.eclipse.org/paho/files/jsdoc/Paho.MQTT.Message.html
* voor het versturen van een mqtt-message: 
  * eerst, aanmaken van een Message-object, met de *payload*
  * vervolgens (*verplicht*): invullen van `destinationName` (het mqtt-topic);
  * tenslotte, versturen van het bericht.

Voorbeeld - versturen van een MQTT-bericht

``` javascript
var message = new Paho.MQTT.Message("Hello"); // payload
message.destinationName = "World";            // topic
client.send(message);
```

Voorbeeld - ontvangen van bericht vial callback-function.

```javascript
var client = new Paho.MQTT.Client(mqttbroker.hostname, Number(mqttbroker.port), "clientId");

// set callback handlers
client.onConnectionLost = onConnectionLost;
client.onMessageArrived = onMessageArrived;

function onMessageArrived(message) {
  console.log("onMessageArrived:" + message.payloadString);
  console.log("destination: " + message.destinationName); // topic
}

```

Voorbeeld - subscribe

``` javascript
client.subscribe("+/+/+");
```

De `connect`-opdracht maakt contact met de broker.
Hierbij geef je ook de eventuele authenticatie-gegevens op.
Je moet er verder rekening mee houden dat de verbinding met de broker op allerlei manieren onderbroken kan worden.
Het is verstandig om regelmatig te controleren of de verbinding nog bestaat, en zo nodig opnieuw te verbinden.

``` javascript
client.connect({
  userName: "myusername", password: "mypassword",
  onSuccess: onConnect, onFailure: onFailure});
``` 

### Lokale broker

Je kunt mqttt ook gebruiken met een lokale mqtt-broker, bijvoorbeeld een Raspberry Pi.
Vaak kun je voor de lokale broker een lokale domeinnaam gebruiken (via mDNS).
Als dat niet lukt, moet je het IP-adres gebruiken.

``` javascript
var mqttbroker = {
    hostname: "raspberrypi.local",
    port: 1884
};
```

Opmerking: MQTT via TCP gebruikt (default) poort 1883. Het websockets-interface gebruikt poort 1884.

### Links

* http://micropython-iot-hackathon.readthedocs.io/en/latest/mqtt.html
* https://github.com/micropython/micropython-lib/tree/master/umqtt.simple

## iotnode-app

Dit is een web-app waarmee je een IoT-knoop kunt simuleren.
Deze web-app communiceert via websockets met 
Dit programma kun je in combinatie met mqttt gebruiken: daarmee kun je beide programma's testen.

