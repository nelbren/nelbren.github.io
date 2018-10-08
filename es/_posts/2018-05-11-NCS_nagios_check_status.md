---
title: Estado de comprobación de Nagios
last_modified_at: 2018-05-11T23:22:00-06:00
ref: nagios-check-status
locale: es
categories:
- nagios
tags:
- github
- bash
- ncs
excerpt: "Muestra el estado del servidor y los servicios monitoreados por nagios."
header:
  overlay_image: /assets/images/posts/mincs.png
  overlay_filter: 0.5
  teaser: /assets/images/posts/ncs_teaser.png
toc: true
toc_sticky: true
---

# Nagios Check Status (NCS)

> ![Nagios Check Status (NCS)](/assets/images/posts/nagios_check_status.png)


## ¿Que es? 
Nagios Check Status significa **Estado de comprobación de Nagios**

Es un conjunto de secuencias de comandos de [Bash](https://es.wikipedia.org/wiki/Bash) para obtener un reporte de salida basado en los estados de los servidores y servicios monitoreados por [Nagios](http://www.nagios.org)

## ¿Cómo funciona?
Obtiene la información de Nagios a través de [MK Livestatus](http://mathias-kettner.com/check_mk.html) y la procesa para mostrar el resultado así:

- **Protector de pantalla:** cambia el color de fondo.
- **Alarma:** pronuncia el resumen de estado y/o reproduce un archivo mp3.
- **Terminal:** muestra un reporte por demanda.
- **Correo:** envia un correo electrónico similar al protector de pantalla o terminal.
- **Imagen:** genera una imagen, usando un conjunto de imagenes como tema y marca de tiempo de color.


> Ejemplo de Imagenes que se actualizan cada 5 minutos:  
> Sitio #[01](https://npr3s.com/pelican/)   
> ![](https://npr3s.com/pelican/images/nagios/status_npro-vps-01.png)
> ![](https://npr3s.com/pelican/images/nagios/status_ndev-vps-01.png)  
> Sitio #[02](https://npr3s.net/pelican/)  
> ![](https://npr3s.net/pelican/images/nagios/status_npro-vps-01.png)
> ![](https://npr3s.net/pelican/images/nagios/status_ndev-vps-01.png)

> Ejemplo de como se muestra el Protector de pantalla: 
> ![NCS Protector de Pantalla Ejemplo](/assets/images/posts/ncs.png)

## Sitio oficial de [Nagios Check Status (NCS)](http://ncs.npr3s.com)
