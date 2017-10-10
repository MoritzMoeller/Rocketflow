![Screenshot](https://raw.githubusercontent.com/MoritzMoeller/Rocketflow/master/rocketflow.png "Logo")
RocketFlow
================

RocketFlow ist eine Software, die im Zuge der Veranstaltung Sofwaretechnik an der Hochschule RheinMain entwickelt wurde.
Umgesetzt wurde das Projekt in einem agilen Team mittels Scrum. Die Anforderung an die Software war es, Firmen zu ermöglichen strukturierte Arbeitsabläufe festzulegen, um so inviduelle Arbeitsschritte erfassen zu können.
Das Endergebnis ist der WorkflowManager RocketFlow. 

Technologie:
* Der Server ist in Java implementiert
* Mittels PostgreSQL und MyBatis wurde die Datenbankanbindung realisiert
* Der Client ist in C# implementiert
* Die Client-Server Kommunikation wird über REST Schnittstellen bereitgestellt
* Die Parallelbearbeitung ist mittels eines Message Bus realisiert
* Build-System wurde Maven verwendet
* Unit-Tests mittels JUnit

Features:
* Workflows mittels Workflow-Manager erstellen und geziehlt Arbeitsschritte festlegen
* Verzweigungen (Forks), Schleifen und Bedingungen zum fortschreiten im Workflow sind möglich
* Parallele Bearbeitung des Workflows durch Messagebus mit Live-Aktualisierung
* Ausführen von Python-Scripten innerhalb eines Workflows (zB. Versand einer Mail bei erfolgreicher Abarbeitung)
* Mittels Workflow-Client können Mitarbeiter Tasks für ihre Workflows erstellen und bearbeiten 


Anleitung
================
Server:
* Mit einem Rechtsklick auf das Projekt den Punkt „Configure“ und darunter den Punkt
„Convert to Maven Project auswählen“
* Einmal „Maven-Test“ ausführen. (Unter Run > Run As > Maven test)
* Konfiguration:
* Datenbank: Im Paket src/main/resources kann die gewünschte Datenbank konfiguriert werden.
* Falls gewünscht kann der Port der REST-Schnittstelle in der Datei app.config konfiguriert werden. Diese befindet sich auch unter src/main/resources

Client:
* im Fileviewer die Datei „Pikachu.sln“ markieren und auf „Open“ klicken.
* Das darauf folgende Fenster mit „OK“ bestätigen.
* Falls eine Sicherheitswarnung für vertrauenswürdige Dateien auftaucht, diese bitte enthaken
und mit „OK“ bestätigen.
* Das Projekt „Pikachu“ mit Rechtsklick als „Startprojekt festlegen“.
* Konfiguration:
* Im Projektordner „Pikachu“ befindet sich die Datei „App.config“, in Ihr kann die Serververbindung konfiguriert werden.
* Für Server auf dem lokalen Host bitte „localhost“ als IP eintragen
* z.B.:
<appSettings>
<add key="RestServerURL" value="http://192.168.178.24:8081" /> <add key="MessageServerURL" value="tcp://192.168.178.24:9999" />
</appSettings>

Auslieferungszustand des Programms:
* Sobald der Server gestartet wurde kann man in der Serverkonsole den Befehl „db create“ (ohne Anführunszeichen) eingeben. Dies führt dazu, dass alle benötigten Tabellen, Views und ein default Admin zum initialen Einloggen ins Programm, angelegt werden.
* Benutzername: admin01
* Passwort: testpw
* Auf Wunsch kann noch der Befehl „db testdata“ (ohne Anführunszeichen) eingegeben
werden. Dies führt dazu, dass ein Testworkflow und dafür benötigte Benutzer und Gruppen angelegt werden.
* Benutzernamen: user01, user02, user03
* Passwort: testpw
* Info: Dieser vorgefertigte Workflow muss zunächst noch vom admin freigegeben werden, bevor ein Job dafür gestartet werden kann.


Screenshots
================
Workflows erstellen und editieren
![Screenshot](https://raw.githubusercontent.com/MoritzMoeller/Rocketflow/master/screen01.png "Workflow Editor")

Workflow Client zum abarbeiten der Tasks
![Screenshot](https://raw.githubusercontent.com/MoritzMoeller/Rocketflow/master/screen02.png "Workflow Client")
