## GERER UNE LED, MODE NON PERSISTANT, AVEC UN BOUTON POUSSOIR

#### DESCRIPTION

<pre>
Créé par Yannick HEUDE
04 Novembre 2024


Ce programme permet de gérer une LED avec un bouton poussoir de manière non persistante,
c'est à dire que la LED change d'état selon l'état du bouton:
    - Bouton pressé:  LED allumée
    - Bouton relaché: LED éteinte

Dans la mesure où la LED et le bouton ne vont pas bouger des ports sur lesquels ils sont connectés,
ils seront déclarés dans des variables constantes.

Nous utiliserons des booléens pour gérer les différents états du bouton et de la LED.

Outils:
    - 1x Arduino Uno
    - 1x Breadboard
    - 1x LED
    - 1x Resistance de 220Ω
    - 1x Bouton poussoir
</pre>

#### CODE SOURCE

```c
// Association du bouton à pression sur le port digital 13
#define BUTTON  13
// Association de la LED sur le port digital 4
#define LED  4

// LED eteinte par defaut
bool LEDState = false;


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

          // == 0                        == True: Allumée
    if (!buttonState) { digitalWrite(LED, !LEDState); }
    else { digitalWrite(LED, LEDState); }
}
```

#### CIRCUIT

<div align="left">
    <img
        src="https://github.com/AyckinnLisa/arduino/blob/main/pics/02.png"
        style="width:60%">
</div>
