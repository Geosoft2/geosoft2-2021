@OTI2020
@Timo123456789

Quellen: https://geocompr.robinlovelace.net/spatial-cv.html#intro-cv

Why? When? How?
# 1. Was ist räumliche Kreuzvalidierung (Spatial Cross Validation)?
    * Idee: Datensatz wird wiederholt in einen Trainings- und einen Testsatz aufgeteilt
    * Trainingsdaten werden zur Anpassung an ein Modell verwendet, welches dann auf den Testsatz angewendet wird
    * Vergleich der vorhergesagten Werte mit den bekannten Antwortwerten (aus dem Testdatensatz) -> Bewertung möglich, ob Modell passt (Ziel ist es die Fähigkeit des Modells Werte (aus unabhängigen Daten) vorherzusagen zu erfassen)  

# Warum benutzen wir räumliche Kreuzvalidierung?
    * Toblers First Law of Geography besagt, dass Punkte, die nahe beieinander liegen, im Allgemeinen ähnlicher sind als Punkte, die weiter entfernt sind
    * -> Punkte sind statistisch gesehen nicht unabhängig, da Trainings- und Testpunkte in konventioneller Kreuzvalidierung (Cross Validation) oft zu nahe beieinander liegen
    * Trainingsbeobachtungen, die sich in der Nähe der Testbeobachtungen befinden können eine Art "Sneak Preview" entstehen lassen
    * -> Informationen, die dem Trainingsdatensatz eigentlich nicht zur Verfügung stehen sollten

# Wann kann diese Methode benutzt werden?
# Wie wird diese Validierungmethode angewendet?

