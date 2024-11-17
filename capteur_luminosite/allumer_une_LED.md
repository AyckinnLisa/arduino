## ALLUMER UNE LED DANS L'OBSCURITE

#### DESCRIPTION

<pre>
Créé par Yannick HEUDE
09 Novembre 2024


Ce programme permet de récupérer un indice de luminosité à l'aide d'un capteur.
Les résultats seront renvoyés dans le moniteur série.
Passé un certain seuil d'obscurité, la LED s'allume.

Il est à noter que nous ne récupèrerons pas la valeur de luminosité en lux. 
L’Arduino va convertir les valeurs de tension en entrée sur A0 (qui varie de 0 à 5V) 
en un nombre décimal compris entre 0 et 1023.

Plus la valeur se rapprochera de 1023 (donc 5V), plus l’intensité lumineuse sera importante.

Pour ce programme, nous allons reprendre le code de récupération des valeurs du capteur et
lui ajouter la gestion de la LED.

Outils:
    - 1x Arduino Uno
    - 1x Breadboard
    - 1x Resistance de 10KΩ
    - 1x Capteur de luminosité
    - 1x LED
    - 1x Resistance 220Ω
</pre>

#### CODE SOURCE

```c
// Definition du port de la LED
#define LED  4
// Définition du port du capteur sur le port analogique A0
#define lightSensor A0

// Variable d'état de la LED (éteinte par défaut)
bool ledState = false;
// Variable de stockage des valeurs renvoyées par le capteur
int lightValue;


void setup()
{
    // Initialisation de la LED
    pinMode(LED, OUTPUT);
    // Initialisation du moniteur série
    Serial.begin(9600);
}


void loop()
{
    // Lecture et stockage des valeurs renvoyées par le capteur
    lightValue = analogRead(lightSensor);

    // Controle de l'état de la LED en fonction de la luminosité
    if (lightValue <= 100) { digitalWrite(LED, !ledState); }
    else { digitalWrite(LED, ledState); }

    // Affichage des valeurs toutes les secondes dans le moniteur série
    Serial.print("Valeur de luminosité: ");
    Serial.println(lightValue);
    delay(1000);
}
```

#### CIRCUIT

<div align="left">
    <img
        src="https://github.com/AyckinnLisa/arduino/blob/main/pics/light_sensor_led.png"
        style="width:60%">
</div>
