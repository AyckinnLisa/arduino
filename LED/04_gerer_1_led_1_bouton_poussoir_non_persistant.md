## GERER UNE LED, MODE NON PERSISTANT, AVEC UN BOUTON POUSSOIR

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
    - x1 Arduino Uno
    - x1 Breadboard
    - x1 LED
    - x1 Resistance de 220 ohm
    - 1x Bouton poussoir
</pre>

<br>

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

---

<div align="center">
    <img
        src="https://github.com/AyckinnLisa/arduino/blob/main/LED/pics/02.png"
        style="width:60%">
</div>
