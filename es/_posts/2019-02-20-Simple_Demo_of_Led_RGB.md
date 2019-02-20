---
title: Demo Simple de Led RGB
last_modified_at: 2018-02-20T18:53:00-06:00
ref: demo_simple_of_led_rgb
locale: es
categories:
- arduino
tags:
- github
- arduino
- led
- rgb
excerpt: "Demo Simple de Led RGB"
header:
header:
  image: /assets/images/posts/Simple_Demo_of_Led_RGB.png
  caption: "Demo Simple de Led RGB en [**Tinkercad**](https://www.tinkercad.com/things/bZejppULsEL-simpledemoofledrgb)"  
  teaser: /assets/images/posts/Simple_Demo_of_Led_RGB_teaser.png
toc: false
toc_sticky: true
classes: wide
author_profile: true
---

# Demo Simple de Led RGB

## <i class="fa fa-eye" aria-hidden="true"></i> Demostración
  
  - <i class="fas fa-draw-polygon"></i> Simulación de Hardware
<iframe width="725" height="725" src="https://www.tinkercad.com/embed/bZejppULsEL?editbtn=1" frameborder="0" marginwidth="0" marginheight="0" scrolling="no"></iframe>  

## <i class="fa fa-info-circle" aria-hidden="true"></i> Introducción

Ver [Introducción del Internet de las Cosas](/es/arduino/Display_on_Arduino_of_SIB) en artículo anterior.

## <i class="fas fa-bullseye"></i> Objetivo

Demostrar como utilizar un led RGB. ¡Eso es todo! 

## <i class="fas fa-save"></i> Software

- <i class="fas fa-draw-polygon"></i> Simulación de Hardware
  - <i class="fas fa-external-link-alt"></i> [Tinkercad](https://www.tinkercad.com/)

## <i class="fas fa-microchip"></i> Hardware

- <i class="fas fa-check"></i> Arduino UNO

  ![](/assets/images/posts/ArduinoUNO_bb.png)

- <i class="fas fa-check"></i> Breadboard mini

  ![](/assets/images/posts/breadboard_mini.png)

- <i class="fas fa-check"></i> Led RGB
  
  ![](/assets/images/posts/led_rgb.png)

- <i class="fas fa-check"></i> Resistencias

  ![](/assets/images/posts/resistor.png)

## <i class="fas fa-code"></i> Código

  - <i class="fas fa-code"></i> **Simple_Demo_of_Led_RGB**

    ```c
    /*
    led_rgb.c 
    v0.0.1 - 2019-02-20 - nelbren.com
    */ 
    int ledRed =   13;
    int ledBlue =  12;
    int ledGreen = 11;

    void setup(void){
      Serial.begin(9600);
      Serial.println("");
    
      pinMode(ledGreen, OUTPUT);
      digitalWrite(ledGreen, HIGH);

      pinMode(ledBlue, OUTPUT);
      digitalWrite(ledBlue, HIGH);

      pinMode(ledRed, OUTPUT);
      digitalWrite(ledRed, HIGH);
    }

    void red(void) {
      digitalWrite(ledRed, HIGH);
      digitalWrite(ledGreen, LOW);
      digitalWrite(ledBlue, LOW);
      Serial.println("  -> RED!");
    }

    void green(void) {
      digitalWrite(ledGreen, HIGH);
      digitalWrite(ledRed, LOW);
      digitalWrite(ledBlue, LOW);
      Serial.println("  -> GREEN!");
    }

    void yellow(void) {
      digitalWrite(ledRed, HIGH);
      digitalWrite(ledGreen, HIGH);
      digitalWrite(ledBlue, LOW);
      Serial.println("  -> YELLOW!");
    }

    void blue(void) {
      digitalWrite(ledBlue, HIGH);
      digitalWrite(ledRed, LOW);
      digitalWrite(ledGreen, LOW);
      Serial.println("  -> BLUE!");
    }

    void white(void) {
      digitalWrite(ledBlue, HIGH);
      digitalWrite(ledRed, HIGH);
      digitalWrite(ledGreen, HIGH);  
      Serial.println("  -> WHITE!");
    }

    void black(void) {
      digitalWrite(ledRed, LOW);
      digitalWrite(ledGreen, LOW);
      digitalWrite(ledBlue, LOW);
      Serial.println("  -> BLACK!");
    }

    void demo(void) {
      Serial.println("DEMO:");
      for(int i = 0; i < 6; i++) {
        switch (i) {
          case 0: red(); break;
          case 1: green(); break;
          case 2: yellow(); break;
          case 3: blue(); break;
          case 4: white(); break;
          case 5: black(); break;
        }
        delay(1000);
      }
      Serial.println("");
    }

    void loop(void){
      demo();
    }
    ```