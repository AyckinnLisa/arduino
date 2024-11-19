## CHANGER LA COULEUR D'UNE LED RGB EN MODE PERSISTANT AVEC 3 BOUTONS POUSSOIRS

#### DESCRIPTION

<pre>
Créé par Yannick HEUDE
17 Novembre 2024


Ce programme permet de changer la couleur d'une LED RGB (Red, Green, Blue) avec 3 boutons poussoirs.
1 bouton pour chaque couleur.

Il est à noter que chaque couleur de la LED RGB est considérée comme une LED à part entière.
Il est donc nécessaire d'ajouter une résistance sur chaque patte gérant une couleur.

| | | |     - (R)ouge    - (B)leue
R G B V     - (G)ND      - (V)erte

Une fois ce concept assimilé, le fonctionnement de la LED RGB est identique aux LEDs classiques.
Notez aussi que l'ordre des pattes de la LED peuvent varier selon la référence de la LED.

Outils:
    - 1x Arduino Uno
    - 1x Breadboard
    - 1x LED RGB
    - 3x Resistances 220Ω
    - 3x Boutons poussoirs
</pre>

#### CODE SOURCE

```c
// Définition des ports des boutons
#define RED_BTN   6
#define BLUE_BTN  5
#define GREEN_BTN 4
// Définition des ports pour chaque couleur de la LED RGB
#define RED_COLOR   10
#define BLUE_COLOR  9
#define GREEN_COLOR 8

// LED rouge
bool redButtonIsUp = true;
bool redLedState = false;
// LED Bleue
bool blueButtonIsUp = true;
bool blueLedState = false;
// LED Verte
bool greenButtonIsUp = true;
bool greenLedState = false;


void setup()
{
    // Initialisation des boutons
    pinMode(RED_BTN, INPUT_PULLUP);
    pinMode(BLUE_BTN, INPUT_PULLUP);
    pinMode(GREEN_BTN, INPUT_PULLUP);
    // Initialisation des LEDs
    pinMode(RED_COLOR, OUTPUT);
    pinMode(BLUE_COLOR, OUTPUT);
    pinMode(GREEN_COLOR, OUTPUT);
}


void loop()
{
    bool redBtnState = digitalRead(RED_BTN);
    bool blueBtnState = digitalRead(BLUE_BTN);
    bool greenBtnState = digitalRead(GREEN_BTN);

    // ROUGE
    if (redButtonIsUp && !redBtnState)
    {
        delay(10);
        redBtnState = digitalRead(RED_BTN);

        if (!redBtnState)
        {
            redLedState = !redLedState;
            digitalWrite(RED_COLOR, redLedState);
        }
    }
    redButtonIsUp = redBtnState;

    // BLEUE
    if (blueButtonIsUp && !blueBtnState)
    {
        delay(10);
        blueBtnState = digitalRead(BLUE_BTN);

        if (!blueBtnState)
        {
            blueLedState = !blueLedState;
            digitalWrite(BLUE_COLOR, blueLedState);
        }
    }
    blueButtonIsUp = blueBtnState;

    // VERTE
    if (greenButtonIsUp && !greenBtnState)
    {
        delay(10);
        greenBtnState = digitalRead(GREEN_BTN);

        if (!greenBtnState)
        {
            greenLedState = !greenLedState;
            digitalWrite(GREEN_COLOR, greenLedState);
        }
    }
    greenButtonIsUp = greenBtnState;
}
```

#### CIRCUIT

<div align="left">
    <img
        src="https://github.com/AyckinnLisa/arduino/blob/main/pics/led_rgb_buttons.png"
        style="width:60%">
</div>
