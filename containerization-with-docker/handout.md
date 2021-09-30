# Containerization with Docker

Student: @AntoniaJost

*To-Do:*
- [ ] add git tag handout-submussion-AntoniaJost -> push it to your fork
- [ ] send pull request

## Was ist Docker und warum nutzen wir es?
- Ermöglicht es, Software in Paketen, sog. **Containern** zu verpacken
- Diese Container sind isoliert voneinander & beinhalten deren eigene Software, Bibliotheken und Abhängigkeiten
- Dennoch kommunizieren die Container untereinander 
- Alle Container teilen sich die Dienste eines einzigen operating system kernel -> dadurch weniger Ressourcenverbrauch als bei virtueller Maschine

- Anwendungen funktionieren geräteübergreifend, unabhängig vom Betriebssystem/anderen Installationen & sind leichter auszustauschen
- Vorteil der Standardisierung:
    - jeder Container hat präzisen Ausgangszustand
    - Container hat definierte Schnittstelle (Ports für Netzwerke & Volumes für Dateien und Verzeichnisse)
    - im Container selbst läuft Applikation mit allen benötigten Abhängigkeiten

## Begrifflichkeiten

#### Dockerfile
Bauanleitung für Images, Textdatei
#### Image
eingepackte Applikation