---
title: Visualization in Arduino of SIB with MicroPython
last_modified_at: 2018-12-02T14:40:00-06:00
ref: display_on_arduino_of_sib_micropython
locale: en
categories:
- arduino
tags:
- github
- bash
- arduino
- micropython
- python
- system
excerpt: "Visualization in LCD Screen of Arduino of SIB with MicroPython"
header:
  video:
    id: 5TPSlFpfZX4
    provider: youtube
  teaser: /assets/images/posts/display_arduino_sib_micropython_teaser.png  
toc: false
toc_sticky: true
classes: wide
author_profile: true
---

# Visualization in Arduino of SIB with MicroPython

## <i class="fa fa-info-circle" aria-hidden="true"></i> Introduction

See [Introduction of Internet of the Things](/en/arduino/Display_on_Arduino_of_SIB) in previous article of **Visualization in Arduino of the System Information Bar**

## <i class="fas fa-bullseye"></i> Objective

This article will show how to automate the deployment of information that is stored in a text file on a web page server, in which its updated by the program [System Information Bar](/en/terminal/SIB_system-information-bar/), using [MicroPython](https://micropython.org/).

[![](/assets/images/posts/micropython.png)](https://micropython.org/)

> MicroPython is a lean and efficient implementation of the Python 3 programming language that includes a small subset of the Python standard library and is optimised to run on microcontrollers and in constrained environments.

> The MicroPython pyboard is a compact electronic circuit board that runs MicroPython on the bare metal, giving you a low-level Python operating system that can be used to control all kinds of electronic projects.

> MicroPython is packed full of advanced features such as an interactive prompt, arbitrary precision integers, closures, list comprehension, generators, exception handling and more. Yet it is compact enough to fit and run within just 256k of code space and 16k of RAM.

> MicroPython aims to be as compatible with normal Python as possible to allow you to transfer code with ease from the desktop to a microcontroller or embedded system.

## <i class="fas fa-save"></i> Software

- <i class="fas fa-laptop-code"></i> Tools
  - <i class="fas fa-external-link-alt"></i> [esptool](https://github.com/espressif/esptool) (ESP8266 and ESP32 serial bootloader utility)
  - <i class="fas fa-external-link-alt"></i> [ampy](https://learn.adafruit.com/micropython-basics-load-files-and-run-code/install-ampy) (Adafruit MicroPython tool)

- <i class="far fa-object-group"></i> Design
  - <i class="fas fa-external-link-alt"></i> [Fritzing](http://fritzing.org/download/?donation=0)
    - <i class="fas fa-download"></i> [Arduino ESP8266 NodeMCU](https://raw.githubusercontent.com/roman-minyaylov/nodemcu-v3-fritzing/master/NodeMCUv3%20Lolin.fzpz)
    - <i class="fas fa-download"></i> [LCD 16x2](http://forum.fritzing.org/uploads/default/original/2X/7/70f90addd7883759e4a0d06a934946c2be8aa6c1.fzpz)

- <i class="fas fa-book-reader"></i> Libraries
  - <i class="fas fa-external-link-alt"></i> [esp8266_i2c_lcd.py](https://github.com/dhylands/python_lcd) (lcd_api and i2c_lcd)
  - <i class="fas fa-external-link-alt"></i> [lcd_api.py](https://github.com/dhylands/python_lcd) (lcd_api and i2c_lcd)


## <i class="fas fa-microchip"></i> Hardware

- <i class="fas fa-check"></i> Arduino ESP8266 NodeMCU
  ![](/assets/images/posts/esp8266_nodemcu.png)
  > **$9.49** [ESP8266 NodeMCU](https://www.amazon.com/HiLetgo-Internet-Development-Wireless-Micropython/dp/B010O1G1ES) in ![https://www.amazon.com/](/assets/images/posts/amazon.png) 

- <i class="fas fa-check"></i> LCD 20x4
  ![](/assets/images/posts/lcd_20x4.png)
  > **$15.00** [Display LCD 20x4](http://cdtechnologia.net/arduino/64-pantalla-lcd.html) en ![http://cdtechnologia.net](/assets/images/posts/cdtechnologia.png) 

- <i class="fas fa-check"></i> Cables Female - Female
  ![](/assets/images/posts/cables_hembra_hembra.png)
  > **$5.20** [Cables Female - Female](http://cdtechnologia.net/semiconductores/117-cables-hembra-macho.html) in ![http://cdtechnologia.net](/assets/images/posts/cdtechnologia.png) 

## <i class="fas fa-code"></i> Code

- <i class="fab fa-github"></i> [Repository in Github](https://github.com/nelbren/display_on_arduino_of_sib_with_micropython)
  - <i class="far fa-object-group"></i> Fritzing
  ![](https://raw.githubusercontent.com/nelbren/display_on_arduino_of_sib_with_micropython/master/fritzing/Display%20on%20Arduino%20of%20System%20Information%20Bar%20with%20Micropython%20-%20fritzing.png)
    - <i class="fas fa-download"></i> [Display on Arduino of System Information Bar with Micropython - fritzing.fzz](https://raw.githubusercontent.com/nelbren/display_on_arduino_of_sib_with_micropython/master/fritzing/Display%20on%20Arduino%20of%20System%20Information%20Bar%20with%20Micropython%20-%20fritzing.fzz)
  - <i class="fas fa-laptop-code"></i> ampy
    - <i class="fas fa-sliders-h"></i> Configuration

      |Item|Value|
      |--:|:--|
      |Port|**Assigned by driver**|
      |Speed|115200|
      |SSDI|**Assigned by user**|
      |Password|**Assigned by user**|

    - <i class="fas fa-code"></i> **Display_on_Arduino_of_System_Information_Bar_-_esp8266_nodemcu.py**

      ```python
      # Display_on_Arduino_of_System_Information_Bar_-_esp8266_nodemcu.py
      # v0.0.1 - 2018-11-12 - nelbren.com
      from machine import Pin, I2C
      from esp8266_i2c_lcd import I2cLcd
      import network, utime, urequests as requests
      import wifi

      link = "http://104.251.217.217/si.txt"
      LCD_COLS,LCD_ROWS = 20,4; n = 0
      i2c = I2C(scl=Pin(5), sda=Pin(4), freq=100000)
      lcd = I2cLcd(i2c, 0x27, LCD_ROWS, LCD_COLS)

      def wait_time():
        lcd.blink_cursor_off()
        lcd.move_to(LCD_COLS - 3, LCD_ROWS - 1)
        lcd.putstr('{:03}'.format(n))
        lcd.move_to(LCD_COLS - 1, LCD_ROWS - 1)
        lcd.blink_cursor_on()

      def lcd_print(msg, r = 0):
        lcd.move_to(0, r)
        if len(msg) > LCD_COLS:
          if r >= LCD_ROWS - 1:
            lcd.putstr(msg[0:LCD_COLS - 3] + "...")
          else:
            lcd.putstr(msg[0:LCD_COLS])
            lcd_print(msg[LCD_COLS:], r + 1)
        else:  
          lcd.putstr(msg)

      def setup():
        lcd.backlight_on()
        lcd_print("SSID: " + wifi.SSID, 0)
        nic = network.WLAN(network.STA_IF)
        nic.active(True)
        nic.connect(wifi.SSID, wifi.PASSWORD)
        n = 0
        while not nic.isconnected():
          lcd_print('{:020}'.format(n), 1)
          utime.sleep(1)
          n+=1
        lcd.clear()
        lcd_print("MYIP: " + nic.ifconfig()[0])

      def display_error(msg, nn):
        global n
        lcd.clear()
        lcd_print(msg)
        lcd.backlight_on()
        n = nn

      setup()
      while True:
        wait_time()
        if n <= 0:
          n = 120
          try:
            r = requests.get(link)
          except:
            display_error('Communication error', 5)
            pass
          else:  
            if r.status_code == 200:
              lcd.backlight_on()
              lcd_print(r.text)
              utime.sleep(2)
              if r.text.find('*') == -1: lcd.backlight_off()
              r.close()
            else:      
              display_error('Get failed!', 5)
        else:
          utime.sleep(1)
        n-=1    
      ```

    - <i class="fas fa-download"></i> [Display_on_Arduino_of_System_Information_Bar_-_esp8266_nodemcu.py](https://raw.githubusercontent.com/nelbren/display_on_arduino_of_sib_with_micropython/master/micropython/mysources/main.py)

## <i class="fas fa-keyboard"></i> Use

![](/assets/images/posts/mpi.png)

1. Get
   ~~~bash
   git clone https://github.com/nelbren/display_on_arduino_of_sib_with_micropython.git
   ~~~
  > Output:
  ~~~
  Cloning into 'display_on_arduino_of_sib_with_micropython'...
  remote: Enumerating objects: 33, done.
  remote: Counting objects: 100% (33/33), done.
  remote: Compressing objects: 100% (26/26), done.
  remote: Total 33 (delta 8), reused 32 (delta 7), pack-reused 0
  Unpacking objects: 100% (33/33), done.   
  ~~~

2. Configuration
   ~~~bash
   cd display_on_arduino_of_sib_with_micropython/micropython
   ./mpi.bash
   ~~~

   > Output:
     ~~~
     Please copy 'cfg.bash.example' to 'cfg.bash', and change wifi and port config
     ~~~

   ~~~bash
   cp cfg.bash.example cfg.bash
   ~~~

    > **NOTE:** Change the value of **`port`** in the file **cfg.bash**

3. Flash
   - Erase
    ~~~bash 
    ./mpi.bash -fe
    ~~~ 
    > Output:
      ~~~
      Sure? (Yes/Any=No):
      Yes
      esptool.py v2.5.1
      Serial port /dev/cu.SLAB_USBtoUART
      Connecting........_
      Detecting chip type... ESP8266
      Chip is ESP8266EX
      Features: WiFi
      MAC: 84:f3:eb:XX:XX:XX
      Uploading stub...
      Running stub...
      Stub running...
      Erasing flash (this may take a while)...
      Chip erase completed successfully in 6.9s
      Hard resetting via RTS pin...
      ~~~
   - Upload Firmware
    ~~~bash
    ./mpi.bash -ff
    ~~~
    > Output:
      ~~~
      Sure? (Yes/Any=No):
      Yes
      esptool.py v2.5.1
      Serial port /dev/cu.SLAB_USBtoUART
      Connecting........_
      Detecting chip type... ESP8266
      Chip is ESP8266EX
      Features: WiFi
      MAC: 84:f3:eb:XX:XX:XX
      Uploading stub...
      Running stub...
      Stub running...
      Configuring flash size...
      Auto-detected Flash size: 4MB
      Flash params set to 0x0040
      Compressed 604872 bytes to 394893...
      Wrote 604872 bytes (394893 compressed) at 0x00000000 in 34.9 seconds (effective 138.6 kbit/s)...
      Hash of data verified.
      |
      Leaving...
      Hard resetting via RTS pin...
      ~~~
4. Serial connection
   ~~~bash
   ./mpi.bash -s
   ~~~
  > Output:
    ~~~python
    >>> import os
    >>> print(os.listdir())
    ['boot.py']
    >>> print('hello world!')
    hello world!
    >>> print('for quit of screen press CONTROL+A and type :quit')
    for quit of screen press CONTROL+A and type :quit    
    >>>    
    ~~~

5. Demos
   - List content
    ~~~bash
    ./mpi.bash -al
    ~~~
    > Ouput:
      ~~~
      /boot.py
      ~~~

   - System information
    ~~~bash  
    ./mpi.bash -di
    ~~~
    > Output:
      ~~~
      run mysources/info.py:
        Platform: esp8266
          Version: 3.4.0
          Modules: {'flashbdev': <module 'flashbdev'>}
            Uname: (sysname='esp8266', nodename='esp8266', release='2.2.0-dev(9422289)', version='v1.9.4-8-ga9a3caad0 on 2018-05-11', machine='ESP module with ESP8266')
      MAC address: 84:f3:eb:xx:xx:xx
      Memory free: 24544 bytes
        Frequency: 80000000 hz
      Count 5K ms: 56210
        Frequency: 160000000 hz
      Count 5K ms: 97798
        Frequency: 80000000 hz
      Count 5K ms: 56042
      DONE.  
      ~~~

   - Shift Cipher
    ~~~bash  
    ./mpi.bash -ds
    ~~~
    > Output:
      ~~~
      RUN BOARD:
      ==========
      run mysources/160Mhz.py:
      DONE.
      intento 00: PHHW PH DIWHU WKH WRJD SDUWB
      ...
      intento 24: NFFU NF BGUFS UIF UPHB QBSUZ
      |
      real	0m3.512s
      user	0m0.130s
      sys	0m0.057s
      run mysources/080Mhz.py:
      DONE.
      intento 00: PHHW PH DIWHU WKH WRJD SDUWB
      ...
      intento 24: NFFU NF BGUFS UIF UPHB QBSUZ
      |
      real	0m3.915s
      user	0m0.132s
      sys	0m0.061s
      |
      RUN LOCAL:
      ----------
      intento 00: PHHW PH DIWHU WKH WRJD SDUWB
      ...
      intento 24: NFFU NF BGUFS UIF UPHB QBSUZ
      |
      real	0m0.129s
      user	0m0.021s
      sys	0m0.041s
      ~~~

6. Display on Arduino of System Information Bar with Micropython
   - Configuration of Wifi
     - SSID 
      ~~~bash 
      ./mpi.bash -dm
      ~~~
      > Output:
        ~~~
        Please configure the 'main_ssid' in 'cfg.bash'
        ~~~

        > **NOTE:** Chane the value of **`main_ssid`** in the file **cfg.bash**
     - Password
      ~~~bash 
      ./mpi.bash -dm
      ~~~
      > Output:
        ~~~
        Please configure the 'main_pass' in 'cfg.bash'
        ~~~

        > **NOTE:** Change the value of **`main_pass`** in the file **cfg.bash**
   - Upload the program
    ~~~bash
    ./mpi.bash -dm
    ~~~
    > Output:
      ~~~
      put esp8266_i2c_lcd.py...uploading:
      put resources/esp8266_i2c_lcd.py...DONE.
      put lcd_api.py...uploading:
      put resources/lcd_api.py...DONE.
      put mysources/wifi.py...DONE.
      put mysources/main.py...DONE.
      run mysources/reset.py...DONE.
      ~~~

## <i class="fa fa-info-circle" aria-hidden="true"></i> Update of text file

See [Update of text file](/en/arduino/Display_on_Arduino_of_SIB) in previous article of **Visualization in Arduino of the System Information Bar**