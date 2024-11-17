#Da ich alle meine Bausteine kostenlos zur Verfügung stelle und ich das auch gerne beibehalten möchte, würde ich mich über eine kleine Paypal Spende freuen. Vielen Dank für deine Unterstützung.


[Spende eine kleine Aufwandsentschädigung](https://www.paypal.com/donate/?hosted_button_id=SHU2PHYACRRMN)


Logic Nodes for the Gira X1

# Logikbaustein Alarmanlage

Diese Anleitung erklärt dir, wie du das Alarmsystem mit den verschiedenen Scharfschaltmodi (extern und intern), den Alarmzuständen und den Rücksetzungen bedienen kannst.
1. Modi des Alarmsystems
Du kannst das System in zwei Modi scharf schalten:
* Extern scharf: Sichert alle Türen, Fenster und Bewegungsmelder.
* Intern scharf: Sichert Türen und Fenster, jedoch ohne Bewegungsmelder.
2. Extern Scharfschalten
Voraussetzungen:
* Alle externen Sensoren (Türen, Fenster, Bewegungsmelder) müssen geschlossen sein.
* Der Alarmzustand muss inaktiv sein.
* Du musst die externe Scharfschaltung anfordern.
Ablauf:
* Das System startet einen Countdown, der durch den Parameter "verz. Extern Scharf (Sek.)" bestimmt wird.
* Nach Ablauf des Countdowns wird der Status auf "extern scharf" gesetzt, bis dahin kannst du das Gebäude verlassen da das öffnen einer Tür zu diesem Zeitpunkt noch nicht ausgewertet wird.
Deaktivierung:
* Wenn du die externe Scharfschaltung zurücksetzt, wird der Status auf "Bereit" gesetzt und der Scharfschaltvorgang gestoppt.
3. Intern Scharfschalten
Voraussetzungen:
* Alle Türen und Fenster müssen geschlossen sein.
* Der Alarmzustand muss inaktiv sein.
* Du musst die interne Scharfschaltung anfordern.
Ablauf:
* Das System startet einen Countdown, der durch den Parameter "verz. Intern Scharf (Sek.)" bestimmt wird.
* Nach Ablauf des Countdowns wird der Status auf "intern scharf" gesetzt.
Deaktivierung:
* Wenn du die interne Scharfschaltung zurücksetzt, wird der Status auf "Bereit" gesetzt.
4. Anlage in Bereitschaft setzen
Wenn weder die interne noch die externe Scharfschaltung aktiv ist und alle Sensoren korrekt geschlossen sind, setzt das System den Status auf "Bereit".
5. Alarm auslösen
Externer Alarm:
* Der externe Alarm wird ausgelöst, wenn das System extern scharf ist und ein Sensor (Türen, Fenster oder Bewegungsmelder) geöffnet wird.
* Die Sirene und das Blitzlicht werden aktiviert, und der Status wechselt auf "Einbruchalarm extern".
Interner Alarm:
* Der interne Alarm wird ausgelöst, wenn das System intern scharf ist und ein Sensor (Türen oder Fenster) geöffnet wird.
* Auch hier werden Sirene und Blitzlicht aktiviert, und der Status ändert sich auf "Einbruchalarm intern".
6. System zurücksetzen
Voraussetzungen:
* Der Reset-Button muss gedrückt werden.
* Der Alarmzustand muss aktiv sein.
* Es darf keine externe oder interne Scharfschaltung aktiv sein.
Ablauf:
* Durch das Drücken des Reset-Buttons deaktivierst du den Alarmzustand, setzt Sirene und Blitzlicht zurück und versetzt das System in den "Bereit"-Modus.
7. Fehlerdiagnose
Das System zeigt dir kontinuierlich den Zustand der externen und internen Scharfschaltung sowie den Status der Sensoren an. So kannst du den aktuellen Systemzustand immer überwachen.
8. Wichtige Parameter
* verz. Extern Scharf (Sek.): Verzögerung vor der Aktivierung des externen Scharfschaltens in Sekunden.
* verz. Intern Scharf (Sek.): Verzögerung vor der Aktivierung des internen Scharfschaltens in Sekunden.
* verz. Extern Alarm (Sek.): Verzögerung vor der Auslösung des externen Alarms in Sekunden.
* verz. Intern Alarm (Sek.): Verzögerung vor der Auslösung des internen Alarms in Sekunden.
9. Hinweise
* Achte darauf, dass alle Sensoren geschlossen sind, bevor du das System scharf schaltest.
* Im Alarmzustand musst du das System mit dem Reset-Button zurücksetzen, um die Alarmvorrichtungen zu deaktivieren.
* WICHTIG: Du musst die Eingänge die du verwendest als Initialwert von „1“ auf „0“ ändern damit die wenn noch kein Telegram eingetroffen ist der Eingang nicht pauschal auf true steht.



Beschreibung der Ein- und Ausgänge sowie Parameter des Alarmsystems

Eingänge
1. Extern Scharf (Bool)
    * Dieser Eingang aktiviert die externe Scharfschaltung des Systems. Wenn auf True gesetzt, sichert das System alle Türen, Fenster und Bewegungsmelder.
    * True: Extern scharf.
    * False: Extern unscharf.
2. Intern Scharf (Bool)
    * Dieser Eingang aktiviert die interne Scharfschaltung des Systems. Wenn auf True gesetzt, werden alle Türen und Fenster gesichert, die Bewegungsmelder bleiben jedoch deaktiviert.
    * True: Intern scharf.
    * False: Intern unscharf.
3. Reset (Bool)
    * Dieser Eingang setzt das Alarmsystem zurück. Wenn ein Alarm aktiv ist und der Eingang auf True gesetzt wird, deaktiviert er den Alarmzustand und setzt das System zurück in den "Bereit"-Modus.
    * True: System zurücksetzen.
    * False: Keine Aktion.
4. Tür 1 bis Tür 5 (Bool)
    * Diese Eingänge repräsentieren den Zustand der Türen. Wenn der Eingang einer Tür auf True gesetzt ist, bedeutet dies, dass die Tür geschlossen ist.
    * True: Tür geschlossen.
    * False: Tür offen.
5. Fenster 1 bis Fenster 10 (Bool)
    * Diese Eingänge repräsentieren den Zustand der Fenster. Ein Fenster ist geschlossen, wenn der entsprechende Eingang auf True gesetzt ist.
    * True: Fenster geschlossen.
    * False: Fenster offen.
6. Bewegung 1 bis Bewegung 10 (Bool)
    * Diese Eingänge überwachen die Bewegungsmelder. Wenn der Eingang eines Bewegungsmelders auf True gesetzt ist, zeigt dies, dass keine Bewegung detektiert wird.
    * True: Keine Bewegung erkannt.
    * False: Bewegung erkannt.
7. Technik 1 (Bool)
   * Dieser Eingang löst unabhängig von intern und extern Scharf aus.
     
Parameter
1. Verz. Extern Scharf (Sek.) (Integer)
    * Dieser Parameter bestimmt die Verzögerung in Sekunden, bevor die externe Scharfschaltung aktiviert wird. Nach der Anforderung zur externen Scharfschaltung wartet das System diese Zeitspanne ab, bevor es den Status auf "extern scharf" setzt.
2. Verz. Intern Scharf (Sek.) (Integer)
    * Dieser Parameter legt die Verzögerung in Sekunden fest, bevor die interne Scharfschaltung aktiviert wird. Nach der Anforderung zur internen Scharfschaltung wartet das System diese Zeitspanne, bevor es den Status auf "intern scharf" setzt.
3. Verz. Extern Alarm (Sek.) (Integer)
    * Dieser Parameter gibt an, wie lange das System warten soll, bevor der externe Alarm ausgelöst wird, nachdem ein Tür Sensor eine Störung (geöffnete Tür) meldet.
    * WICHTIG: Die Alarm Verzögerung wirkt sich nur auf die Tür Eingänge aus. Alle anderen Sensoren führen sofort zu einem Alarm!
4. Verz. Intern Alarm (Sek.) (Integer)
    * Hier wird die Verzögerung in Sekunden eingestellt, bevor der interne Alarm ausgelöst wird, nachdem ein Tür Sensor eine Störung (geöffnete Tür) meldet.
    * WICHTIG: Die Alarm Verzögerung wirkt sich nur auf die Tür Eingänge aus. Alle anderen Sensoren führen sofort zu einem Alarm!
5. Sensoren NC = 1 / NO = 0 (Bool)
    * Dieser Parameter bestimmt, ob die Sensoren als Normal geschlossen (NC) oder Normal offen (NO) konfiguriert sind.
    * True (1): Sensoren arbeiten im Normal-geschlossen-Modus (NC).
    * False (0): Sensoren arbeiten im Normal-offen-Modus (NO).
6. Sirene Timer (Sek.) (Integer)
    * Hier wird die Verzögerung in Sekunden eingestellt, bis die Sirene nach einem Alarm deaktiviert wird. Jede neue Melder Änderung aktiviert die Sirene und den Timer erneut.
      
Ausgänge
1. Sirene (Bool)
    * Dieser Ausgang wird aktiviert, wenn ein Alarm ausgelöst wird. Wenn auf True gesetzt, wird die Sirene aktiviert.
    * True: Sirene aktiv.
    * False: Sirene inaktiv.
2. Blitzlicht (Bool)
    * Dieser Ausgang wird ebenfalls bei einem Alarm aktiviert. Wenn auf True gesetzt, wird das Blitzlicht eingeschaltet.
    * True: Blitzlicht aktiv.
    * False: Blitzlicht inaktiv.
3. Status Extern Scharf (Bool)
    * Dieser Ausgang zeigt an, ob das System extern scharf ist. Wenn auf True gesetzt, ist die externe Scharfschaltung aktiv.
    * True: Extern scharf.
    * False: Extern unscharf.
4. Status Intern Scharf (Bool)
    * Dieser Ausgang zeigt an, ob das System intern scharf ist. Wenn auf True gesetzt, ist die interne Scharfschaltung aktiv.
    * True: Intern scharf.
    * False: Intern unscharf.
5. Betriebszustand (String)
    * Dieser Ausgang gibt den aktuellen Betriebszustand des Systems als Text aus, z.B. "Bereit", "extern scharf", "Einbruchalarm extern" usw.
6. Debug (String)
    * Dieser Ausgang gibt eine detaillierte Diagnose des Systems aus, wie z.B. den Status der Sensoren, ob die externe oder interne Scharfschaltung aktiv ist, und ob der Alarmzustand aktiviert ist.
  
# Changelog

	Version 1.2:
	- Ausschalt Timer für die Sirene hinzugefügt. Wenn die Zeit verstrichen ist schaltet die Sirene aus

	Version 1.1.0:
	- Anzahl für die Fensterkontakte von 10 auf 20 erhöht.
 	- Technik Alarm Eingang hinzugefügt.
 
	Version 1.0.1:
	- Wenn die Verzögerung aktiv ist und ein Sensor nicht geschlossen ist kommt ein Fehler. Vorher wurde trotzdem scharf geschaltet.


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
- User Filter (User ID zum Filtern ob der User beim Alarm adressiert ist, Integer)

Hinweis:
Der Intervall zum Triggern des Bausteins sollte nicht zu klein sein um des Gira X1 nicht zu überlasten.
Ein Intervall von 20-30 Sekunden ist sinnvoll.

###Changelog###

Version 1.1.0
User Filter hinzugefügt um zu überprüfen ob der User mit einer bestimmten ID adressiert ist.
Die Ausgänge werden ab jetzt nur bei einer Wertänderung neu beschrieben. Vorher wurden die Ausgänge mit jedem triggern des Bausteins neu beschrieben.

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

