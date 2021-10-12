# STAC: spatiotemporal asset catalog
Bearbeitet von: [@KatharinaGI](https://github.com/KatharinaGI),

Informationsquelle: https://stacspec.org/

## Ausgangspunkt

- Es gibt heutzutage eine riesige Menge an Geodaten, die unser Verständis der Welt erheblich verbessern und unsere Entscheidungen erleichtern könnten
- Die meisten dieser Daten sind jedoch unzugänglich, da sie in unzähligen verschiedenen Formaten vorliegen und es keine einheitliche Methode gibt, um relevante Informationen über einen Ort im Laufe der Zeit zu finden
- Wenn ein Nutzer nach allen Bildern in seinem Interessengebiet und -zeitraum suchen möchte, kann er nicht nur eine Suche durchführen - er muss verschiedene Tools verwenden und sich mit APIs verbinden, die zwar ähnlich, aber alle leicht unterschiedlich sind. 
=> **STAC!**

## Was ist STAC?

#### Die STAC-Spezifikation lebt zur einfachen Zugänglichkeit als leicht lesbare Markdown-Seiten auf Github, für mehr Informationen klicke also hier: https://github.com/radiantearth/stac-spec !

- **Der SpatioTemporal Asset Catalog (STAC)** ist eine offene Spezifikation, die aus der Zusammenarbeit verschiedener Organisationen entstanden ist, um den Zugang zu sowie die Bereitstellung von Informationen über unseren Planeten zu verbessern 

<img src="https://github.com/KatharinaGI/geosoft2-2021/blob/main/stac-spatiotemporal-asset-catalog/Screenshot_Supporters.PNG" alt="drawing" width="380" height="200"/> *(Bildquelle: https://stacspec.org/)*

- Das Ziel von STAC: über eine **gemeinsame Sprache** zur Beschreibung von Geodaten einen globalen Index für alle Bilddaten (Satelliten-, Luft-, Drohnenbilder usw.), abgeleitete Datenprodukte und alternative Geodatenerfassungen (LiDAR, SAR, Full Motion Video, Hyperspektralaufnahmen usw.) zu erstellen. 
   * **JSON-Format** als kleinsten gemeinsamen Nenner, um alle relevanten Daten über die Erde zu umhüllen. 
- STAC konzentriert sich auf einen leicht umsetzbaren Standard, mit dem alle Anbieter ihre **raum-zeitlichen Informationen** („spatiotemporal assets“) auf dauerhafte und zuverlässige Weise als SpatioTemporal Asset Catalogs (STAC) offenlegen können
  * kein neuer Code benötigt, wenn neuer Datensatz/API veröffentlicht wird
  *	Die meisten Geodatenkataloge setzen voraus, dass der Datenanbieter Server und Datenbanken unterhält, um die Suche zu ermöglichen -> bei riesigen Datenmengen Herausforderung 
-	STAC zielt darauf ab, nächste Generation von Geodaten-Suchmaschinen zu ermöglichen und gleichzeitig bewährte Web-Praktiken zu unterstützen, damit Geodaten in herkömmlichen Suchmaschinen leichter auffindbar sind.

## Warum STAC? “The Advantages of using STAC’s” 

#### *STAC ist für Datenanbieter*

- STAC ist ein standardisierter Weg, um Bestände von räumlichen und zeitlichen Daten für den externen Zugriff (Suchmaschinen, wachsendes System von Tools) zugänglich zu machen

#### *STAC ist für Entwickler*

- Um Infrastruktur aufzubauen, um Sammlungen von Geodaten oder Bildprodukten zu hosten, aufzunehmen oder zu verwalten, ist das Kern-JSON Minimum, das für die Interaktion mit jeder Geodatensammlung erforderlich ist. 
  * JSON-Kern ist vollständig **erweiterbar**: Hinzufügen von Attributen möglich, um Anwendungsfall oder Datensatz besser zu erfassen. 
  * Darüber hinaus standardisiert STAC Metadatenfelder, Namenskonventionen, Abfragesprache und Katalogstruktur. 
-	Als Entwickler haben Sie zwei Möglichkeiten, STAC zu implementieren: 

Statischer Stac| STAC-API
------------ | -------------
Ceinfach zu erstellen und kann leicht von verschiedenen Tools aufgenommen werden, die die STAC-API generieren | ermöglicht die Abfrage von Daten in einer Standardsprache und die Rückgabe einer Teilmenge des Katalogs

  * Beide Arten unterstützen die Erstellung einer Katalog-Webseite mit STAC-kompatiblen Artikeln: kann interaktive Landing Page für die einzelnen Daten sein und lässt sich leicht so konfigurieren, dass sie von einer **Suchmaschine gecrawlt** werden kann. 
- Von Entwicklern für Entwickler entwickelt, sodass die Implementierung in der Regel einfach ist, und es ein wachsendes System von Tools und Bibliotheken gibt, die verwendet werden können.

#### *STAC ist für Datennutzer*

- Nutzer von räumlich-zeitlichen Datensätzen müssen oft eigene Pipelines für die Aufnahme von Sammlungen in ihr System erstellen, Sammlungen werden mit unterschiedlich detaillierten Metadaten und über verschiedene Bereitstellungsmechanismen geliefert

=> die **Notwendigkeit maßgeschneiderter Arbeitsabläufe (Aufwand) beseitigen**

## Philosophie

1. #### *Kleiner, flexibler Kern:*
  * STAC soll einfach zu implementieren und an bestehende Implementierungen anpassbar sein. 
  * Die STAC-Validierung ermöglicht maximale Flexibilität, indem sie einfach das Vorhandensein von Schlüsselfeldern prüft und es ermöglicht, dass andere implementierungsspezifische Felder von STAC-Clients nach Bedarf genutzt werden können. 
  * Alle Teile von STAC sollten kleinteilig und lose gekoppelt sein, um eine agile Entwicklung zu ermöglichen.
2. #### *Entwicklung von Best Practices und Erweiterungen durch reale Nutzung:*
  * Während sich der STAC-Kern auf eine minimale Spezifikation konzentriert, werden kontinuierlich optionale Erweiterungen hinzugefügt, um die Interoperabilität und Nutzbarkeit der über STAC bereitgestellten Daten zu erhöhen. 
3. #### *Starke Verwendung von Links:*
* Links zwischen verschiedenen Elementen ermöglichen die Modellierung komplexer Beziehungen. 
4. #### *HTML-Darstellungen*
  * Wichtig: Berücksichtigung des maschinenlesbaren JSON als auch des für den Menschen nutzbare HTML 
  * STAC-Items sind so konzipiert, dass sie leicht in HTML umgewandelt werden können, das von Menschen durchstöbert und von Suchmaschinen gecrawlt werden kann -> Integration in das Web möglich 

## -> Zukunftsvisionen von STAC

- Die Verfolgung der Herkunft bis zur Quelle ist ein Traum der meisten Nutzer von Geodaten: die Verlagerung in die Cloud bietet die Möglichkeit, diesen Traum zu verwirklichen. -	Während jeder mit Google und der Möglichkeit, jede Webseite auf der Welt zu durchsuchen, vertraut ist, ist dies für Geodaten noch nicht möglich.
  * Die Vision des STAC für die globale Suche ist nicht, Suchanfragen an jeden STAC-Server zu senden, sondern einfach jedes Element "web-crawlable" zu machen.
  * Herkunfts-Links zwischen Katalogen tragen zur Auffindbarkeit bei, indem sie das Ranking einer Seite in den Algorithmen der Suchmaschinen erhöhen. Stabiles HTML bedeutet mehr Links zu diesen Seiten, was sie in den Suchergebnissen weiter nach oben bringt
- Förderung der Konversation über Geostandards und Prozesse, Voranbringen des Standards im Bereich Geodaten als Ganzes -> Zusammenarbeit






