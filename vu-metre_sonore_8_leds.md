## VU-METRE SONORE AVEC 8 LEDS

<pre>
Créé par Yannick HEUDE
16 Novembre 2024

Outils:
    - 1x Arduino Uno
    - 1x Breadboard
    - 1x Capteur sonore
    - 8x LEDs
    - 8x Resistances 220Ω
</pre>

#### CODE SOURCE

```c
// Definition des ports des LEDs
int ledsPort[8] = {3, 4, 5, 6, 7, 8, 9, 10};

// Definition du port du micro
#define MICRO A0

// Definition des variables de stockage des données sonores et des LEDs
int soundValue, led;


void setup()
{
    // Initialisation des LEDs
    for(led = 0; led < 8; led++) { pinMode(ledsPort[led], OUTPUT); }
}


void loop()
{
    // Lecture des données sonores
    soundValue = analogRead(MICRO);
    // Conversion des valeurs sonores
    soundValue = (soundValue / 9);

    if (soundValue < 9)
    {
        if (soundValue == 0)
        {
            for (led = 0; led < 8; led++) { digitalWrite(ledsPort[led], LOW); }
        }
        else
        {
            for (led = 0; led < soundValue; led++)
            {
                digitalWrite(ledsPort[led], HIGH);
                delay(10);
            }
            for (led = led; led < 8; led++) { digitalWrite(ledsPort[led], LOW); }
        }
    }
}
```
