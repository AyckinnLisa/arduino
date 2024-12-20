## FAIRE CLIGNOTER UNE LED

#### DESCRIPTION

<pre>
Créé par Yannick HEUDE
04 Novembre 2024


Le programme permet de faire clignoter une LED toutes les 200 millisecondes (0.2 secondes).

Dans la mesure où la LED ne va pas bouger du port sur lequel elle est connectée,
elle est déclarée dans une variable constante.

Outils:
    - 1x Arduino Uno
    - 1x Breadboard
    - 1x LED
    - 1x Resistance de 220Ω
</pre>

#### CODE SOURCE

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

#### CIRCUIT

<div align="left">
    <img
        src="https://github.com/AyckinnLisa/arduino/blob/main/pics/01.png"
        style="width:60%">
</div>
