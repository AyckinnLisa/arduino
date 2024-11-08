## CONTROLER UNE LED AVEC UN POTENTIOMETRE

<pre>
Créé par Yannick HEUDE
08 Novembre 2024

Ce programme permet de controler l'intensité lumineuse d'une LED en utilisant un potentiomètre.

Puisque l'idée est d'influer sur la luminosité de la LED, elle doit être connectée sur un port de
modulation PWM et le potentiomètre sur un port analogique.

Outils:
    - 1x Arduino Uno
    - 1x Breadboard
    - 1x LED 
    - 1x Resistances de 220 ohm
    - 1x Potentiomètre
</pre>

<br>

```c
// Définition du port de la LED
#define LED   3
// Définition du port du potentiomètre
#define POTI A0

// Variable de stockage des valeurs du potentiomètre
unsigned int potiValue;
// Variable de stockage des valeurs d'intensité de la LED
int ledIntensityValue;


void setup()
{
    // Initialisation de la LED en sortie
    pinMode(LED, OUTPUT);
}


void loop()
{
    // Lecture de la broche analogique et stockage de la valeur du potentiomètre
    potiValue = analogRead(POTI);

    /*
        Initialisation des bornes min et max de l'intensité de la LED avec la fonction [MAP]
        [MAP] transforme les valeurs du potentiomètre en valeurs acceptables pour la LED et utilise 5 paramètres:
            - [potiValue]: La variable de stockage des valeurs du potentiomètre
            - [0]:    Valeur minimale du potentiomètre
            - [1023]: Valeur maximale du potentiomètre
            - [0]:    Valeur minimale de l'intensité de la LED
            - [255]:  Valeur maximale de l'intensité de la LED
    */
    ledIntensityValue = map(potiValue, 0, 1023, 0, 255);

    // Envoi la valeur du potentiomètre dans la LED
    analogWrite(LED, ledIntensityValue);

    // Pour éviter d'envoyer une mauvaise information à la LED au moment du mouvement du potentiomètre,
    // un délai de 10 millisecondes est nécessaire avant que la LED n'affiche la valeur.
    delay(10);
}
```

---

<div align="center">
    <img
        src="https://github.com/AyckinnLisa/arduino/blob/main/LED/pics/07.png"
        style="width:60%">
</div>

---

![Démo: ](https://www.tinkercad.com/things/02s6dJYr2DA-ledpotentiometre")