---
title: Arduino ESP8266 NodeMCU in Access Point mode with Web Server to control an RGB Led
last_modified_at: 2018-02-21T10:00:00-06:00
ref: arduino_esp8266_nodemcu_in_mode_access_point_with_web_server_to_control_an_led_rgb
locale: en
categories:
- arduino
tags:
- github
- arduino
- led
- rgb
- web
- server
excerpt: "Arduino ESP8266 NodeMCU in Access Point mode with Web Server to control an RGB Led"
header:
  video:
    id: FTBfNMLqln0
    provider: youtube
  teaser: /assets/images/posts/arduino_esp8266_nodemcu_in_mode_access_point_with_web_server_to_control_an_led_rgb_teaser.png
toc: false
toc_sticky: true
classes: wide
author_profile: true
---

## <i class="fa fa-info-circle" aria-hidden="true"></i> Introduction

See [Introduction of Internet of the Things](/en/arduino/Display_on_Arduino_of_SIB) in previous article.

## <i class="fas fa-bullseye"></i> Objective

Demonstrate how to use the Arduino ESP8266 NodeMCU as an Access Point with Web Server to Control an RGB Led.

## <i class="fas fa-save"></i> Software

- <i class="fas fa-screwdriver"></i> Driver
  - <i class="fas fa-external-link-alt"></i> [CP210x USB to UART Bridge VCP Drivers](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers)

- <i class="fas fa-laptop-code"></i> Integrated Development Environment
  - <i class="fas fa-download"></i> [Arduino IDE](https://www.arduino.cc/en/Main/Software)

## <i class="fas fa-microchip"></i> Hardware

- <i class="fas fa-check"></i> Arduino ESP8266 NodeMCU
  ![](/assets/images/posts/esp8266_nodemcu.png)
  > **$9.49** [ESP8266 NodeMCU](https://www.amazon.com/HiLetgo-Internet-Development-Wireless-Micropython/dp/B010O1G1ES) in ![https://www.amazon.com/](/assets/images/posts/amazon.png)

- <i class="fas fa-check"></i> Breadboard mini

  ![](/assets/images/posts/breadboard_mini.png)

- <i class="fas fa-check"></i> Led RGB
  
  ![](/assets/images/posts/led_rgb.png)

- <i class="fas fa-check"></i> Resistances (330 ohms)

  ![](/assets/images/posts/resistor.png)

## <i class="fas fa-map"></i> Pinout diagram

  ![](/assets/images/posts/ESP_12E.png)

## <i class="fas fa-code"></i> Code

  - <i class="fab fa-github"></i> [Repository in Github](https://github.com/nelbren/arduino_esp8266_nodemcu_in_mode_access_point_with_web_server_to_control_an_led_rgb)
    - <i class="far fa-object-group"></i> Fritzing

    ![](https://github.com/nelbren/arduino_esp8266_nodemcu_in_mode_access_point_with_web_server_to_control_an_led_rgb/raw/master/fritzing/Arduino_ESP8266_NodeMCU_Access_Point_Web_Server_Led_RGB_bb.png)
    
      - <i class="fas fa-download"></i> [Arduino_ESP8266_NodeMCU_Access_Point_Web_Server_Led_RGB.fzz](https://github.com/nelbren/arduino_esp8266_nodemcu_in_mode_access_point_with_web_server_to_control_an_led_rgb/raw/master/fritzing/Arduino_ESP8266_NodeMCU_Access_Point_Web_Server_Led_RGB.fzz)

  - <i class="fas fa-laptop-code"></i> Arduino IDE
    
    - <i class="fas fa-microchip"></i> Board
  
      1. Add url board
       
         ![](/assets/images/posts/esp8266_add_url_of_board.png)

         > http://arduino.esp8266.com/stable/package_esp8266com_index.json

      2. Install board

         ![](/assets/images/posts/esp8266_install_board.png)   

    - <i class="fas fa-sliders-h"></i> Configuration
    
      ![](/assets/images/posts/esp8266_arduino_ide_setup.png)

  - <i class="fas fa-code"></i> **Arduino_ESP8266_NodeMCU_Access_Point_Web_Server_Led_RGB**

    ```c
    /*
    Arduino_ESP8266_NodeMCU_Access_Point_Web_Server_Led_RGB.c 
    v0.0.1 - 2019-02-21 - nelbren.com
    */
    #include <ESP8266WiFi.h>
    #include <WiFiClient.h>
    #include <ESP8266WebServer.h>
    
    const char* ssid = "ESPWebServer";
    const char* password = "12345678";

    WiFiServer server(80);

    int ledRed =   D0; // D0 = GPIO16
    int ledGreen = D1; // D1 = GPIO05
    int ledBlue =  D2; // D2 = GPIO04

    int estado = 0;
    char *msg;

    void setup(void){
      Serial.begin(9600);
      Serial.println("");
      WiFi.mode(WIFI_AP);
      WiFi.softAP(ssid, password);
    
      IPAddress myIP = WiFi.softAPIP(); //Get IP address
      Serial.print("HotSpt IP:");
      Serial.println(myIP);

      pinMode(ledGreen, OUTPUT);
      digitalWrite(ledGreen, HIGH);

      pinMode(ledBlue, OUTPUT);
      digitalWrite(ledBlue, HIGH);

      pinMode(ledRed, OUTPUT);
      digitalWrite(ledRed, HIGH);

      server.begin();
      Serial.println("HTTP server started");
    }

    void red(void) {
      digitalWrite(ledRed, HIGH);
      digitalWrite(ledGreen, LOW);
      digitalWrite(ledBlue, LOW);
      Serial.println("RED!");
    }

    void green(void) {
      digitalWrite(ledGreen, HIGH);
      digitalWrite(ledRed, LOW);
      digitalWrite(ledBlue, LOW);
      Serial.println("GREEN!");
    }

    void yellow(void) {
      digitalWrite(ledRed, HIGH);
      digitalWrite(ledGreen, HIGH);
      digitalWrite(ledBlue, LOW);
      Serial.println("YELLOW!");
    }

    void blue(void) {
      digitalWrite(ledBlue, HIGH);
      digitalWrite(ledRed, LOW);
      digitalWrite(ledGreen, LOW);
      Serial.println("BLUE!");
    }

    void white(void) {
      digitalWrite(ledBlue, HIGH);
      digitalWrite(ledRed, HIGH);
      digitalWrite(ledGreen, HIGH);  
      Serial.println("WHITE!");
    }

    void black(void) {
      digitalWrite(ledRed, LOW);
      digitalWrite(ledGreen, LOW);
      digitalWrite(ledBlue, LOW);
      Serial.println("BLACK!");
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
    }

    void loop(void){
      WiFiClient client = server.available();
      if (!client) {
        return;
      }

      Serial.println("new client");

      while(client.connected() && !client.available())
      {
        delay(1);
      }

      String request = client.readStringUntil('\r');
      Serial.println(request);
      client.flush();

      String mode = "";
      
      if (request.indexOf("/BLACK") != -1) {
        black();
        mode = "BLACK";
      }

      if (request.indexOf("/RED") != -1) {
        red();
        mode = "RED";
      }
      
      if (request.indexOf("/GREEN") != -1) {
        green();
        mode = "GREEN";
      }
      
      if (request.indexOf("/YELLOW") != -1) {
        yellow();
        mode = "YELLOW";
      }
      
      if (request.indexOf("/BLUE") != -1) {
        blue();
        mode = "BLUE";
      }
      
      if (request.indexOf("/WHITE") != -1) {
        white();
        mode = "WHITE";
      }

      if (request.indexOf("/DEMO") != -1) {
        demo();
        mode = "DEMO";
      }

      // Return the response
      client.println("HTTP/1.1 200 OK");
      client.println("Content-Type: text/html");
      client.println(""); // do not forget this one
      client.println("<!DOCTYPE HTML>");
      client.println("<html>");

      //client.println("<head><meta http-equiv='refresh' content='1'></head>");

      if (mode == "") {
        client.println("<h1>MODE: Waiting for instructions from Cyberdyne Systems</h1>");
      } else {  
        client.println("<h1>MODE: ");
        client.println(mode);
        client.println("</h1>");
      }
      client.println("<hr>");
      client.println("<h2>");
      client.println("<a href=\"/RED\">RED</a><br>");
      client.println("<a href=\"/GREEN\">GREEN</a><br>");
      client.println("<a href=\"/YELLOW\">YELLOW</a><br>");
      client.println("<a href=\"/BLUE\">BLUE</a><br>");
      client.println("<a href=\"/WHITE\">WHITE</a><br>");
      client.println("<a href=\"/BLACK\">BLACK</a><br>");
      client.println("<br>");
      client.println("<a href=\"/DEMO\">DEMO</a><br>");
      client.println("</h2>");
      client.println("<hr>");
      client.println("<center>");
      client.println("<h3><a href='https://nelbren.com'>nelbren.com</a>&copy;2019</h3>");
      client.println("</center>");
      client.println("</html>");

      delay(1);
      Serial.println("Client disconnected");
      Serial.println("");
    }
    ```
