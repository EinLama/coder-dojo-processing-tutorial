# Processing Tutorial

Eine kleine Einführung in Processing. Kann direkt mit den CoderDojo-Kids durchgearbeitet werden.

# Processing herunterladen

Processing findet ihr auf https://processing.org/download/ - eine Spende ist optional möglich. Einfach herunterladen und den Ordner irgendwo hinlegen. Eine Installation ist nicht erforderlich.

# Was ist Processing?

Diese Erklärung ist vermutlich nicht akkurat... sollte aber für unsere Zwecke reichen: Processing ist eine IDE und ein Wrapper um Java/OpenGL. Man schreibt echten Java-Code, unterliegt aber weniger Einschränkungen:

* man braucht keine Klasse um alles herum, sondern kann C-style Code schreiben (imperativ).
* kein public static void main
* vorgefertige grafische Funktionen
* auf Wunsch kann man alle Java-std-Klassen nutzen (ArrayList, usw.)
* eigene Klassen können auch definiert werden

# Processing öffnen

Wenn man die Binary ausführt, sieht man einen Editor. Per PLAY-button (oder ^R, bzw. R) kann ein Programm gestartet werden, nachdem es eingetippt wurde. Mit Datei > Exportieren... kann eine Binary gespeichert werden, auf Wunsch kann sogar Java mit in die Binary gebundelt werden. So kann man ein Projekt einfach Freunden zur Verfügung stellen - sie müssen dann noch nichtmal Java installieren.

![Ansicht der IDE](images/ide.jpg)

# Beispielprogramme

Ich fange gerne mit diesen Icebreakern an:

```java
// wird einmal beim Programmstart aufgerufen
void setup() {
  size(800, 600); // Fenster in der Auflösung 800x600 zeichnen
}

// wird einmal pro Frame aufgerufen, also etwa 60 mal pro Sekunde
void draw() {
  background(0, 0, 0); // schwarzen Hintergrund malen
  
  // Strichfarbe setzen, gilt für alles, was ab jetzt gemalt wird:
  stroke(255, 255, 255);
  
  // Linie malen. Die Argumente sind: startX, startY, endX, endY
  line(0, 300, 800, 300);
}
```

Da `draw()` immer wieder aufgerufen wird, können wir einfach Bewegungen erzeugen. So lassen wir die Linie wandern:

```java
float lineY;
float lineSpeed = 3.0;

void setup() {
  size(800, 600);
  
  /*
   * Zum Start mittig auf die Y-Achse platzieren.
   * `height` ist die Fenstergröße. Erst nach Aufruf von `size` verfügbar.
   */
  lineY = height / 2;
}

void draw() {
  background(0, 0, 0);

  stroke(255, 255, 255);
  line(0, lineY, 800, lineY);
  
  // Wichtig: hier wird die Bewegung umgesetzt!
  lineY = lineY + lineSpeed;
  
  // Wir wollen nicht, dass die Linie das Fenster verlässt:
  if (lineY >= height) { // Bildschirm unten verlassen?
    lineSpeed = -lineSpeed;  // Beschleunigung umkehren
  }
  
  if (lineY <= 0) { // Bildschirm oben verlassen?
    lineSpeed = -lineSpeed; // Beschleunigung umkehren
  }
}
```
