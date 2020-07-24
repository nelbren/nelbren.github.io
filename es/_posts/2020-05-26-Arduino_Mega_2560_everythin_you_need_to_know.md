---
title: Arduino Mega, todo lo que necesitas saber
last_modified_at: 2020-05-26T02:53:00-06:00
ref: arduino_mega_everything_you_need_to_know
locale: es
categories:
- arduino
tags:
- arduino
- led
excerpt: "Comparación de Arduino Mega 2560 y Arduino UNO"
header:
  overlay_image: /assets/images/posts/Mega2560/a000067_featured_1_.jpg
  overlay_filter: 0.7
  show_overlay_excerpt: true
  teaser: /assets/images/posts/Mega2560/a000067_featured_1_.jpg
toc: true
toc_sticky: false
author_profile: true
---

# Arduino Mega 2560, todo lo que necesitas saber

## Introducción

Hace algunos unos días estuve conversando con un amigo que no veía hace meses, él es un apasionado del **Internet de las Cosas** y esa última vez que hablamos me comentaba que estaba trabajando en un proyecto de una **Estación Meteorológica**, me compartió que estaba usando un **Arduino UNO** como cerebro al cual se conectaban todos los sensores. Para mi sorpresa, en este momento ya cuenta con 32 Estaciones Meteorológicas diseminadas estratégicamente con el fin de obtener datos estadísticos que le proporcionen información para poder realizar **inteligencia artificial**, **análisis de tendencias**, entre otros. Uno de los detalles que me explicaba era el hecho de que ahora el proyecto tenía dos componentes de Arduino, uno era un **Arduino Mega** como cerebro y control de todos los sensores y el otro un **Arduino UNO** como vigilante del cerebro (Arduino Mega). Por lo que me entro la curiosidad de conocer más sobre las capacidades del Arduino Mega y compararlo con el Arduino Uno; documentar mis observaciones y compartir estos hallazgos en este tutorial.

Lo primero que debemos saber es lo básico, o sea la primer interrogante, que te puedes plantear es:

## ¿Qué es Arduino Mega?

**Arduino Mega 2560 R3** es una tarjeta de desarrollo mucho más potente que el **Arduino UNO**. Como nombremos la placa es indistinto, **"Arduino Mega"**, **"Arduino Mega 2560"** o **"Arduino Mega 2560 R3"**, en este tutorial la llamaremos **"Arduino Mega"**.

### Comparación física entre Arduino Mega y Arduino UNO

![Arduino Mega](/assets/images/posts/Mega2560/arduino_mega_y_arduino_uno.jpg)

Pero en **¿qué es más potente?**, para ello tenemos que ver en que difieren:

## Diferencia entre Arduino Mega y Arduino UNO

Las diferencias más significativas entre el **Arduino Mega** y el **Arduino UNO** es el **tamaño de la placa**, **la capacidad de la memoria flash**, así como el **número de pines digitales y analógicos**. 
No obstante, las placas tienen las mismas características respecto al **voltaje**, **la corriente de los pines**, **la velocidad de reloj** y el **led incorporado**. 
A continuación, puedes observar con más en detalle dichas diferencias y además las similitudes entre ambas placas.

## Características técnicas

|Característica|Arduino Mega 2560|Arduino UNO|
|--:|:--|:--|
|Revisión|3|3|
|Microcontrolador|ATmega2560|ATmega328P|
|Voltaje de Operación|5V|5V|
|Voltaje de entrada (recomendado)|7-12V|7-12V|
|Voltaje de entrada (limite)|6-20V|6-20V|
|Pines digitales de entrada/salida|**54 (15 salidas PWM)**|14 (6 salidas PWM)|
|Pines analógicos de entrada|**16**|6|
|Corriente por pines de entrada/salida|20mA|20mA|
|Corriente para pin 3.3V|50mA|50mA|
|Memoria Flash|**256KB (8KB bootloader)**|32KB (0.5KB bootloader)|
|Memoria SRAM|**8KB**|2KB|
|Memoria EEPROM|**4KB**|1KB|
|Velocidad de reloj|16Mhz|16Mhz|
|Led incorporado|13|13|
|Longitud|**101.52mm**|68.6mm|
|Ancho|**52.3mm**|53.4mm|
|Peso|**37g**|25g|

---

## Dónde comprar

### En la tienda de [Arduino](https://store.arduino.cc/)

   ![Arduino](/assets/images/posts/Mega2560/Arduino_Logo.svg)

   - [ARDUINO MEGA 2560 REV3](https://store.arduino.cc/usa/mega-2560-r3)

     ![Arduino Mega](/assets/images/posts/Mega2560/a000067_featured_1_.jpg)

   - [ARDUINO UNO REV3](https://store.arduino.cc/usa/arduino-uno-rev3)

     ![Arduino UNO](/assets/images/posts/Mega2560/a000066_featured_5.jpg)

### En la tienda de [C&D Technologia](http://cdtechnologia.net)

   ![C&D Technologia](/assets/images/posts/Mega2560/circuitos-y-desarrollo-en-tecnologia-cd-technologia-logo-1589751414.jpg)

   - [Arduino Mega 2560](https://cdtechnologia.net/arduino/47-arduino-mega-2560.html)

     ![Arduino Mega](/assets/images/posts/Mega2560/arduino_mega.png)

   - [Arduino Uno Rev3](https://cdtechnologia.net/arduino/46-arduino-uno-generico-2.html)

     ![Arduino Mega](/assets/images/posts/Mega2560/arduino_uno.png)

### En la tienda de [Amazon](https://amazon.com)

   ![Amazon](/assets/images/posts/Mega2560/640px-Amazon_logo.svg.png)

   - [Arduino Mega 2560](https://www.amazon.com/s?k=arduino+mega+2560+r3&ref=nb_sb_noss_1)

     ![Arduino Mega](/assets/images/posts/Mega2560/arduino_mega.png)

   - [Arduino Uno Rev3](https://www.amazon.com/s?k=Arduino+Uno+Rev3&ref=nb_sb_noss_2)

     ![Arduino Mega](/assets/images/posts/Mega2560/arduino_uno.png)

## Diferencias entre placas originales y copias

En realidad, todas las placas utilizan el mismo microcontrolador dependiendo del modelo. Por lo tanto, un Arduino copia y un Arduino original se programan igual. La diferencia está en dónde se fabrica y en los componentes, y ahí es donde radica el problema. Sí deseas saber más detalles acerca de adquirir una placa original o una copia te invito a que veas el artículo sobre [Comprar Arduino original o Arduino copia, tu eliges](https://programarfacil.com/blog/comprar-una-placa-original-o-una-placa-copia-de-arduino/)

---

## Cómo programar el Arduino Mega

Para programar el **Arduino Mega** se utilizó el software **Arduino IDE v1.8.12**, se conectó la placa por medio del cable USB a la computadora, y definieron los siguientes elementos para hacer la conexión:

|Tipo|Valor|
|--:|:--|
|Placa|**"Arduino Mega o Mega 2560"**|
|Procesador|**ATmega 2560 (Mega 2560)**|
|Puerto|**COM3** (Dependerá de su configuración)|

### La prueba más sencilla y rápida, uso del led incorporado

  1. Seleccionar el proyecto **Blink** que viene en los *Ejemplos* de *01.Basics*
  
     ![Blink_1](/assets/images/posts/Mega2560/blink_1_mega_o_uno.png)

  2. Modificar los **milisegundos** de las dos instrucciones de `delay` para que sea más notorio el "**parpadeo**" del *led incorporado en la placa*.
  
     ```
     delay(250);
     ```
  
  3. Subir el programa.
  
     ![Blink_2](/assets/images/posts/Mega2560/blink_2_mega.png)

  4. Verificar el **apagado** y **encendido** del *led incorporado en la placa*.
  
     ![Blink_3](/assets/images/posts/Mega2560/blink_3_mega.jpg)

### Ejemplo de uso de sensor ultrasónico HC-SR04

Vamos a utilizar el mismo sensor del artículo [Sensor de nivel de agua con Arduino](https://programarfacil.com/blog/arduino-blog/sensor-de-nivel-de-agua-con-arduino/), a fin de demostrar cómo programar el **Arduino Mega**; comprobando que dicha programación es 100% compatible con el **Arduino UNO**.

|Arduino Mega|HC-SR04|
|--:|:--|
|**GND**|**Gnd**|
|**5V**|**Vcc**|
|Pin 6|Echo|
|Pin 7|Trig|

#### Esquema de conexiones

<center>
  <img src="/assets/images/posts/Mega2560/arduino_mega_con_hc-sr04_bb.svg" height="600px"/>
</center>  

#### Imagen de conexiones
![Arduino_Mega_con_hc-src04](/assets/images/posts/Mega2560/arduino_mega_con_hc-sr04.jpg)

---

## Cómo programar el Arduino UNO

Para programar el **Arduino UNO** se utilizó el software **Arduino IDE v1.8.12**, se conectó la placa por medio del cable USB a la computadora, y definieron los siguientes elementos para hacer la conexión:

|Tipo|Valor|
|--:|:--|
|Placa|**"Arduino Uno"**|
|Puerto|**COM4** (Dependerá de su configuración)|

### La prueba más sencilla y rápida, uso del led incorporado

  1. Seleccionar el proyecto **Blink** que viene en los *Ejemplos* de *01.Basics*
  
     ![Blink_1](/assets/images/posts/Mega2560/blink_1_mega_o_uno.png)

  2. Modificar los **milisegundos** de las dos instrucciones de `delay` para que sea más notorio el "**parpadeo**" del *led incorporado en la placa*.
  
     ```
     delay(250);
     ```
  
  3. Subir el programa.
  
     ![Arduino UNO](/assets/images/posts/Mega2560/blink_2_uno.png)

  4. Verificar el **apagado** y **encendido** del *led incorporado en la placa*.
  
     ![Arduino UNO](/assets/images/posts/Mega2560/blink_3_uno.jpg)

### Ejemplo de uso de sensor ultrasónico HC-SR04

Vamos a utilizar el mismo sensor del artículo [Sensor de nivel de agua con Arduino](https://programarfacil.com/blog/arduino-blog/sensor-de-nivel-de-agua-con-arduino/), a fin de demostrar cómo programar el **Arduino UNO**; comprobando que dicha programación es 100% compatible con el **Arduino Mega**.

|Arduino UNO|HC-SR04|
|--:|:--|
|**GND**|**Gnd**|
|**5V**|**Vcc**|
|Pin 6|Echo|
|Pin 7|Trig|

#### Esquema de conexiones

<center>
  <img src="/assets/images/posts/Mega2560/arduino_uno_con_hc-sr04_bb.svg" height="600px"/>
</center>  

#### Imagen de conexiones

![Arduino_UNO_con_hc-src04](/assets/images/posts/Mega2560/arduino_uno_con_hc-sr04.jpg)

---

## Conclusiones

En este momento, cuando ya conocemos la placa **Arduino Mega**, sus características, sus diferencias y similitudes, con respecto al **Arduino UNO**, validando que ambas son **100% compatibles en su programación**, nos encontramos con la facultad para entender qué cuando necesitas realizar un proyecto, en donde tendrás muchos sensores o actuadores, como el caso de mi amigo, que su proyecto de **"Estación Meteorológica Solar 9 en 1"**, el cual consta de sensores de velocidad de viento, dirección del viento, luminosidad, humedad del suelo, temperatura, humedad relativa ambiental, precipitación de lluvia (pluviómetro) y sistemas de transmisión GSM, almacenamiento de datos, transmisión RF y de energía solar. Está cantidad de sensores y sistemas no pueden ser manejados por un **Arduino UNO**, por lo que es necesario y obligatorio un equipo como el **Arduino Mega** para llevar a cabo dicha tarea. Sin embargo, en proyectos con pocos sensores el **Arduino Mega** seria completamente subutilizado, en este caso la mejor opción sería un **Arduino UNO**. Por lo tanto, dependerá de tu proyecto el uso de una placa o la otra.
