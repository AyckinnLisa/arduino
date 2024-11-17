## CHANGER LA COULEUR D'UNE LED RGB

#### DESCRIPTION

<pre>
Créé par Yannick HEUDE
16 Novembre 2024


Ce programme permet de changer la couleur de la LED RGB (Red, Green, Blue) en fonction de nos besoins.
Ici, nous allons allumer les couleurs une par une pendant 1 seconde, puis toutes en même temps en 
clignotant pendant 3 secondes, enfin, on éteint la LED pendant 1 seconde et la boucle repart.

Il est à noter que chaque couleur de la LED RGB est considérée comme une LED à part entière.
Il est donc nécessaire d'ajouter une résistance sur chaque patte gérant une couleur.

| | | |     - (R)ouge    - (B)leue
R G B V     - (G)ND      - (V)erte

Une fois ce concept assimilé, le fonctionnement de la LED RGB est identique aux LEDs classiques.

Outils:
    - 1x Arduino Uno
    - 1x Breadboard
    - 1x LED RGB
    - 3x Resistances 220Ω
</pre>

#### CODE SOURCE

```c
// Définition des ports pour chaque couleur de la LED RGB
#define ROUGE  3
#define BLEUE  4
#define VERTE  5

// Variable pour le compteur de clignotement
int count = 1;

// Fonction de gestion des différents états de la LED
void loopColors(bool rState, bool bState, bool gState, int dTime)
{
    digitalWrite(ROUGE, rState);
    digitalWrite(BLEUE, bState);
    digitalWrite(VERTE, gState);
    delay(dTime);

    return 0;
}


void setup()
{
    // Initialisation des couleurs
    pinMode(ROUGE, OUTPUT);  
    pinMode(BLEUE, OUTPUT);
    pinMode(VERTE, OUTPUT);
}


void loop()
{
    // Allumage de la rouge
    loopColors(true, false, false, 1000);
    // Allumage de la bleue
    loopColors(false, true, false, 1000);
    // Allumage de la verte
    loopColors(false, false, true, 1000);

    // Clignotement pendant 10 tours
    for (int i = 1; i < 11; i++)
    {
        loopColors(true, false, false, 100);
        loopColors(false, true, false, 100);
        loopColors(false, false, true, 100);

        count++;
    }
    
    // Extinction de la LED
    loopColors(false, false, false, 500);
}
```

#### CIRCUIT

<div align="left">
    <img
        src="https://github.com/AyckinnLisa/arduino/blob/main/pics/led_rgb.png"
        style="width:60%">
</div>
