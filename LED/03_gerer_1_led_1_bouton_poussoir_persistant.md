## GERER UNE LED, MODE PERSISTANT, AVEC UN BOUTON POUSSOIR

<pre>
Créé par Yannick HEUDE
04 Novembre 2024


Ce programme permet de gérer une LED avec un bouton poussoir de manière persistante,
c'est à dire que la LED change d'état à chaque pression du bouton.

Dans la mesure où la LED et le bouton ne vont pas bouger des ports sur lesquels ils sont connectés,
ils seront déclarés dans des variables constantes.

Nous utiliserons des booléens pour gérer les différents états du bouton et de la LED.

Outils:
    - 1x Arduino Uno
    - 1x Breadboard
    - 1x LED
    - 1x Resistance de 220 ohm
    - 1x Bouton poussoir
</pre>

<br>

```c
// Association du bouton à pression sur le port digital 13 
#define BUTTON  13
// Association de la LED sur le port digital 4
#define LED  4

bool buttonIsUp = true;
bool ledState = false;


void setup()
{
    // Initialisation du bouton en entrée
    pinMode(BUTTON, INPUT_PULLUP);
    // Initialisation de la LED en sortie
    pinMode(LED, OUTPUT);
}


void loop()
{
    // Lecture de l'état du bouton (par defaut: 1)
    // 0: Bouton pressé
    // 1: Bouton relaché
    bool buttonState = digitalRead(BUTTON);

    // Le court delai sert à éviter d'envoyer une mauvaise information 
    // à la LED due au rebondissement au moment de la pression du bouton
    if (buttonIsUp && !buttonState)
    {
        delay(10);
        // Relecture de l'état du bouton
        buttonState = digitalRead(BUTTON);

        // A chaque pression du bouton, l'état du bouton passe à 0 
        // et la LED change d'état
        if (!buttonState)
        {
            ledState = !ledState;
            digitalWrite(LED, ledState);
        }
    }
    // Réinitialisation du bouton
    buttonIsUp = buttonState;
}
```

---

<div align="center">
    <img
        src="https://github.com/AyckinnLisa/arduino/blob/main/pics/02.png"
        style="width:60%">
</div>
