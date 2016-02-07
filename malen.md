# Malprogramm

Hier simulieren wir einen Kalligrafie-Pinsel, um "Tinte" zu malen.

```java
// Ein "float" ist eine Fließkommazahl
float breite = 0.0;

void setup() {
  size(500, 500);

  /* Wir wollen nicht jeden Frame das ganze Fenster übermalen,
   * sondern nur einmalig zum Start. Daher bestimmen wir das
   * hier in `setup` und nicht in `draw`. */
  background(255, 255, 255); // weiße Leinwand
  fill(0, 0, 0); // schwarze Tinte
}

void draw() {
  // Einen Kreis an die Mausposition malen
  ellipse(mouseX, mouseY, breite, breite);

  /* Wird eine Maustaste gedrückt, malen wir einen Tintenklecks.
   * Wir addieren jeden Frame 0.5 auf die Tinte, sodass der Klecks immer
   * dicker wird, je länger man malt. */
  if (mousePressed) {
    breite = breite + 0.5;
  } else {
    // Die Maustaste wurde losgelassen: keine Tinte mehr malen.
    breite = 0.0;
  }
}
```

Probiert es direkt aus. Per Mausklick kann man malen. Je länger man gedrückt hält, desto dicker
wird der Strich.

## Änderungen

* Experimentiert mit der Pinseldicke (statt `0.5` eine andere Zahl auf die `breite` addieren).
* Bewegt den Aufruf von `background()` aus `setup` heraus nach `draw`. Was passiert? Und wieso?
* Malt mit einer anderen Farbe als Schwarz.

Das alleine macht noch nicht so viel her...

# zwei Pinsel gleichzeitig

Wie wäre es mit einem weiteren Pinsel, der spiegelverkehrt malt? Das klingt
komplizierter als es ist:

```java
  ellipse(width - mouseX, mouseY, breite, breite);
```


