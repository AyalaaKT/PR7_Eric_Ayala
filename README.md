# PR7_PD_EricAyala

## PRACTICA 6:  Buses de comunicación III (I2S)

### Ejercicio Práctico

**Codigo:**
```cpp
    #include <Arduino.h>
    #include "AudioGeneratorAAC.h"
    #include "AudioOutputI2S.h"
    #include "AudioFileSourcePROGMEM.h"
    #include "sampleaac.h"

    AudioFileSourcePROGMEM *in;
    AudioGeneratorAAC *aac;
    AudioOutputI2S *out;

    void setup()
    {
    Serial.begin(115200);

    audioLogger = &Serial;
    in = new AudioFileSourcePROGMEM(sampleaac, sizeof(sampleaac));
    aac = new AudioGeneratorAAC();
    out = new AudioOutputI2S();

    aac->begin(in, out);
    }


    void loop()
    {
    if (aac->isRunning()) {
        aac->loop();
    } else {
        Serial.printf("AAC done\n");
        delay(1000);
    }
    }
```
## EXPLICACIÓN DEL CÓDIGO
Este código reproduce un archivo de audio en formato AAC almacenado en la memoria flash del microcontrolador y utiliza una salida de audio I2S.

Se incluyen las librerías necesarias: Arduino.h para funciones básicas, AudioGeneratorAAC.h para decodificar el audio AAC, AudioOutputI2S.h para manejar la salida de audio I2S, y AudioFileSourcePROGMEM.h para acceder al archivo de audio en la memoria flash. Además, se incluye sampleaac.h, que contiene el archivo de audio.

Se declaran tres variables globales: in, que es una instancia de AudioFileSourcePROGMEM para la fuente de audio; aac, que es una instancia de AudioGeneratorAAC para la decodificación; y out, que es una instancia de AudioOutputI2S para la salida de audio.

## CONCLUSIÓN
En conclusión, hemos logrado configurar y controlar la reproducción de archivos de audio AAC almacenados en la memoria flash a través de la salida I2S. Esta práctica ha sido efectiva y nos proporciona una base sólida para futuros proyectos de audio.
