## Mesurer l'intensité lumineuse avec 8 LEDs

#### DESCRIPTION

<pre>
Créé par Yannick HEUDE
12 Novembre 2024


Ce programme permet de récupérer un indice de luminosité à l'aide d'un capteur.
Les résultats seront renvoyés dans le moniteur série.
Passé un certain seuil d'obscurité, la LED s'allume.

Il est à noter que nous ne récupèrerons pas la valeur de luminosité en lux. 
L’Arduino va convertir les valeurs de tension en entrée sur A0 (qui varie de 0 à 5V) 
en un nombre décimal compris entre 0 et 1023.

Plus la valeur se rapprochera de 1023 (donc 5V), plus l’intensité lumineuse sera importante.

Outils:
    - 1x Arduino Uno
    - 1x Breadboard
    - 1x Resistance de 10KΩ
    - 1x Capteur de luminosité
    - 8x LEDs
    - 8x Resistances 220Ω
</pre>

#### CODE SOURCE

```c
// Definition des ports des 8 LEDs
#define LED1  3
#define LED2  4
#define LED3  5
#define LED4  6
#define LED5  7
#define LED6  8
#define LED7  9
#define LED8 10

// Definition du port du capteur sur le port analogique A0
#define lightSensor A0

// Variable de stockage de l'intensité lumineuse
int lightValue;


// Gestion de l'allumage des LEDs en fonction de la valeur de l'intensité
void intensity_measure(int value, int limit, int ledPort)
{
    if (value >= limit) { digitalWrite(ledPort, HIGH); }
    else { digitalWrite(ledPort, LOW); }
}


void setup() 
{
    // Initialisation des LEDs
    pinMode(LED1, OUTPUT);
    pinMode(LED2, OUTPUT);
    pinMode(LED3, OUTPUT);
    pinMode(LED4, OUTPUT);
    pinMode(LED5, OUTPUT);
    pinMode(LED6, OUTPUT);
    pinMode(LED7, OUTPUT);
    pinMode(LED8, OUTPUT);
}


void loop() 
{
    // Lecture et stockage des valeurs renvoyées par le capteur
    lightValue = analogRead(lightSensor);
    // Delai de traitement de récupération des valeurs en millisecondes
    delay(10);

    intensity_measure(lightValue, 1, LED1);
    intensity_measure(lightValue, 120, LED2);
    intensity_measure(lightValue, 240, LED3);
    intensity_measure(lightValue, 360, LED4);
    intensity_measure(lightValue, 480, LED5);
    intensity_measure(lightValue, 600, LED6);
    intensity_measure(lightValue, 720, LED7);
    intensity_measure(lightValue, 840, LED8);
}
```

#### CIRCUIT

<div align="center">
    <img
        src="https://github.com/AyckinnLisa/arduino/blob/main/pics/light_sensor_8_leds.png"
        style="width:60%">
</div>