## ALLUMER UNE LED

<pre>
Créer par Yannick HEUDE
04 Novembre 2024


Le programme permet simplement d'allumer une LED avec un Arduino Uno.

Dans la mesure où la LED ne va pas bouger du port sur lequel elle est connectée,
elle est déclarée dans une variable constante.

Outils:
    - x1 Arduino Uno
    - x1 Breadboard
    - x1 LED
    - x1 Resistance de 220 ohm
</pre>

<br>

```c
// Affectation de la LED sur le port digital 4 du board Arduino
const int LED = 4;


void setup()
{
  // Initialisation de la LED en sortie
  pinMode(LED, OUTPUT);
}


void loop()
{
  // Allumage de la LED = HIGH
  digitalWrite(LED, HIGH);
}
```

---

<div align="center">
    <img
        src="https://github.com/AyckinnLisa/arduino/blob/main/LED/pics/01.md"
        style="width:75%">
</div>
