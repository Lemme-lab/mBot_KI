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
![Screenshot_64](https://user-images.githubusercontent.com/71924682/149638247-de375810-bac8-494e-96c2-d392e038d9a5.png)

## Input Algorithmus
Da die Bilder in Unterschiedlichen Größen kommen (Verschiedene Datasets),
müssen wir einen Algorithmus Implementieren der alle Bilder zu einer Größe
Hinunterschneidet. Wenn man den Input nicht auf eine Größe Hinunterschneidet,
kann das CNN diese nicht übernehmen (Interne Fehler in der Funktion). 

## Externes Training-Set:
![Screenshot_65](https://user-images.githubusercontent.com/71924682/149638250-584213ff-eb6c-4956-98df-b415dfdb449d.png)

## Input Algorithmus Teil.1
Die Bilder werden geladen und auf eine gewisse Größe (px) geschnitten.
Danach werden die Bilder mit den neuen zugeschnittenen Bildern überschrieben
und ein Blocked Array (X=Bilder, Y=Beschriftung) und ein Free Array mit der
Länge der beiden erstellt.
![Screenshot_66](https://user-images.githubusercontent.com/71924682/149638253-aa1783de-8260-46d4-ba24-0539f1fd0f11.png)

## Input Algorithmus Teil.2
Die zugeschnittenen Bilder werden eingelesen und in Farbwerte umgewandelt.
Danach werden sie in den zuvor erstellten Arrays gespeichert.
Hinter den ‚#‘ findet man Test Funktionen die das Array oder die Bilder
mit ihrer Überschrift ausgeben.
Zuletzt wird noch die Anzahl an Blocked und Free Images angezeigt.
![Screenshot_67](https://user-images.githubusercontent.com/71924682/149638254-8753b760-a47a-4070-b63a-7bd41ab8c1a1.png)
![Screenshot_68](https://user-images.githubusercontent.com/71924682/149638259-cb0ec1ed-81d8-4afb-95ec-88b9fbf8f0b4.png)
![Screenshot_69](https://user-images.githubusercontent.com/71924682/149638260-7d43f91f-95f8-4c03-9e97-14e88fb56611.png)

## Training-Code
Der Haupt-Code, hier werden alle Bilder verarbeitet.
Im model.fit Teil wird das Neural Network mit 32 Bilder pro Input
auf 200 Epochen trainiert. Der erste große Teil sind Layers.
Diese helfen die accuracy zu steigern. Am Ende wird das ganze nochmal
Compiled und zusammengefasst.
![Screenshot_70](https://user-images.githubusercontent.com/71924682/149638267-0a2688cd-5baa-4d5d-b67e-2168f61dcfab.png)
![Screenshot_71](https://user-images.githubusercontent.com/71924682/149638270-4901f15b-15d7-46cf-be87-5a56c1064cc6.png)
![Screenshot_72](https://user-images.githubusercontent.com/71924682/149638273-4759fd6a-1561-4f07-a6b3-eae1dc0596f8.png)

## Evaluation, Testen, Speichern
Zuletzt wird das Model nochmal Compiled und Evaluiert. Dann kann man dem
Neural Network ein Bild geben welches es dann Predicted (Free/Blocked).
Am Ende speichert man das System als HDF5 gespeichert. 
![Screenshot_74](https://user-images.githubusercontent.com/71924682/149638276-ae15cd99-f23b-43d7-b2b2-dca94fabef1f.png)

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

![Screenshot_75](https://user-images.githubusercontent.com/71924682/149638279-bad68030-53b3-40f5-87cc-b14e7541c8d3.png)
