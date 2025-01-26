# Allgemeine Einstellungen

## Zeitzone und Koordinaten 

MEZ (irgendwo in Berlin)

`Backlog TimeSTD 0, 0, 10, 1, 3, 60; TimeDST 0, 0, 3, 1, 2, 120; timezone 99; Latitude 52.45; Longitude 13.41; time`

## Feste IP Adresse 

`IPAddress1 192.168.1.x`

# Zwischenstecker

## Einschalten-Status

`PowerOnState 3`

* 0 / OFF = keep relay(s) OFF after power up \\
* 1 / ON = turn relay(s) ON after power up \\
* 2 / TOGGLE = toggle relay(s) from last saved state \\
* 3 = switch relay(s) to their last saved state (default) \\
* 4 = turn relay(s) ON and disable further relay control \\

## Spannung

`VoltageSet 230`

## Leistung 

`PowerSet 56.0`
