## ALLUMER UNE LED

<pre>
Créé par Yannick HEUDE
04 Novembre 2024


Le programme permet simplement d'allumer une LED avec un Arduino Uno.

Outils:
    - x1 Arduino Uno
    - x1 Breadboard
    - x1 LED
    - x1 Resistance de 220 ohm
</pre>

<br>

```c
// Affectation de la LED sur le port digital 4 du board Arduino
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
}
```

---

<div align="center">
    <img
        src="https://github.com/AyckinnLisa/arduino/blob/main/LED/pics/01.png"
        style="width:60%">
</div>
