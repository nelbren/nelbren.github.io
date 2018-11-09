---
title: Visualización en Arduino de la Barra de Información del Sistema
last_modified_at: 2018-10-07T01:26:00-06:00
ref: display_on_arduino_of_sib
locale: es
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
  teaser: /assets/images/posts/display_arduino_sib_teaser.png
toc: false
toc_sticky: true
classes: wide
author_profile: true
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
  > **$12.28** [Tarjeta Wifi ESP-12E](http://cdtechnologia.net/arduino/346-tarjeta-wifi-esp-12e.html?search_query=Arduino+wifi&results=12) en ![http://cdtechnologia.net](/assets/images/posts/cdtechnologia.png) 
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
  - <i class="far fa-object-group"></i> Fritzing
  ![](https://github.com/nelbren/display_on_arduino_of_sib/raw/master/fritzing/Display%20on%20Arduino%20of%20System%20Information%20Bar%20-%20fritzing.png)
    - <i class="fas fa-download"></i> [Display on Arduino of System Information Bar - fritzing.fzz](https://github.com/nelbren/display_on_arduino_of_sib/raw/master/fritzing/Display%20on%20Arduino%20of%20System%20Information%20Bar%20-%20fritzing.fzz)
  - <i class="fas fa-laptop-code"></i> Arduino IDE
    - <i class="fas fa-sliders-h"></i> Configuración
    ![](/assets/images/posts/arduino_ide_wemos_d1.png)
    - <i class="fas fa-code"></i> **Display_on_Arduino_of_System_Information_Bar_-_WemosD1R2.ino**

    ```c
    // Display on Arduino of System Information Bar - WemosD1R2.c
    // v0.0.1 - 2018-10-07 - nelbren.com

    #include <ESP8266WiFi.h>
    #include "LiquidCrystal_I2C.h"

    const char* host = "104.251.217.217";
    const int   port = 80;
    const char* uri = "/si.txt";
    String httpPacket = "GET " + String(uri) + 
                        " HTTP/1.1\r\n" + 
                        "Host: " + String(host) + "\r\n" + 
                        "Connection: close\r\n\r\n";

    int n = 0;

    const char* ssid = "CHANGE-TO-YOUR-SSID";
    const char* password = "CHANGE-TO-YOUR-PASSWORD";
    const int addr = 0x27, en = 2, rw = 1,rs = 0, d4 = 4, d5 = 5, d6 = 6, d7 = 7;
    LiquidCrystal_I2C lcd(addr, en, rw, rs, d4, d5, d6, d7);
    const int lcd_cols = 20;
    const int lcd_rows = 4;

    void wait_time() {
      String msg = "";
      char buffer[10];
      lcd.noBlink();
      sprintf(buffer, "%03d", n);
      msg.concat(buffer);
      lcd.setCursor(lcd_cols - 3, lcd_rows - 1);
      lcd.print(buffer);
      lcd.setCursor(lcd_cols - 1, lcd_rows - 1);
      lcd.blink();
      Serial.print(buffer); 
      Serial.print(",");
    }

    void lcd_print(String msg, int r = 0) {
      String msg2;
      int wc_x, wc_y;
      int l = msg.length();
      lcd.setCursor(0, r);
      if (l > lcd_cols) {
        if (r >= lcd_rows - 1) {
          msg2 = msg.substring(0, lcd_cols - 3) + "...";     
          lcd.print(msg2);
          wc_x = msg2.length()-1;
          wc_y = r;
        } else {
          lcd.print(msg.substring(0, lcd_cols));
          wc_x = lcd_cols - 1;
          wc_y = r + 1;
          lcd_print(msg.substring(lcd_cols), r + 1);
        }
      } else {
        lcd.print(msg);
        wc_x = msg.length() - 1;
        wc_y = r;
      }
    }

    void setup(void) {
      String msg = "My IP: ";
      Serial.begin(115200); 
      lcd.begin(lcd_cols, lcd_rows);
      lcd.setBacklightPin(3,POSITIVE);
      lcd.setBacklight(LOW);  
      lcd.home();  
      WiFi.begin(ssid, password);
      while (WiFi.status() != WL_CONNECTED) { delay(500); }
      IPAddress myIP = WiFi.localIP();
      msg.concat(myIP.toString());
      lcd.clear();
      lcd_print(msg);
      Serial.println(msg);
    }

    void display_error(String msg, int nn) {
      lcd_print(msg);
      lcd.setBacklight(HIGH);
      n = nn;
    }

    void read_stream(WiFiClient client) {
      unsigned long timeout = millis();
      while (client.available() == 0) {
        if (millis() - timeout > 5000) {
          display_error("Comm failed (2)!", 10);
          client.stop();
          return;
        }
      }   
      if (client.find("\r\n\r\n")){
        delay(5);
        unsigned int i = 0;
        String message = "";
        while (i<60000) {
          if(client.available()) {
            char c = client.read();
            if (c != '\r' && c != '\n') message += c;
            i=0;
          }
          i++;
        }
        Serial.println("\r\n[" + message + "]");
        lcd.setBacklight(HIGH);
        lcd_print(message, 0);
        delay(500);
        if (message.indexOf("*") == -1) lcd.setBacklight(LOW);
        delay(500);
      } else {
        display_error("Comm failed (3)!", 15);
      }
    }

    void loop(void){
      wait_time();
      if ( n <= 0 ) {
        WiFiClient client;
        n = 120;
        if (!client.connect(host, port)) {
          display_error("Comm failed (1)!", 5);
          return;
        }  
        client.print(httpPacket);
        read_stream(client);
      } else {
        delay(1000);
      }
      n--;
    }
    ```
    - <i class="fas fa-download"></i> [Display_on_Arduino_of_System_Information_Bar_-_WemosD1R2.ino](https://raw.githubusercontent.com/nelbren/display_on_arduino_of_sib/master/arduino_ide/Display_on_Arduino_of_System_Information_Bar_-_WemosD1R2/Display_on_Arduino_of_System_Information_Bar_-_WemosD1R2.ino)


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
