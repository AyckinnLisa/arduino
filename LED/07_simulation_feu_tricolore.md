## SIMULATION D'UN FEU TRICOLORE

#### DESCRIPTION

<pre>
Créé par Yannick HEUDE
06 Novembre 2024

Ce programme permet de simuler un feu tricolore routier.
Le feu rouge reste actif 7 secondes, ensuite, il passe au vert pendant 7 secondes, puis,
il passe au orange pendant 4 secondes et reprend la boucle au début.

La solution de facilité serait d'utiliser les paramètres HIGH (allumée) et LOW (éteinte),
le problème est que pour chaque action du feu tricolore, il faut lister l'état de chaque LED,
ce qui est assez lourd et utilise beaucoup de répétition de code.

Pour optimiser le code et alleger la boucle, nous allons utiliser une fonction et les booléens
pour gérer l'état des LEDs: (True: Allumée - False: Eteinte).

Outils:
    - 1x Arduino Uno
    - 1x Breadboard
    - 3x LEDs (rouge, orange, verte)
    - 3x Resistances de 220Ω
</pre>

#### CODE SOURCE

```c
// Définition des sorties des LEDs
#define RED    12
#define ORANGE  7
#define GREEN   4

// Fonction de gestion du cycle
void led_on_off(bool redLedState, bool orangeLedState, bool greenLedState, int wait)
{
    digitalWrite(RED, redLedState);
    digitalWrite(ORANGE, orangeLedState);
    digitalWrite(GREEN, greenLedState);
    delay(wait);

    return 0;
}


void setup()
{
    // Initialisation des LEDs en sortie
    pinMode(RED, OUTPUT);
    pinMode(ORANGE, OUTPUT);
    pinMode(GREEN, OUTPUT);
}


void loop()
{
    // Feu rouge
    led_on_off(true, false, false, 7000);
    // Feu vert
    led_on_off(false, false, true, 7000);
    // Feu orange
    led_on_off(false, true, false, 4000);
}
```

#### CIRCUIT

<div align="left">
    <img
        src="https://github.com/AyckinnLisa/arduino/blob/main/pics/05.png"
        style="width:60%">
</div>
