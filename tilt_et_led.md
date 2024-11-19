## GESTION D'UNE LED AVEC UN TILT

#### DESCRIPTION

<pre>
Créé par Yannick HEUDE
19 Novembre 2024

Ce programme permet d'allumer ou éteindre une LED avec un tilt.

Si la bille du tilt touche les pattes de connexion, la LED s'allume.
Des que la bille perd le contact avec les pattes, le LED s'éteint.

Outils:
    - 1x Arduino Uno
    - 1x Breadboard
    - 1x LED
    - 1x Resistance de 220Ω
    - 1x Tilt
</pre>

#### CODE SOURCE

```c
// Association du port de la LED
#define LED 3
// Association du port du tilt
#define TILT 8


void setup()
{
    // Initialisation du tilt en entrée car c'est lui qui va
    // envoyer l'information à la LED
    pinMode(TILT, INPUT_PULLUP);
    // Initialisation de la LED car elle ne va faire que réagir
    // à l'information du tilt
    pinMode(LED, OUTPUT);
}


void loop()
{
    // Si la bille touche les pattes de connexion du tilt, la LED s'allume
    if (digitalRead(TILT) == LOW) { digitalWrite(LED, HIGH); }
    else { digitalWrite(LED, LOW); }
}
```

#### CIRCUIT

<div align="left">
    <img
        src="https://github.com/AyckinnLisa/arduino/blob/main/pics/tilt_led.png"
        style="width:60%">
</div>
