---
title: Visualization in Arduino of the System Information Bar
last_modified_at: 2018-10-07T01:26:00-06:00
ref: display_on_arduino_of_sib
locale: en
show-avatar: true 
categories: 
- arduino
tags: 
- github 
- bash 
- arduino 
- system 
excerpt: "Visualization in a LCD Screen of Arduino of the System Information Bar"
header:
  overlay_image: /assets/images/posts/Display_on_Arduino_of_System_Information_Bar.png
  overlay_filter: 0.5 
  show_overlay_excerpt: false
  teaser: /assets/images/posts/display_arduino_sib_teaser.png
toc: true 
toc_sticky: true
---      

# Visualization in Arduino of the System Information Bar 

## <i class="fa fa-eye" aria-hidden="true"></i> Demonstration 

- <i class="fas fa-video"></i> Arduino WeMos D1 R2
  {% include video id="btFnUsUcHu0" provider="youtube" %}

- <i class="fas fa-draw-polygon"></i> Hardware Simulation

<iframe width="450" height="450" src="https://www.tinkercad.com/embed/fqruqClfHMR?editbtn=1" frameborder="0" marginwidth="0" marginheight="0" scrolling="no"></iframe>

## <i class="fa fa-info-circle" aria-hidden="true"></i> Introduction 

![](/assets/images/posts/gao-assesses-iot-cybersecurity-other-risks-showcase_image-6-a-9926.jpg)

The [Internet of things](http://www.visualcapitalist.com/what-is-internet-things/) is a concept which refers to a digital interconnection of daily objects with internet.

[For the year of 2020](http://www.visualcapitalist.com/internet-things-2020/), there is a forecast there will be 31 billón divices and 4 billion people. 

![](/assets/images/posts/Massimo_post.png)       
One of the divices which has revolucionized the concept of **Do it yourself** (known as DIY) is [Arduino](https://www.arduino.cc/en/Guide/Introduction).

*Arduino is an electric platform of open code based in hardware and software easy to use. The plates Arduino can read entries (light in a sensor, a finger in a bottom or a Twitter message) and turn it into an exit: activate a motor, turn on an LED, and publish something online. You can tell your card that it must send a set of instructions to the microcontroller on the card.*

![](/assets/images/posts/arduino_board.png)

## <i class="fas fa-bullseye"></i> Objective

This article will show how to automate the deployment of information that is stored in a text file, in which its updated by the program [System Information Bar](/en/terminal/SIB_system-information-bar/).

## <i class="fas fa-save"></i> Software

- <i class="fas fa-laptop-code"></i> Integrated Development Environment
   - <i class="fas fa-download"></i> [Arduino IDE](https://www.arduino.cc/en/Main/Software)
- <i class="far fa-object-group"></i> Design
  - <i class="fas fa-download"></i> [Fritzing](http://fritzing.org/download/?donation=0)
    - <i class="fas fa-download"></i> [Arduino WeMos D1 R2](https://github.com/mikeipin/Fritzing-Part-WeMos-D1-R2/raw/master/src/WeMosD1-R2.fzpz)
    - <i class="fas fa-download"></i> [LCD 16x2](http://forum.fritzing.org/uploads/default/original/2X/7/70f90addd7883759e4a0d06a934946c2be8aa6c1.fzpz)
- <i class="fas fa-draw-polygon"></i> Hardware Simulation
  - <i class="fas fa-external-link-alt"></i> [Tinkercad](https://www.tinkercad.com/)

## <i class="fas fa-microchip"></i> Hardware

- <i class="fas fa-check"></i> Arduino WeMos D1 R2
  ![](/assets/images/posts/wemos_d1_r2.png        )
  > **SOLD OUT** [Alternatives](http://cdtechnologia.net/search?controller=search&orderby=position&orderway=desc&search_query=arduino+esp8266&submit_search=) in ![http://cdtechnologia.net](/assets/images/posts/cdtechnologia.png)
- <i class="fas fa-check"></i> LCD 20x4         
  ![](/assets/images/posts/lcd_20x4.png)
  > **$15.00** [Display LCD 20x4](http://cdtechnologia.net/arduino/64-pantalla-lcd.html) in ![http://cdtechnologia.net](/assets/images/posts/cdtechnologia.png)
- <i class="fas fa-check"></i> Cables Male - Male
  ![](/assets/images/posts/cables_macho_macho.png)
  > **$5.20** [Cables Male - Male](http://cdtechnologia.net/semiconductores/116-cables-hembra-macho.html) in ![http://cdtechnologia.net](/assets/images/posts/cdtechnologia.png)
- <i class="fas fa-check"></i> Cables Female - Female 
  ![](/assets/images/posts/cables_hembra_hembra.png)
  > **$5.20** [Cables Female - Female](http://cdtechnologia.net/semiconductores/117-cables-hembra-macho.html) in ![http://cdtechnologia.net](/assets/images/posts/cdtechnologia.png)


## Code

- [Repository in Github](https://github.com/nelbren/display_on_arduino_of_sib)

## Update of text file

1. Install the program [System Information Bar](/en/terminal/SIB_system-information-bar/).

2. Create the following program (sequence of commands):
   ```bash  
   $ cat loop.bash
   #!/bin/bash
   # loop.bash 
   # v0.0.1 - 2018-10-07 - nelbren.com
   si=/usr/local/npres/bin/system/si.bash output=/home/hosting/npr3s/si/si.txt
   while true; do
     $si -n | cut -d"|" -f1 > $output
     sleep 120
   done
   ```

3. Start the program:
   ```bash
   $ sudo nohup ./loop.bash &
   ``` 
