# STAC: spatiotemporal asset catalog
Bearbeitet von: [@KatharinaGI](https://github.com/KatharinaGI),

Informationsquelle: https://stacspec.org/

## Ausgangspunkt

- Es gibt heutzutage eine riesige Menge an Geodaten, die unser Verständis der Welt erheblich      verbessern und unsere Entscheidungen erleichtern könnten
- Die meisten dieser Daten sind jedoch unzugänglich, da sie in unzähligen verschiedenen Formaten vorliegen und es keine einheitliche Methode gibt, um relevante Informationen über einen Ort im Laufe der Zeit zu finden
- Wenn ein Nutzer nach allen Bildern in seinem Interessengebiet und -zeitraum suchen möchte, kann er nicht nur eine Suche durchführen - er muss verschiedene Tools verwenden und sich mit APIs verbinden, die zwar ähnlich, aber alle leicht unterschiedlich sind. 
=> STAC!

## Was ist STAC?

#### Die STAC-Spezifikation lebt zur einfachen Zugänglichkeit als leicht lesbare Markdown-Seiten auf Github, für mehr Informationen klicke also hier: https://github.com/radiantearth/stac-spec !

- Der SpatioTemporal Asset Catalog (STAC) ist eine offene Spezifikation, die aus der Zusammenarbeit verschiedener Organisationen entstanden ist, um den Zugang zu sowie die Bereitstellung von Informationen über unseren Planeten zu verbessern 

<img src="https://github.com/KatharinaGI/geosoft2-2021/blob/main/stac-spatiotemporal-asset-catalog/Screenshot_Supporters.PNG" alt="drawing" width="350" height="160"/> *Bildquelle: https://stacspec.org/*

- Das Ziel von STAC: über eine gemeinsame Sprache zur Beschreibung von Geodaten einen globalen Index für alle Bilddaten (Satelliten-, Luft-, Drohnenbilder usw.), abgeleitete Datenprodukte und alternative Geodatenerfassungen (LiDAR, SAR, Full Motion Video, Hyperspektralaufnahmen usw.) zu erstellen. 
   * JSON-Format als kleinsten gemeinsamen Nenner, um alle relevanten Daten über die Erde zu umhüllen. 
- STAC konzentriert sich auf einen leicht umsetzbaren Standard, mit dem alle Anbieter ihre raum-zeitlichen Informationen („spatiotemporal assets“) auf dauerhafte und zuverlässige Weise als SpatioTemporal Asset Catalogs (STAC) offenlegen können
  * kein neuer Code benötigt, wenn neuer Datensatz/API veröffentlicht wird
  *	Die meisten Geodatenkataloge setzen voraus, dass der Datenanbieter Server und Datenbanken unterhält, um die Suche zu ermöglichen -> bei riesigen Datenmengen Herausforderung 
-	STAC zielt darauf ab, nächste Generation von Geodaten-Suchmaschinen zu ermöglichen und gleichzeitig bewährte Web-Praktiken zu unterstützen, damit Geodaten in herkömmlichen Suchmaschinen leichter auffindbar sind.



