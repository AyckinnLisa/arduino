## GERER UNE LED, MODE PERSISTANT, AVEC DEUX BOUTONS POUSSOIRS

#### DESCRIPTION

<pre>
Créé par Yannick HEUDE
04 Novembre 2024


Ce programme permet de gérer une LED avec deux boutons poussoirs de manière persistante,
c'est à dire que la LED change d'état selon le bouton pressé.

Dans la mesure où la LED et les boutons ne vont pas bouger des ports sur lesquels ils sont connectés,
ils seront déclarés dans des variables constantes.

Nous utiliserons des booléens pour gérer les différents états des boutons et de la LED.

Outils:
    - 1x Arduino Uno
    - 1x Breadboard
    - 1x LED
    - 1x Resistance de 220Ω
    - 2x Boutons poussoirs
</pre>

#### CODE SOURCE

```c
// Association des boutons à pression sur les ports digitaux 12 et 13
#define BUTTON_ON   12
#define BUTTON_OFF  13
// Association de la LED sur le port digital 4
#define LED  4

// Définition des boutons sur 1 par défaut
bool buttonOnIsUp = true;
bool buttonOffIsUp = true;
// LED eteinte par defaut
bool ledState = false;


void setup()
{
    // Initialisation des boutons ON et OFF en entrée
    pinMode(BUTTON_ON, INPUT_PULLUP);
    pinMode(BUTTON_OFF, INPUT_PULLUP);

    // Initialisation de la LED en sortie
    pinMode(LED, OUTPUT);
}


void loop()
{
    // Lecture de l'état des boutons (par defaut: 1)
    // 0: Bouton pressé
    // 1: Bouton relaché
    bool buttonOnState = digitalRead(BUTTON_ON);
    bool buttonOffState = digitalRead(BUTTON_OFF);

    // Gestion de l'allumage de la LED
    // Le court delai sert à éviter d'envoyer une mauvaise information 
    // à la LED due au rebondissement au moment de la pression du bouton
    if (buttonOnIsUp && !buttonOnState)
    {
        delay(10);
        buttonOnState = digitalRead(BUTTON_ON);

        if (!buttonOnState) { digitalWrite(LED, !ledState); }
    }

    // Gestion de l'extinction de la LED
    if (buttonOffIsUp && !buttonOffState)
    {
        delay(10);
        buttonOffState = digitalRead(BUTTON_OFF);
        
        if (!buttonOffState) { digitalWrite(LED, ledState); }
    }
}
```

#### CIRCUIT

<div align="left">
    <img
        src="https://github.com/AyckinnLisa/arduino/blob/main/pics/03.png"
        style="width:60%">
</div>
