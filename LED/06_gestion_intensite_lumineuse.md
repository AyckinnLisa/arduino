## GERER L'INTENSITE D'UNE LED AVEC DEUX BOUTONS POUSSOIRS

<pre>
Créé par Yannick HEUDE
04 Novembre 2024


Ce programme permet de gérer l'intensité d'une LED avec deux boutons poussoirs.
Un bouton pour l'augmentation de l'intensité et un bouton pour la diminution.

Nous utiliserons des booléens pour gérer les différents états des boutons et de la LED.

Il est IMPERATIF que la LED soit connectée sur un port 'Pulse Width Modulation' (PWM) ou 
Modulation de Largeur d'Impulsion (MLI), qui est un port de gestion de modulation allant
de 0 à 100%. Sur le board Arduino, ils sont identifiés par le signe [~].

Pour déterminer les valeurs minimales et maximales à utiliser pour le réglage de l'intensité,
il faut utiliser la fonction [constrain]. Elle prend 3 paramètres:
    - La valeur actuelle
    - La valeur minimale
    - La valeur maximale
    
Il est à noter que les valeurs minimales et maximales utilisables sont (0 - 255), nous pouvons
donc travailler dans cet intervalle.


Outils:
    - x1 Arduino Uno
    - x1 Breadboard
    - x1 LED
    - x1 Resistance de 220 ohm
    - x2 Boutons poussoirs
</pre>

<br>

```c
// Association de la LED sur le port digital PWM 3
#define LED  3
// Association des boutons sur les ports digitaux 12 et 13
#define BUTTON_UP   12
#define BUTTON_DOWN 13

// Définition de l'intensité au maximum par défaut
int brightness = 240;
// Définition des actions d'augmentation et de diminution de l'intensité
bool upLight = true;
bool downLight = true;


void setup()
{
    // Initialisation de la LED en sortie
    pinMode(LED, OUTPUT);
    // Initialisation des boutons en entrée
    pinMode(BUTTON_UP, INPUT_PULLUP);
    pinMode(BUTTON_DOWN, INPUT_PULLUP);
}


void loop()
{
    // [analogWrite] permet de prendre en compte la variation de l'intensité
    analogWrite(LED, brightness);

    // Définition des valeurs de modification de l'intensité
    upLight = PressButton(BUTTON_UP, upLight, +30);
    downLight = PressButton(BUTTON_DOWN, downLight, -30);
}



// Création de la fonction de gestion de la pression des boutons
bool PressButton(int buttonPin, bool isActive, int lightValue)
{
    bool isActivated = digitalRead(buttonPin);

    // Le court délai permet d'éviter d'envoyer une mauvaise information à la LED
    // due au rebondissement au moment de la pression du bouton
    if (isActive && !isActivated)
    {
        delay(10);
        isActivated = digitalRead(buttonPin);

        // Définit les valeurs minimales et maximales (0 à 240)
        if (!isActivated) { brightness = constrain((brightness + lightValue), 0, 240); }
    }
    return isActivated;
}
```

---

<div align="center">
    <img
        src="https://github.com/AyckinnLisa/arduino/blob/main/LED/pics/04.png"
        style="width:60%">
</div>
