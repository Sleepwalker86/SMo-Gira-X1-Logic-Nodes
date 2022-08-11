Logic Nodes for the Gira X1

# Logikbaustein Poolsteuerung Gira X1

Der Baustein ist für die Steuerung einer Umwelzpumpe und einem Umschaltventil für zb. Sonnenkollektoren gedacht, die über einen Bypass angeschlossen sind.
Der Baustein startet immer mit dem Start der Pumpe bis die Prüfzeit abgelaufen ist und schaltet anschließend um auf Heizen Ventil = 1.
Nach Ablauf der Prüfzeit wird geprüft ob die Temperatur am Eingang „Rücklauftemperatur“  größer oder kleiner ist als der Eingang  „Vorlauftemperatur“.
Rücklauf größer als Vorlauf -> weiter Heizen und nach Prüfzeit erneut Temperaturen vergleichen
Rücklauf kleiner als Vorlauf -> Ventil = 0, umschalten auf Zirkulieren und nach Ablauf der Pufferzeit erneut auf heizen umschalten Ventil = 1.
Liegt am Eingang „Filtern“ eine „1“ an, wird nur Zirkuliert und der Ausgang „Ventil“ schaltet nicht ein.
Liegt am Eingang „Wasserdruck Sensor“ eine „0“ an, startet der Baustein nicht bzw. es wird der Ausgang „Pumpe“ und „Ventil“ auf „0“ gesetzt.

Folgende Eingänge stehen zur Verfügung:

- Freigabe (Bool)
- Wasserdruck Sensor (Bool)
- Solltemperatur (Float)
- Vorlauftemperatur (Float)
- Rücklauftemperatur (Float)
- Filtern (Bool)

Folgende Parameter stehen zur Verfügung:

- Temperaturdifferenz, Vor/Rücklauf (Double)
- Pufferzeit (Integer)
- Prüfzeit (Integer)
- Wartezeit Ventilumschaltung / Sek.
- Folgende Ausgänge stehen zur Verfügung:

- Pumpe (Anschluss Pumpe, Bool)
- Ventil (Anschluss Ventil, Bool)
- Debug (Ausgabe aktueller Vorgang + Zeitstempel, String)
- Freigabe 

- Der Eingang „Freigabe“ dient zum aktivieren des Bausteins.
Liegt am Eingang eine „1“ an startet der Baustein, trifft eine „0“ ein stoppt der Baustein.

- Wasserdruck Sensor 
Der Eingang „Wasserdruck Sensor“ kann dazu verwendet werden, einen Druckabfall auszuwerten falls die Pumpe oberhalb des Wasserpegels steht. Fällt der Druck ab und es trifft am Eingang eine „0“ ein schaltet die Pumpe ab solange bis wieder eine „1“ eintrifft. (Default = true)

- Solltemperatur
Hier muss eine Vorgabetemperatur eintreffen oder fest in den Parametern definiert werden.
Es wird somit versucht auf diese Temperatur zu heizen und beim Überschreiten der Temperatur wird nur noch Zirkuliert und nicht mehr geheizt.

- Vorlauftemperatur
Hier muss die Temperatur eintreffen die die aktuelle Poolwasser Temperatur darstellt. Es gilt als Vergleichswert zur Soll und Rücklauftemperatur. 

- Rücklauftemperatur
Hier muss die Temperatur eintreffen die nach den Sonnenkollektoren gemessen wird. Dieser Wert wird verwendet um zu entscheiden ob das Ventil geöffnet oder geschlossen wird.

- Filter
Der Eingang Filter dient dazu zb. Bei schlechtem Wetter ein ständiges umschalten zu verhindern.
Liegt an dem Eingang eine „1“ an wechselt der Baustein nicht in den Heizbetrieb, das Ventil bleibt dementsprechend auf „0“.

Bei mir kommt der Wert von der PV Anlage, wenn länger eine gewisse Leistung unterschritten ist schalte ich um auf Zirkulieren. (Default = 0)

- Temperaturdifferenz, Vor/Rücklauf
Hier wird der Wert angegeben um wieviel Grad das Wasser wärmer sein soll das von den Kollektoren kommt als das was am Eingang Vorlauftemperatur anliegt. (Default = 0,3 °C)

- Pufferzeit
Dieser Wert gibt an wie lange gewartet werden soll in Minuten bis vom Zirkulieren wieder ins heizen umgeschaltet werden soll um erneut zu prüfen ob jetzt Sonne da ist und das Wasser wärmer vom Rücklauf zurück kommt als der Vorlauf. (Default = 60 Minuten)

- Prüfzeit
Dieser Wert gibt an wie lange gewartet werden soll, wenn geheizt wird, bis Vor und Rücklauf gegeneinander geprüft werden.
(Default = 10 Minuten)

- Wartezeit Ventilumschaltung / Sek.
Dieser Wert gibt an wie lange zum umschalten des Ventils in den Heiz- oder Zirkulierbetrieb die Pumpe ausgeschaltet werden soll damit nicht bei Last umgeschaltet wird. (Default = 15 Sekunden)

Verwendetes Icon:
Schwimmbad Icons erstellt von xnimrodx - Flaticon


# Logikbaustein Divera Gira X1

Der Logikbaustein ruft über die API von Divera in Verbindung mit dem API Key aktuelle Einsatzdaten ab.
Jedes mal wenn der Baustein am Eingang „Trigger“ eine 1 bekommt startet die Abfrage der Daten erneut.

Folgende Parameter werden an den Ausgängen ausgegeben:

- Einsatzalarm (0= kein Einsatz, 1= Einsatzalarm liegt an, Bool)
- Stichwort (Alarmstichwort, String)
- Meldung (Meldungstext, String)
- Adresse (String)
- Datum (Alarmierungszeitpunkt, DateTime)
- Sonderrechte (Bool)
- Angaben zum Gebäude (String)
- Anrufer (String)
- Patient (Zeichenfolge)
- Bemerkung (String)
- Anzahl gelesen (Integer)
- Einsatznummer (String)
- Impuls (Bool)
- Json (Ausgabe der kompletten Json Abfrage zum debuggen, String)


Folgende Eingänge/Parameter stehen zur Verfügung:
- Trigger (Startet den Baustein neu, Bool)
- API Key (Angabe des API Keys die von Divera bereitgestellt wird, String)

Hinweis:
Der Intervall zum Triggern des Bausteins sollte nicht zu klein sein um des Gira X1 nicht zu überlasten.
Ein Intervall von 20-30 Sekunden ist sinnvoll.

###Changelog###

Version 1.0.22
Ausgänge um die Einsatznummer und einen Impuls erweitert
Impuls wird ausgelöst wenn sich das Datum bzw. die Uhrzeit ändert.

Version 1.0.20
Abfangen von Nullwerten die ein Fehler des Baustein auslösen.

#Link zur Divera API Dokumentation:
https://api.divera247.com/?urls.primaryName=api%2Fv1#/E

Verwendetes Icon:
https://www.flaticon.com/de/kostenlose-icons/alarm Alarm Icons erstellt von Freepik - Flaticon


# Logikbaustein MQTT Publish Gira X1

Dieser Baustein sendet beim eintreffen am Eingang „Message“ einen String an einen MQTT Broker mit dem angegebenen Topic.

Folgende Eingänge stehen zur Verfügung:
- Message (String)

Folgende Parameter stehen zur Verfügung:
- Host (IP Adresse des Brokers, String)
- Topic (String)

Folgende Ausgänge stehen zur Verfügung:
- Debug (Ausgabe von Fehlern und der gesendeten Nachricht, String)

# Logikbaustein MQTT Subscribe Gira X1

Dieser Baustein empfängt eine Nachricht von einen MQTT Server mit dem angegebenen Topic und leitet diese an den Ausgang  „Message“ weiter.(String)

Folgende Eingänge stehen zur Verfügung:
- Enable(Bool, Hier muss der Datenpunkt vom X1 "Bereit" angegeben werden)

Folgende Parameter stehen zur Verfügung:
- Host (IP Adresse des Brokers, String)
- Topic (String)

Folgende Ausgänge stehen zur Verfügung:
- Message(Ausgabe von der empfangenen Nachricht, String)
- Debug(Ausgabe von Fehlern, String)

Dieser Baustein muss in der Simulation im GPA vorm beenden der Simulation am Eingang "Enable" mit einer 0 beendet werden.

