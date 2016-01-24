# Linie in Bewegung

Hier malen wir ein Fenster, in dem sich eine Linie hin- und herbewegt.

## Fenster mit Linie

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

## Die Linie bewegt sich

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
