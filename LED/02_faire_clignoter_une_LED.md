## FAIRE CLIGNOTER UNE LED

<pre>
Créé par Yannick HEUDE
04 Novembre 2024


Le programme permet de faire clignoter une LED toutes les 200 millisecondes (0.2 secondes).

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
// Association de la LED sur le port digital 4
#define LED  4


void setup()
{
  // Initialisation de la LED en sortie
  pinMode(LED, OUTPUT);
}


void loop()
{
  // Allumage de la LED = HIGH
  digitalWrite(LED, HIGH);
  delay(200);

  // Extinction de la LED = LOW
  digitalWrite(LED, LOW);
  delay(200);
}
```

---

<div align="center">
    <img
        src="https://github.com/AyckinnLisa/arduino/blob/main/LED/pics/01.png"
        style="width:60%">
</div>
