## ALLUMER PLUSIEURS LEDS

<pre>
Créé par Yannick HEUDE
07 Novembre 2024

Ce programme permet d'allumer 4 LEDs une par une, toutes les secondes de manière 
non persistente, puis, une par une de manière persistante et enfin, il éteint toutes
les LEDs et la boucle reprend.

Pour ce programme, nous allons reprendre le même principe que pour le feu tricolore.
Lien: [Feu tricolore](https://github.com/AyckinnLisa/arduino/blob/main/LED/07_simulation_feu_tricolore.md)

Outils:
    - 1x Arduino Uno
    - 1x Breadboard
    - 4x LEDs (bleue, rouge, orange, verte)
    - 4x Resistances de 220 ohm
</pre>

<br>

```c
// Définition des ports des LEDs
#define BLUE   13
#define RED    12
#define ORANGE  7
#define GREEN   4

// Fonction de gestion du cycle
void led_on_off(bool BLedState, bool RLedState, bool OLedState, bool GLedState, int wait)
{
    digitalWrite(BLUE, BLedState);
    digitalWrite(RED, RLedState);
    digitalWrite(ORANGE, OLedState);
    digitalWrite(GREEN, GLedState);
    delay(wait);

    return 0;
}


void setup()
{
    // Initialisation des LEDs en sortie
    pinMode(BLUE, OUTPUT);
    pinMode(RED, OUTPUT);
    pinMode(ORANGE, OUTPUT);
    pinMode(GREEN, OUTPUT);
}


void loop()
{
    // Chaque LEDs seules
    led_on_off(true, false, false, false, 1000);
    led_on_off(false, true, false, false, 1000);
    led_on_off(false, false, true, false, 1000);
    led_on_off(false, false, false, true, 1000);

    // Toutes les LEDs ensembles
    led_on_off(true, false, false, false, 1000);
    led_on_off(true, true, false, false, 1000);
    led_on_off(true, true, true, false, 1000);
    led_on_off(true, true, true, true, 1000);

    // On éteint tout et on recommence
    led_on_off(false, false, false, false, 1000);
}
```

---

<div align="center">
    <img
        src="https://github.com/AyckinnLisa/arduino/blob/main/LED/pics/06.png"
        style="width:60%">
</div>
