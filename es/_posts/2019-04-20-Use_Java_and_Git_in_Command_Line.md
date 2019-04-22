---
title: Uso de Java y Git en la Linea de Comando
last_modified_at: 2019-03-20T20:19:00-06:00
ref: use_java_and_git_in_the_command_line
locale: es
show-avatar: true
categories:
- develop
tags:
- github
- bash
- cmd
- java
excerpt: "Una breve guía de cómo utilizar Java y Git en la Linea de Comando en Windows, Mac o Linux"
header:
  overlay_image: /assets/images/posts/jgit.png
  overlay_filter: 0.7
  show_overlay_excerpt: true
  teaser: /assets/images/posts/jgit_teaser.png
toc: true
toc_sticky: true
author_profile: false
---

## <i class="fas fa-bullseye"></i> Objetivo

  Aprender a utilizar:

  - <i class="fab fa-java"></i> **Java**

    <i class="fa fa-quote-left" aria-hidden="true"></i> 
    *Es un lenguaje de programación de propósito general, concurrente, orientado a objetos, que fue diseñado específicamente para tener tan pocas dependencias de implementación como fuera posible.* 
    <i class="fa fa-quote-right" aria-hidden="true"></i>
    <br>
    <i class="fab fa-wikipedia-w"></i>
    [Wikipedia](https://es.wikipedia.org/wiki/Java_(lenguaje_de_programaci%C3%B3n)) 
    <i class="fas fa-external-link-square-alt"></i>

  - <i class="fas fa-code-branch"></i> **Git**

    <i class="fa fa-quote-left" aria-hidden="true"></i> 
    *Es un software de control de versiones diseñado por Linus Torvalds, pensando en la eficiencia y la confiabilidad del mantenimiento de versiones de aplicaciones cuando éstas tienen un gran número de archivos de código fuente.* 
    <i class="fa fa-quote-right" aria-hidden="true"></i>i
    <br>
    <i class="fab fa-wikipedia-w"></i>
    [Wikipedia](https://es.wikipedia.org/wiki/Git) 
    <i class="fas fa-external-link-square-alt"></i>

  - <i class="fas fa-terminal"></i> **Linea de Comando**

    <i class="fa fa-quote-left" aria-hidden="true"></i> 
    *La interfaz de línea de comandos o interfaz de línea de órdenes (en inglés, command-line interface, CLI) es un método que permite a los usuarios dar instrucciones a algún programa informático por medio de una línea de texto simple.* 
    <i class="fa fa-quote-right" aria-hidden="true"></i>
    <br>
    <i class="fab fa-wikipedia-w"></i>
    [Wikipedia](https://es.wikipedia.org/wiki/Interfaz_de_l%C3%ADnea_de_comandos) 
    <i class="fas fa-external-link-square-alt"></i>

## <i class="fa fa-arrow-circle-down" aria-hidden="true"></i> Descargas

  Enlaces de programas actualizados al 2019-04-20:

  - <i class="fas fa-code-branch"></i> [Git](https://git-scm.com/downloads)

    - <i class="fab fa-windows"></i> [Windows](https://github.com/git-for-windows/git/releases/download/v2.21.0.windows.1/Git-2.21.0-64-bit.exe) 
    - <i class="fab fa-apple"></i> [Mac](https://sourceforge.net/projects/git-osx-installer/files/git-2.21.0-intel-universal-mavericks.dmg/download?use_mirror=autoselect)
    - <i class="fab fa-linux"></i> [Linux](https://git-scm.com/download/linux)

      ```bash
      sudo apt-get install git
      ```
  - <i class="fab fa-java"></i> [Java](https://www.java.com/es/download/)

    - <i class="fab fa-windows"></i> [Windows](https://download.oracle.com/otn/java/jdk/8u211-b12/478a62b7d4e34b78b671c754eaaf38ab/jdk-8u211-windows-x64.exe)
    - <i class="fab fa-apple"></i> [Mac](https://download.oracle.com/otn/java/jdk/8u211-b12/478a62b7d4e34b78b671c754eaaf38ab/jdk-8u211-macosx-x64.dmg)
    - <i class="fab fa-linux"></i> [Linux](https://download.oracle.com/otn/java/jdk/8u211-b12/478a62b7d4e34b78b671c754eaaf38ab/jdk-8u211-linux-x64.tar.gz)

      ```bash
      sudo apt install openjdk-8-jdk
      ```
  - <i class="fas fa-terminal"></i> Linea de Comando
   
    - <i class="fab fa-windows"></i> **Windows**

      1. Teclas: **Windows + R**
      2. Ejecutar: **Cmd**

    - <i class="fab fa-apple"></i> **Mac**

      1. Teclas: **Shift + Cmd + U**
      2. Ejecutar: **Terminal**

    - <i class="fab fa-linux"></i> **Linux**

      - Localmente:
        - Teclas: **Alt+F1~7** o Ejecutar: **Terminal**
      - Remotamente:
        - Ejecutar: **ssh nombre**

## <i class="fab fa-java"></i> Java

   - ### <i class="fas fa-code-branch"></i> Validación de versión

     ```bash
     javac --version
      ```
     - <i class="fab fa-windows"></i> **Windows**
       ![](/assets/images/posts/javac_version_windows.png)
     - <i class="fab fa-apple"></i> **Mac**
       ![](/assets/images/posts/javac_version_mac.png)
     - <i class="fab fa-linux"></i> **Linux**
       ![](/assets/images/posts/javac_version_linux.png)

  - ### <i class="fas fa-edit"></i> Creación de programa

    - <i class="fas fa-code"></i> Código (Principal.java)

      ```java
      class Principal {
        private static void dormir() {
          try { Thread.sleep(5000); }
          catch (InterruptedException ex) { 
            Thread.currentThread().interrupt(); 
          }
        }
        public static void main(String[] args) {
          System.out.println("3");
          dormir();
          System.out.println("2");
          dormir();
          System.out.println("1");
        }
      }
      ```
    - <i class="fab fa-windows"></i> **Windows**
      ![](/assets/images/posts/make_source_windows.png)
    - <i class="fab fa-apple"></i> **Mac**
      ![](/assets/images/posts/make_source_mac.png)
    - <i class="fab fa-linux"></i> **Linux**
      ![](/assets/images/posts/make_source_linux.png)

  - ### <i class="fas fa-eye"></i> Visualización de programa

    - <i class="fab fa-windows"></i> **Windows**
      ![](/assets/images/posts/show_source_windows.png)
    - <i class="fab fa-apple"></i> **Mac**
      ![](/assets/images/posts/show_source_mac.png)
    - <i class="fab fa-linux"></i> **Linux**
      ![](/assets/images/posts/show_source_linux.png)

  - ### <i class="fas fa-edit"></i> Modificación de programa

    - <i class="fab fa-windows"></i> **Windows**
      - Notepad
    - <i class="fab fa-apple"></i> **Mac** 
      - vi, vim
      - nano
    - <i class="fab fa-linux"></i> **Linux**
      - vi, vim
      - nano

  - ### <i class="fas fa-filter"></i> Compilación de programa

    - <i class="fab fa-windows"></i> **Windows**
      ![](/assets/images/posts/compile_windows.png)
    - <i class="fab fa-apple"></i> **Mac**
      ![](/assets/images/posts/compile_mac.png)
    - <i class="fab fa-linux"></i> **Linux**
      ![](/assets/images/posts/compile_linux.png)

  - ### <i class="fas fa-microchip"></i> Ejecución de programa

    - <i class="fab fa-windows"></i> **Windows**
      ![](/assets/images/posts/run_windows.png)
    - <i class="fab fa-apple"></i> **Mac**
      ![](/assets/images/posts/run_mac.png)
    - <i class="fab fa-linux"></i> **Linux**
      ![](/assets/images/posts/run_linux.png)

## <i class="fab fa-git-square" aria-hiddden="true"></i> Git

  - ### <i class="fas fa-code-branch"></i> Validación de versión

    - <i class="fas fa-book"></i> [La Línea de Comandos](https://git-scm.com/book/es/v2/Inicio---Sobre-el-Control-de-Versiones-La-L%C3%ADnea-de-Comandos) <i class="fas fa-external-link-square-alt"></i>

    - <i class="fas fa-terminal"></i> **Comando**
      ```bash
      git --version
      ```
 
    - <i class="fab fa-windows"></i> **Windows**
      ![](/assets/images/posts/git_version_windows.png)
    - <i class="fab fa-apple"></i> **Mac**
      ![](/assets/images/posts/git_version_mac.png)
    - <i class="fab fa-linux"></i> **Linux**
      ![](/assets/images/posts/git_version_linux.png)

  - ### <i class="fas fa-folder"></i> Inicialización de repositorio

    - <i class="fas fa-book"></i> [Obteniendo un repositorio Git](https://git-scm.com/book/es/v2/Fundamentos-de-Git-Obteniendo-un-repositorio-Git#r_getting_a_repo) <i class="fas fa-external-link-square-alt"></i>

    - <i class="fas fa-terminal"></i> **Comando**
      ```bash
      git init
      ```

    - <i class="fab fa-windows"></i> **Windows** | <i class="fab fa-apple"></i> **Mac** | <i class="fab fa-linux"></i> **Linux**
      ![](/assets/images/posts/git_init_windows.png)

  - ### <i class="fas fa-folder-minus"></i> Ignorar incluir bytecode 

    - <i class="fas fa-book"></i> [Ignorar archivos](https://git-scm.com/book/es/v2/Fundamentos-de-Git-Guardando-cambios-en-el-Repositorio#r_ignoring) <i class="fas fa-external-link-square-alt"></i>

    - <i class="fas fa-terminal"></i> **Comando**
      ```bash
      .gitignore
      ```

    - <i class="fab fa-windows"></i> **Windows** | <i class="fab fa-apple"></i> **Mac** | <i class="fab fa-linux"></i> **Linux**
      ![](/assets/images/posts/gitignore_windows.png)

  - ### <i class="fas fa-folder-plus"></i> Adición de archivos

    - <i class="fas fa-book"></i> [Rastrear Archivos Nuevos](https://git-scm.com/book/es/v2/Fundamentos-de-Git-Guardando-cambios-en-el-Repositorio#r_tracking_files) <i class="fas fa-external-link-square-alt"></i>

    - <i class="fas fa-terminal"></i> **Comando**
      ```bash
      git add .
      ```

    - <i class="fab fa-windows"></i> **Windows** | <i class="fab fa-apple"></i> **Mac** | <i class="fab fa-linux"></i> **Linux**
      ![](/assets/images/posts/git_add_windows.png)

  - ### <i class="fas fa-database"></i> Configuración de git

    - <i class="fas fa-book"></i> [Tu identidad](https://git-scm.com/book/es/v2/Inicio---Sobre-el-Control-de-Versiones-Configurando-Git-por-primera-vez#_tu_identidad) <i class="fas fa-external-link-square-alt"></i>

    - <i class="fas fa-terminal"></i> **Comandos**
      ```bash
      git config --global user.email "usuario@correo.com"
      git config --global user.email "Nombre de Usuario"
      ```

    - <i class="fab fa-windows"></i> **Windows** | <i class="fab fa-apple"></i> **Mac** | <i class="fab fa-linux"></i> **Linux**
      ![](/assets/images/posts/git_config_windows.png)

  - ### <i class="fas fa-database"></i> Consolidación de cambios

    - <i class="fas fa-book"></i> [Confirmar tus Cambios](https://git-scm.com/book/es/v2/Fundamentos-de-Git-Guardando-cambios-en-el-Repositorio#r_committing_changes) <i class="fas fa-external-link-square-alt"></i>

    - <i class="fas fa-terminal"></i> **Comando**
      ```bash
      git commit -m "Descripción de la consolidación"
      ```

    - <i class="fab fa-windows"></i> **Windows** | <i class="fab fa-apple"></i> **Mac** | <i class="fab fa-linux"></i> **Linux**
      ![](/assets/images/posts/git_commit_windows.png)

  - ### <i class="fas fa-link"></i> Conectar repo-local a remoto

    - <i class="fas fa-info-circle"></i> **NOTA:** El repositorio debe exitir. <br>
      Ver cómo [Crear repositorio en Gibhub](https://nelbren.com/es/tutorial/Version_Control_of_SoloLearn_in_Github/#2) <i class="fas fa-external-link-square-alt"></i>

    - <i class="fas fa-book"></i> [Añadir Repositorios Remotos](https://git-scm.com/book/es/v2/Fundamentos-de-Git-Trabajar-con-Remotos#_a%C3%B1adir_repositorios_remotos) <i class="fas fa-external-link-square-alt"></i>

    - <i class="fas fa-terminal"></i> **Comando**
      ```bash
      git remote add origin https://github.com/USUARIO/RUTA.git
      ```

    - <i class="fab fa-windows"></i> **Windows** | <i class="fab fa-apple"></i> **Mac** | <i class="fab fa-linux"></i> **Linux**
      ![](/assets/images/posts/git_remote_windows.png)

  - ### <i class="fas fa-external-link-alt"></i> Enviar cambios al repo-remoto

    - <i class="fas fa-book"></i> [Enviar a Tus Remotos](https://git-scm.com/book/es/v2/Fundamentos-de-Git-Trabajar-con-Remotos#r_pushing_remotes) <i class="fas fa-external-link-square-alt"></i>

    - <i class="fas fa-terminal"></i> **Comando**
      ```bash
      git push -u origin master
      ```
    - <i class="fab fa-windows"></i> **Windows** | <i class="fab fa-apple"></i> **Mac** | <i class="fab fa-linux"></i> **Linux**
      ![](/assets/images/posts/git_push_1de2_windows.png)
      ![](/assets/images/posts/git_push_2de2_windows.png)

  - ### <i class="fa fa-eye"></i> Ver consolidación en GitHub

    - <i class="fab fa-github"></i> [Repositorio en GitHub](https://github.com/nelbren/desplegar_321) <i class="fas fa-external-link-square-alt"></i>

    - <i class="fab fa-windows"></i> **Windows** | <i class="fab fa-apple"></i> **Mac** | <i class="fab fa-linux"></i> **Linux**
      ![](/assets/images/posts/github_result.png)

## <i class="fas fa-link" aria-hidden="true"></i> Referencias
  - <i class="fab fa-git-square" aria-hiddden="true"></i> [Pro Git book](https://git-scm.com/book/es/v2) <i class="fas fa-external-link-square-alt"></i>
  - <i class="fab fa-java" aria-hiddden="true"></i> [Java desde Cero](http://mmc.geofisica.unam.mx/cursos/mcst-2007-II/Java/Java%20desde%20Cero.pdf) <i class="fas fa-external-link-square-alt"></i>
  - <i class="fab fa-git-square" aria-hiddden="true"></i> [git - la guía sencilla](http://rogerdudler.github.io/git-guide/index.es.html) <i class="fas fa-external-link-square-alt"></i>
  - <i class="fab fa-java" aria-hiddden="true"></i> [Java Programming Cheatsheet](https://introcs.cs.princeton.edu/java/11cheatsheet/) <i class="fas fa-external-link-square-alt"></i>
  - <i class="fab fa-java" aria-hiddden="true"></i> [Java: manual de referencia, 7ma Edición](ftp://soporte.uson.mx/PUBLICO/02_ING.SISTEMAS.DE.INFORMACION/PPI2/Java%20Manual%20de%20Referencia,%207ma%20Edici%F3n%20-%20Herbert%20Schildt-FREELIBROS.ORG.pdf) <i class="fas fa-external-link-square-alt"></i>

<hr class="small">

![](/assets/images/posts/origin_and_master_merge.jpg)

<hr class="small">

MADE WITH <i class="fas fa-heart"></i> BY **[NELBREN](/es/about/)**
{: .text-center}

