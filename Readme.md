Bemerkung:
Da LoRaWAN leider nicht wie geplant zur Verfügung stand - bzw. der Verbindungsaufbau mit vielen Problemen behaftet war -, haben wir uns im Team stärker auf die Umsetzung einer Parkplatz-Zustandserkennung fokussiert. 

Wichtig war uns dabei, auch ohne ein neuronales Netz ein zuverlässiges Ergebnis zu erzielen und dem Sensor möglichst lange Sleep-Zeiten zu gewähren. Der Prototyp ist in Java implementiert und verwendet noch viele Operationen auf “BufferedImages”, kann aber problemlos auf primitive Operationen und die Sprache C portiert werden.

Das System würde im Live-Betrieb Kamera-Standbilder in vom User festgelegten Intervallen aufnehmen und von ihm festgelegte Parkflächen mit verschiedenen Filtern auf den Zustand “frei” oder “belegt” untersuchen. Dabei kann unsere Lösung nicht nur eine einzelne Parkfläche, sondern einen kompletten Parkplatz überwachen.

Die Übermittlung der Daten würde dann als ein Bit pro Parkfläche erfolgen (1 = belegt, 0 = frei) und damit den geringstmöglichen Traffic bei gleichzeitiger Schärfe auf einzelne Parkflächen generieren.

Leider konnten wir im vorgegebenen Zeitraum nicht mehr den Clusterungs-Algorithmus fertig implementieren, auch wenn dieser von uns schon konzeptioniert und teilweise implementiert wurde. Daher zeigt das System momentan die “Rohdaten” vor dem letzten entscheidenden Schritt; der Klassifizierung in “frei” oder “belegt” der Flächen.

UserManual:
Dashboard:
Verwendung
endgültige Darstellung der Stadien der Parkplätze auf Basis von erhaltenen Daten
hier ist nur die Route 127.0.0.1:8000/ gültig

Laravel-Projekt öffnen und folgende Befehle im Projektverzeichnis ausführen:
composer install
npm install
php artisan serve





Click-Seite:
Verwendung
definition der einzelnen Parkflächen

Punktsetzung im Bild für ein Polygon, um die Flächen zu bestimmen. Dafür muss die Datei main.c ausgeführt werden.

Algorithmus:
Verwendung
Verarbeitung der Kamerabilder, um freie und besetzt Parkflächen zu detektieren.

Startklasse (Main) heißt ParkingspaceSurveillance
Kantendetektion und Flächenfilterung, um anhand dessen Stadien pro Fläche zu ermitteln
Programm ausführen und per Dateiexplorer das zu untersuchende Bild/Maske auswählen (im Projekt liegen zwei Bilder und zwei Masken bereit)
Anschließend Speicherort für das gefilterte Bild auswählen
	



