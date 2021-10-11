# Containerization with Docker

Student: [@AntoniaJost](https://github.com/AntoniaJost),

Student: [@TobiasBrand-GI](https://github.com/TobiasBrand-GI)

git tag <handout-submission-TobiasBrand-AntoniaJost>

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
#### Volumes
- Daten dauerhaft/ Container-unabhängig speichern
- Datenaustausch zwischen Containern möglich

## Ablauf
![Bild zum Ablauf von Docker](https://github.com/AntoniaJost/geosoft2-2021/blob/main/containerization-with-docker/Docker%20Ablauf.jpg)

# entscheidende Ausdrücke:
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
# Version der genutzten Syntax
version: "3"

# Container / Parts der App
services:

  app:
    # Container Name
    container_name: stadtfuehrer
    # Path zum lokalen Dockerfile, um Image erstellen zu lassen
    build: .
    # Image, dass vom Container genutzt wird
    image: tobiasbrand/stadtfuehrer
    # Genutzter Port des Containers
    ports:
      - "3000:3000"
    # Abhängigkeiten von anderem Container
    depends_on:
      - mongodbservice

  mongodbservice:
    # Container "mongo"
    container_name: mongo
    # Image von Docker Hub
    image: mongo
    ports:
      - "27017:27017"
```

- docker-compose up reicht aus, um ganze App zu starten
- Workflow:
    - Dockerfile für jedes neue Image
    - Rest von Docker Hub einfügen
    - App mit Docker Compose starten

## Docker Hub

- Offizielle Plattform, um Images zu suchen und teilen
- Steuerbarer Access und Push/ Pull Möglichkeiten
- Weitere, fortgeschrittene Funktionen (Builds, Webhooks)
- Ein CLI-Tool und API existieren

## Beispiele

- Multi-Container-Apps sind meist die beste Wahl
- 1 Container = 1 Aufgabe (z.B. Frontend, Backend, Datenbank)
