Logic Nodes for the Gira X1

# Logikbaustein Pollenflug Gira X1

Dieser Baustein fragt den Pollenflug-Gefahrenindex vom Deutschen Wetterdienst für drei Tage ab und gibt den Index an den entsprechenden Ausgang weiter.
Zusätzlich gibt es für jedes Gewächs einen Ausgang der bei überschreiten der eingestellten Schwelle für diesen Tag ein „True“ ausgibt.

Folgende Eingänge stehen zu Verfügung:
- Trigger (Bool)

Folgende Parameter stehen zu Verfügung:
- Region (Integer)
- Partregion (Integer)
- Warnschwelle(Integer, 1=niedrig,2=mittel,3=hoch)

Folgende Ausgänge stehen zu Verfügung:

- Roggen übermorgen (String)
- Roggen heute (String)
- Roggen morgen (String)
- Roggen Warnung (Bool)
- Beifuss übermorgen (String)
- Beifuss heute (String)
- Beifuss morgen (String)
- Beifuss Warnung (Bool) 
- Birke übermorgen (String)
- Birke heute (String)
- Birke morgen (String)
- Birke Warnung (Bool)
- Graeser übermorgen (String)
- Graeser heute (String)
- Graeser morgen (String)
- Graeser Warnung (Bool)
- Esche übermorgen (String)
- Esche heute (String)
- Esche morgen (String)
- Esche Warnung (Bool)
- Hasel übermorgen (String)
- Hasel heute (String)
- Hasel morgen (String)
- Hasel Warnung (Bool)
- Erle übermorgen (String)
- Erle heute (String)
- Erle morgen (String)
- Erle Warnung (Bool)
- Ambrosia übermorgen (String)
- Ambrosia heute (String)
- Ambrosia morgen (String)
- Ambrosia Warnung (Bool)
- Region Name (String)
- Debug (String)

https://www.flaticon.com/de/kostenlose-icons/pollen Pollen Icons erstellt von Freepik - Flaticon



DWD Dokumentation: https://opendata.dwd.de/climate_environment/health/alerts/Beschreibung_pollen_s31fg.pdf

# Logikbaustein Tankerkoenig Gira X1

Dieser Baustein fragt aktuelle Spritpreise von Tankerkoenig.de ab.

Folgende Eingänge stehen zur Verfügung:
- Trigger (Bool)

Folgende Parameter stehen zur Verfügung:
- API Key (String)
- geographische Breite des Standortes
- geographische Länge
- Suchradius in km
- Spritsorte(e5, e10,diesel, all)
- Sortierung(price, dist)

Folgende Ausgänge stehen zur Verfügung:
- Json (String)
- Name (String)
- Straße (String)
- Distanz (Double)
- Diesel (Double)
- E5 (Double)
- E10 (Double)
- Offen (Bool)
- Hausnummer (String)
- PLZ (Integer)
- Preis (Double, Dieser Ausgang wird nur beschrieben wenn nach einer Spritsorte gefiltert wird)

## Changelog
V 1.0.8 Behebt den Fehler das wenn eine Tankstelle nicht für alle Kraftstoffe einen Preis zurück gibt der Download fehl schlägt.

API https://creativecommons.tankerkoenig.de/

Verwendetes Icon :<a href="https://www.flaticon.com/free-icons/gas-station" title="gas station icons">Gas station icons created by DinosoftLabs - Flaticon</a>

# Logikbaustein PiHole Gira X1

Dieser Baustein fragt die PiHole Status API in eurem Netzwerk ab.

Trifft eine „1“ am Eingang „Trigger“ ein wird die API abgefragt und an die Ausgänge weitergeleitet.

Folgende Eingänge stehen zur Verfügung:
- Trigger (Bool)

Folgende Parameter stehen zur Verfügung:
- Host (String)

Folgende Ausgänge stehen zur Verfügung:
- domains_being_blocked (Integer)
- dns_queries_today (Integer)
- ads_blocked_today (Double)
- public double ads_percentage_today (Integer)
- unique_domains (Integer)
- queries_forwarded (Integer)
- queries_cached (Integer)
- clients_ever_seen (Integer)
- unique_clients (Integer)
- dns_queries_all_types (Integer)
- reply_UNKNOWN (Integer)
- reply_NODATA (Integer)
- reply_NXDOMAIN (Integer)
- reply_CNAME (Integer)
- reply_IP (Integer)
- reply_DOMAIN (Integer)
- reply_RRNAME (Integer)
- reply_SERVFAIL (Integer)
- reply_REFUSED (Integer)
- reply_NOTIMP (Integer)
- reply_OTHER (Integer)
- reply_DNSSEC (Integer)
- reply_NONE (Integer)
- reply_BLOB (Integer)
- dns_queries_all_replies (Integer)
- privacy_level (Integer)
- file_exists (Bool)
- status (String) 
- absolute (Integer)
- days (Integer)
- hours (Integer)
- minutes (Integer)
- Aktive (Bool, 1= Status enabled 0= Status disabled)

API PiHole https://discourse.pi-hole.net/t/pi-hole-api/1863

Verwendetes Icon https://www.flaticon.com/free-icons/hand Hand icons created by Freepik - Flaticon

# Logikbaustein Auswerten	Gira X1

Dieser Baustein wertet am Eingang „Wert“ eintreffende Zahlen aus und gibt folgende Ergebnisse am Ausgang „Ergebnis“ zurück.
Am Parameter „Modus“ muss ein unten aufgelisteter Modus gewählt werden.
Der Parameter begrenzt die maximalen Werte zur Berechnung am Eingang „Wert“.
Der Eingang	„Reset“ dient dazu die Warteliste zu löschen und den Baustein erneut zu starten.

Modus:
- Min -> Minimum
- Max -> Maximum
- AVG -> Durchschnitt
- First -> Erster eingetroffener Wert
- Last -> letzter eingetroffener Wert

Folgende Eingänge stehen zu Verfügung:
- Wert (Double)
- Reset (Bool)

Folgende Parameter stehen zu Verfügung:
- Modus (String)
- Anzahl Werte (Integer)

Folgende Ausgänge stehen zu Verfügung:
- Ergebnis (Double)
- Debug (String)

Verwendetes Icon : <a href="https://www.flaticon.com/de/kostenlose-icons/mathe" title="mathe Icons">Mathe Icons erstellt von Freepik - Flaticon</a>

# Logikbaustein MQTT Subscribe Gira X1

Dieser Baustein empfängt eine Nachricht von einen MQTT Server mit dem angegebenen Topic und leitet diese an den Ausgang  „Message“ weiter.(String)
Folgende Eingänge stehen zur Verfügung:
- Enable(Bool, Hier muss der Datenpunkt vom X1 “Bereit” angegeben werden)
Folgende Parameter stehen zur Verfügung:
- Host (IP Adresse des Brokers, String)
- Port (Integer)
- Topic (String)
- Username (String)
- Password (String)
- Restart( Hier kann die Zeit in Stunden angegeben werden um die Verbindung erneut aufzubauen, 0=aus, Integer)
Folgende Ausgänge stehen zur Verfügung:
- Message(Ausgabe von der empfangenen Nachricht, String, QoS 0)
- Debug(Ausgabe von Fehlern, String)

Wenn man zb. Temperaturwerte empfangen möchte kann man am Ausgang des Baustein ein Typ Converter anhängen um anschließen mit den Werten auch rechnen zu können.
Dieser Baustein muss in der Simulation im GPA vorm beenden der Simulation am Eingang “Enable” mit einer 0 beendet werden.

###Changelog###
Version 1.0.50
- Baustein um Username, Password und Port erweitert

# Logikbaustein MQTT Publish Gira X1

Dieser Baustein sendet beim eintreffen eines Telegramm am Eingang „Message“ einen String an einen MQTT Broker mit dem angegebenen Topic.

Folgende Eingänge stehen zur Verfügung:
- Message (String)

Folgende Parameter stehen zur Verfügung:
- Host (IP Adresse des Brokers, String)
- Port (Integer)
- Topic (String)
- Username (String)
- Password (String)

Folgende Ausgänge stehen zur Verfügung:
- Debug (String)

###Changelog###
Version: 1.0.6
- Baustein um Username, Password und Port erweitert

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

# Logikbaustein Divera Status Rückmeldung

Beschreibung
Der Logikbaustein setzt einen User Status über die Divera API.
Es besteht die Möglichkeit einen zuvor definierten Status per Trigger zu setzen oder  eine ID an den Eingang „Status ID“  zu senden um somit flexibel einen Status setzen zu können.
 
Folgende Eingänge stehen zur Verfügung:
- Trigger (Bool)
- Status ID (Integer)

Folgende Parameter stehen zur Verfügung:
- Benutzer API Key (String)
 
Folgende Ausgänge stehen zur Verfügung
- Erfolg (Bool)
- Debug (String)

Trigger:
Trifft an dem Eingang eine 1 ein, sendet der Baustein den Status mit der ID die am Eingang „Status ID“

Status ID:
Trifft an dem Eingang Zahl ein die einem in Rivera angelegten Status gleicht wird dieser status gesendet.
Der Status wird ab „1“ aufwärts gezählt. Zb. 1 = Verfügbar, 2 = nicht Einsatzbereit etc…..

Benutzer API Key:
Hier müsst ihr euren eigenen Benutzer API Key angeben den ihr in euren Accounteinstellungen findet (Einstellungen/Debug)

Link zur Divera API Dokumentation:
https://api.divera247.com/?urls.primaryName=api%2Fv1#/E
Verwendetes Icon:
https://www.flaticon.com/de/kostenlose-icons/alarm Alarm Icons erstellt von Freepik – Flaticon

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


# Logikbaustein Pv Heizstab Steuerung Gira X1

Dieser Baustein Steuert PV geführt einen Heizstab für einen Warmwasserspeicher.

Folgende Eingänge stehen zu Verfügung:
- Freigabe (Bool)
- Aktuelle Leistung (Double, positiv=Überschuss / negativ=Bezug)
- Hausverbrauch (Double)
- Ist Temperatur (Double)

Folgende Parameter stehen zu Verfügung:
- Leistung invertieren (Bool)
- Nur PV (Bool)
- Soll Temperatur (Double)
- Leistung Stufe 1 (Integer, W oder KW)
- Leistung Stufe 2 (Integer, W oder KW)
- Leistung Stufe 3 (Integer, W oder KW)
- Toleranz Leistung (Integer, % von Stufe1)
- Umschaltpause(ms) (Integer)
- Regel Zeit(min) (Integer)
- Netzbezug erlauben (Bool)

Folgende Ausgänge stehen zu Verfügung:
- Stufe 1 (Bool)
- Stufe 2 (Bool)
- Stufe 3 (Bool)
- Debug (String)

Leistung Invertieren:
Je nach dem von wo aus die aktuelle Leistung betrachtet wird kann der Überschuss positiv oder Negativ sein.
Mit diesem Parameter könnt ich eure aktuelle Leistung anpassen bzw. invertieren.

Nur PV:
Dieser Parameter legt fest ob eure aktuelle Leistung am Haus Übergabepunkt gemessen wird oder ob ihr die aktuelle Leistung von der PV Anlage bekommt
Aus = aktuelle Leistung wird beim zuschalten einer Leistungsstufe um den Wert der Leistungsstufe reduziert 
Ein = Egal ob der Verbraucher ein oder aus geschaltet ist bleibt die aktuelle Leistung gleich da es der Wert eurer PV Anlage ist

Hausverbrauch:
Mit diesem Wert rechnet der Baustein künstlich einen Eigenverbrauch vom Haushalt hinzu wenn ihre Leistung am Eingang „Aktuelle Leistung“ den Hausverbrauch nicht enthält.
Dies ist zb der Fall wenn sie nur die aktuelle erzeugte Leistung von ihrem Wechselrichter bekommen.

Parameter:
Leistung Stufe 1-3:
Hier müssen die Werte für die jeweilige Leistungsstufe in W oder KWh eingegeben werden.
Diese Werte dienen als Berechnungsgrundlage für die Entscheidung ob geheizt wird oder nicht.

Toleranz Leistung:
Dieser Wert wirkt sich unterschiedlich aus je nach dem ob Netzbezug erlaubt ist oder nicht.
Die Toleranz wird in % von der Angegebenen Leistung am Parameter „Leistung Stufe 1“ berechnet

- Netzbezug nicht erlaubt
Die Toleranz wird auf den Wert zur Auswertung addiert, sodass wenn zb. Leistungsstufe 1 500W beträgt und die
Toleranz 100W dann wird erst bei > 600W eingeschaltet.

- Netzbezug erlauben
Die Toleranz wird von dem Wert zur Auswertung abgezogen, sodass wenn zb. Leistungsstufe 1 500W beträgt und die
Toleranz 100W dann wird bereits bei > 400W eingeschaltet.

Umschaltpause:
Dieser Wert definiert in ms die Umschaltzeit zwischen ein uns ausschalten der einzelne Stufen.

Regel Zeit:
Diese Zeit wird gewartet bevor der Baustein die nächsten Leistungsvergleich bzw. Schaltung durchführt um ein ständiges ein und Ausschalten zu verhindern.

Netzbezug erlauben:
Hiermit wird definiert ob der Netzbezug erlaub wird.
Wenn der Netzbezug erlaubt wird Schalten die Ausgänge abzüglich der eingestellten Toleranz ein und nicht erst wenn für die jeweilige Stufe genug Überschuss vorhanden ist.
Selbes passiert ebenfalls beim ausschalten in umgekehrter Reihenfolge.

SOLL Temperatur:
Wenn der IST kleiner als der SOLL dann ist der Baustein aktiv und versucht auf die Sollwert Vorgabe zu heizen.
WICHTIG: Der verwendete Warmwasserspeicher muss zwingend einen eigenen separaten Temperaturfühler haben der den Heizstab bei erreichen der vom Hersteller vorgegebenen Maximaltemperatur abschaltet.
Das Kann nicht mittels KNX Komponenten abgebildet werden!!!! 

Verwendetes Icon :https://www.flaticon.com/de/kostenlose-icons/photovoltaik Photovoltaik Icons erstellt von Khoirul Huda - Flaticon


###Changelog###
Version 1.0.3
- Parameter “nur PV“ hinzugefügt für den fall das ihr nur euren erzeugten Wert von der PV Anlage bekommt

