# Containerization with Docker

Student: @AntoniaJost
Student: @TobiasBrand-GI

*To-Do:*
- [ ] add git tag handout-submussion-AntoniaJost -> push it to your fork
- [ ] send pull request

## Was ist Docker und warum nutzen wir es?
#### Was?
- Ermöglicht es, Software in Paketen, sog. **Containern** zu verpacken
- Diese Container sind isoliert voneinander & beinhalten deren eigene Software, Bibliotheken und Abhängigkeiten
- Dennoch kommunizieren die Container untereinander 
- Alle Container teilen sich die Dienste eines einzigen operating system kernel -> dadurch weniger Ressourcenverbrauch als bei virtueller Maschine

####  Warum?
- Anwendungen funktionieren geräteübergreifend, unabhängig vom Betriebssystem/anderen Installationen & sind leichter auszustauschen
- Vorteil der Standardisierung:
    - jeder Container hat präzisen Ausgangszustand
    - Container hat definierte Schnittstelle (Ports für Netzwerke & Volumes für Dateien und Verzeichnisse)
    - im Container selbst läuft Applikation mit allen benötigten Abhängigkeiten

## Begrifflichkeiten

#### Dockerfile
- Bauanleitung für Images 
- Textdatei
#### Image
- eingepackte Applikation
- enthält Dateisystem mit Anwendung & allen benötigten Abhängigkeiten
#### Registry
- zentrale Bibliothek für Images
- dient dazu, fertig gebaute Images zu speichern & später wieder daraus zu laden
#### Container
- laufende Applikation
- startet Kopie des Images, Prozesse im Container haben die Möglichkeit, während der Laufzeit Änderungen im Dateisystem vorzunehmen

## Ablauf
![Bild zum Ablauf von Docker](https://github.com/AntoniaJost/geosoft2-2021/blob/main/containerization-with-docker/Docker%20Ablauf.jpg)

entscheidende Ausdrücke:
- $ docker build –t name .
    - -t: tag -> vergibt Namen (name)
    - .: gibt Build-Kontext an -> da, wo Dockerfile liegt
- $ docker push
- $ docker pull
- $ docker run –d –p host:container
    - -d: detach: startet Container im Hintergrund
    - -p: publish: bindet Containerport an Hostport

## Dockerfile
```Dockerfile
# Gibt Image an, das als Basis verwendet werden soll (eigenes oder aus Registry)
FROM node:14

# Erstellt Verzeichnis
WORKDIR /usr/src/app

# Kopiert app code source vom lokalen Ordner in das docker /usr/src/app Arbeitsverzeichnis
COPY . .

# Dieser Befehl soll beim Bauen des Images ausgeführt werden
RUN npm install

# Bindet Container an bestimmten Port
EXPOSE 3000

# Befehl, der beim Start eines Containers aufgerufen werden soll
CMD node server.js
```

## docker-compose.yml
```Dockerfile
# hier Code Beispiel ergänzen
```

## Docker Hub

## Beispiele