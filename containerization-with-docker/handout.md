# Containerization with Docker

Student: @AntoniaJost

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
- $ docker push
- $ docker pull
- $ docker run –d –p host:container

## Dockerfile
```Dockerfile
FROM node:14

# Create app directory
WORKDIR /usr/src/app

# Copy app code source from our local folder into the docker /usr/src/app working directory
COPY . .

# Install app dependencies
RUN npm install

# Expose app on a given port
EXPOSE 3000

# Start app
CMD node server.js
```