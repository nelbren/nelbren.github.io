---
title: Visualización en Arduino de la Barra de Información del Sistema
last_modified_at: 2018-10-07T01:26:00-06:00
ref: display_on_arduino_of_sib
locale: es
show-avatar: true
categories:
- arduino
tags:
- github
- bash
- arduino
- system
excerpt: "Visualización en Pantalla LCD de Arduino de la Barra de Información del Sistema"
header:
  overlay_image: /assets/images/posts/Display_on_Arduino_of_System_Information_Bar.png
  overlay_filter: 0.5
  show_overlay_excerpt: false
toc: true
toc_sticky: true
---

# Visualización en Arduino de la Barra de Información del Sistema

## <i class="fa fa-eye" aria-hidden="true"></i> Demostración

  - <i class="fas fa-video"></i> Arduino WeMos D1 R2
{% include video id="btFnUsUcHu0" provider="youtube" %}
  
  - <i class="fas fa-draw-polygon"></i> Simulación de Hardware
<iframe width="450" height="450" src="https://www.tinkercad.com/embed/fqruqClfHMR?editbtn=1" frameborder="0" marginwidth="0" marginheight="0" scrolling="no"></iframe>

## <i class="fa fa-info-circle" aria-hidden="true"></i> Introducción

![](/assets/images/posts/gao-assesses-iot-cybersecurity-other-risks-showcase_image-6-a-9926.jpg)

El [Internet de las Cosas](http://www.visualcapitalist.com/what-is-internet-things/) es un concepto que se refiere a una interconexión digital de objetos cotidianos con internet. 

[Para el año de 2020](http://www.visualcapitalist.com/internet-things-2020/), se tiene un pronostico que habran 31 billones de dispositivos y 4 billones de personas. 

![](/assets/images/posts/Massimo_post.png)

Uno de los dispositivos que ha revolucionado el concepto de ***Hazlo tu mismo*** (conocido como DIY, por sus siglas en inglés y significa Do It Yourself) es [Arduino](https://www.arduino.cc/en/Guide/Introduction). 

*Arduino es una plataforma electrónica de código abierto basada en hardware y software fáciles de usar. Las placas Arduino pueden leer entradas (luz en un sensor, un dedo en un botón o un mensaje de Twitter) y convertirla en una salida: activar un motor, encender un LED y publicar algo en línea. Puede decirle a su tarjeta qué debe hacer enviando un conjunto de instrucciones al microcontrolador en la tarjeta.*

![](/assets/images/posts/arduino_board.png)

## <i class="fas fa-bullseye"></i> Objetivo

En este articulo se mostrara como automatizar el despliege de la información que esta almacenada en un archivo de texto, el cual es actualizado por el programa [Barra de Información del Sistema](/es/terminal/SIB_system-information-bar/).

## <i class="fas fa-save"></i> Software

- <i class="fas fa-laptop-code"></i> Entorno de Desarrollo Integrado
  - <i class="fas fa-download"></i> [Arduino IDE](https://www.arduino.cc/en/Main/Software)
- <i class="far fa-object-group"></i> Diseño
  - <i class="fas fa-download"></i> [Fritzing](http://fritzing.org/download/?donation=0)
    - <i class="fas fa-download"></i> [Arduino WeMos D1 R2](https://github.com/mikeipin/Fritzing-Part-WeMos-D1-R2/raw/master/src/WeMos-D1-R2.fzpz)
    - <i class="fas fa-download"></i> [LCD 16x2](http://forum.fritzing.org/uploads/default/original/2X/7/70f90addd7883759e4a0d06a934946c2be8aa6c1.fzpz)
- <i class="fas fa-draw-polygon"></i> Simulación de Hardware
  - <i class="fas fa-external-link-alt"></i> [Tinkercad](https://www.tinkercad.com/)

## <i class="fas fa-microchip"></i> Hardware

- <i class="fas fa-check"></i> Arduino WeMos D1 R2
  ![](/assets/images/posts/wemos_d1_r2.png)
  > **AGOTADO** [Alternativas](http://cdtechnologia.net/search?controller=search&orderby=position&orderway=desc&search_query=arduino+esp8266&submit_search=) en ![http://cdtechnologia.net](/assets/images/posts/cdtechnologia.png) 
- <i class="fas fa-check"></i> LCD 20x4
  ![](/assets/images/posts/lcd_20x4.png)
  > **$15.00** [Pantalla LCD 20x4](http://cdtechnologia.net/arduino/64-pantalla-lcd.html) en ![http://cdtechnologia.net](/assets/images/posts/cdtechnologia.png) 
- <i class="fas fa-check"></i> Cables Macho - Macho
  ![](/assets/images/posts/cables_macho_macho.png)
  > **$5.20** [Cables Macho - Macho](http://cdtechnologia.net/semiconductores/116-cables-hembra-macho.html) en ![http://cdtechnologia.net](/assets/images/posts/cdtechnologia.png) 
- <i class="fas fa-check"></i> Cables Hembra - Hembra
  ![](/assets/images/posts/cables_hembra_hembra.png)
  > **$5.20** [Cables Hembra - Hembra](http://cdtechnologia.net/semiconductores/117-cables-hembra-macho.html) en ![http://cdtechnologia.net](/assets/images/posts/cdtechnologia.png) 

## <i class="fas fa-code"></i> Código

- <i class="fab fa-github"></i> [Repositorio en Github](https://github.com/nelbren/display_on_arduino_of_sib)

## <i class="fa fa-info-circle" aria-hidden="true"></i> Actualización de archivo de texto

1. Instalar el programa [Barra de Información del Sistema](/es/terminal/SIB_system-information-bar/).

2. Crear el siguiente programa (secuencia de comandos):
   ```bash
   $ cat loop.bash
   #!/bin/bash
   # loop.bash
   # v0.0.1 - 2018-10-07 - nelbren.com

   si=/usr/local/npres/bin/system/si.bash
   output=/home/hosting/npr3s/si/si.txt

   while true; do
     $si -n | cut -d"|" -f1 > $output
     sleep 120
   done
   ```

3. Iniciar el programa:
    ```bash
    $ sudo nohup ./loop.bash &
    ```
