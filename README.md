# mBot_KI

## Idee
Der mBot ist kein wirkliches selbstfahrendes Auto. Er kann Linien nur Folgen,
wenn sie durchgehend und direkt unter dem Fahrzeug sind.
Auch das er Hindernissen ausweichen kann ist eher trivial gelöst.
Er fährt erst gegen das Objekt und korrigiert dann erst. Die Idee der Erweiterung
ist das der mBot schon im Vorhinein Hindernisse erkennen kann
und diesen dann ausweicht. Auch die Linefollowing Funktion
soll Implemtiert werden. Der Input für beide Funktionen kommt von einer Kamera.

## Code
5.2.1 Erklärung Idee:
Das Ganze soll von einen Künstlichen Neuronalen Netzwerk gesteuert werden.
Genauer gesagt von einen CNN welches Trainingsdaten nimmt diese evaluiert Details findet,
die in jedem Bild vorhanden sind und diese in neuen Bildern findet. Das Ganze wird auf der Basis
von Keras Tensorflow gebaut.

## Input Algorithmus
Da die Bilder in Unterschiedlichen Größen kommen (Verschiedene Datasets),
müssen wir einen Algorithmus Implementieren der alle Bilder zu einer Größe
Hinunterschneidet. Wenn man den Input nicht auf eine Größe Hinunterschneidet,
kann das CNN diese nicht übernehmen (Interne Fehler in der Funktion). 

## Externes Training-Set:

## Input Algorithmus Teil.1
Die Bilder werden geladen und auf eine gewisse Größe (px) geschnitten.
Danach werden die Bilder mit den neuen zugeschnittenen Bildern überschrieben
und ein Blocked Array (X=Bilder, Y=Beschriftung) und ein Free Array mit der
Länge der beiden erstellt.

## Input Algorithmus Teil.2
Die zugeschnittenen Bilder werden eingelesen und in Farbwerte umgewandelt.
Danach werden sie in den zuvor erstellten Arrays gespeichert.
Hinter den ‚#‘ findet man Test Funktionen die das Array oder die Bilder
mit ihrer Überschrift ausgeben.
Zuletzt wird noch die Anzahl an Blocked und Free Images angezeigt.

## Training-Code
Der Haupt-Code, hier werden alle Bilder verarbeitet.
Im model.fit Teil wird das Neural Network mit 32 Bilder pro Input
auf 200 Epochen trainiert. Der erste große Teil sind Layers.
Diese helfen die accuracy zu steigern. Am Ende wird das ganze nochmal
Compiled und zusammengefasst.

## Evaluation, Testen, Speichern
Zuletzt wird das Model nochmal Compiled und Evaluiert. Dann kann man dem
Neural Network ein Bild geben welches es dann Predicted (Free/Blocked).
Am Ende speichert man das System als HDF5 gespeichert. 

# Hardware
##CPU
Durch die geringe „CPU-Leistung“ des Arduinos müsste man auf einen
Raspberry PI 4 umsteigen. Die Implementierung der Live Kamera wäre
dadurch auch viel einfacher.

## Kamera
Die PI-Cam wurde ausgesucht für das Live Video.
Sie kann jedoch auch durch die Wireless Funktion sehr gut
zum Trainingsdaten sammeln eingesetzt werden.
Cam und Controll Code:
