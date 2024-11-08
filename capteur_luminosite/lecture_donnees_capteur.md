## LECTURE DES DONNEES DU CAPTEUR DE LUMINOSITE

<pre>
Créé par Yannick HEUDE
08 Novembre 2024


Ce programme permet de récupérer un indice de luminosité à l'aide d'un capteur.
Les résultats seront renvoyés dans le moniteur série.

Il est à noter que nous ne récupèrerons pas la valeur de luminosité en lux. 
L’Arduino va convertir les valeurs de tension en entrée sur A0 (qui varie de 0 à 5V) 
en un nombre décimal compris entre 0 et 1023.

Plus la valeur se rapprochera de 1023 (donc 5V), plus l’intensité lumineuse sera importante.

Outils:
    - 1x Arduino Uno
    - 1x Breadboard
    - 1x Resistance de 10K ohm
    - 1x Capteur de luminosité
</pre>

<br>

```c
// Définition du port du capteur sur le port analogique A0
#define lightSensor A0

// Variable de stockage des valeurs renvoyées par le capteur
int lightValue;


void setup()
{
    // Initialisation du moniteur série
    Serial.begin(9600);
}


void loop()
{
    // Leture et stockage des valeurs renvoyées par le capteur
    lightValue = analogRead(lightSensor);

    // Affichage des valeurs toutes les secondes dans le moniteur série
    Serial.print("Valeur de luminosité: ");
    Serial.println(lightValue);
    delay(1000);
}
```

---

<div align="center">
    <img
        src="https://github.com/AyckinnLisa/arduino/blob/main/pics/light_sensor.png"
        style="width:60%">
</div>
