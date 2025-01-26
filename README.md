# hmip-mqtt_tasmota
Hommatic IP Tasmota Anbindung mit MQTT

## Voraussetzung

* HMIP CCU3
* ccu-jack https://github.com/mdzio/ccu-jack
* optional, aber sehr hilfreich ;-) MQTT Explorer https://github.com/thomasnordquist/MQTT-Explorer

## Einstellungen 

### Tasmota Gerät

* Einstellungen/MQTT Einstellungen (Configuration/Configre MQTT)
  * MQTT Server IP und Port: __192.168.1.200:1883__
  * Topic: __friendlyName__ (z. B. PLUG01)
  * Full Topic: __%topic%/%prefix%/__
 
* check im MQTT Explorer
  * Telemetriedaten Topic __PLUG01/tele__
    * __STATE__ über das Gerät
    * __SENSOR__ Sensordaten
   
## Geräte

### Nous A1T Zwischenstecker Schaltsteckdose 

#### ccu-jack

* Virtuelle Geräte/Erstellen
  * Gerätesymbol __HM-ES-PMSw1-Pl__
  * für Ein- und Ausschalten Kanal 1: __MQTT Schaltaktor mit Rückmeldung__
  * für Timer aktivieren/deaktivieren Kanal 2: __MQTT Schaltaktor mit Rückmeldung__
  * für Energiemessung Kanal 3: __MQTT Energiemessung__
 
#### CCU3

* Schaltaktor
  * SWITCH|COMMAND_TOPIC __PLUG01/cmnd/POWER__
  * SWITCH|ON_PAYLOAD __ON__
  * SWITCH|OFF_PAYLOAD __OFF__
  * SWITCH|FEEDBACK_TOPIC __PLUG01/stat/POWER__
  * SWITCH|ON_PATTERN __ON__
  * SWITCH|OFF_PATTERN __OFF__
  * SWITCH|MATCHER __EXACT__
* Timer an/aus
  * SWITCH|COMMAND_TOPIC	__PLUG01/cmnd/timers__
  * SWITCH|ON_PAYLOAD	__1__
  * SWITCH|OFF_PAYLOAD	__0__
  * SWITCH|FEEDBACK_TOPIC	__PLUG01/stat/RESULT__
  * SWITCH|ON_PATTERN	__"Timers":"ON"__
  * SWITCH|OFF_PATTERN	__"Timers":"OFF"__
  * SWITCH|MATCHER	__CONTAINS__
* Messwert-Kanal
  * POWERMETER|ENERGY_COUNTER_TOPIC __PLUG01/tele/SENSOR__
  * POWERMETER|ENERGY_COUNTER_PATTERN __{{(parseJSON .).ENERGY.Total}}__
  * POWERMETER|ENERGY_COUNTER_EXTRACTOR __TEMPLATE__
  * POWERMETER|POWER_TOPIC __PLUG01/tele/SENSOR__
  * POWERMETER|POWER_PATTERN __{{(parseJSON .).ENERGY.Power}}__
  * POWERMETER|POWER_EXTRACTOR __TEMPLATE__
  * POWERMETER|CURRENT_TOPIC __PLUG01/tele/SENSOR__
  * POWERMETER|CURRENT_PATTERN __{{(parseJSON .).ENERGY.Current}}__
  * POWERMETER|CURRENT_EXTRACTOR __TEMPLATE__
  * POWERMETER|VOLTAGE_TOPIC __PLUG01/tele/SENSOR__
  * POWERMETER|VOLTAGE_PATTERN __{{(parseJSON .).ENERGY.Voltage}}__
  * POWERMETER|VOLTAGE_EXTRACTOR __TEMPLATE__







