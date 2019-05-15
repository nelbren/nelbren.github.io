---
title: Use of Java and Git in the Command Line
last_modified_at: 2019-03-20T20:19:00-06:00
ref: use_java_and_git_in_the_command_line
locale: en
show-avatar: true
categories:
- develop
tags:
- git
- github
- bash
- cmd
- java
excerpt: "A quick guide on how to use Java and Git in the Command Line in Windows, Mac or Linux"
header:
  overlay_image: /assets/images/posts/jgit.png
  overlay_filter: 0.7
  show_overlay_excerpt: true
  teaser: /assets/images/posts/jgit_teaser.png
toc: true
toc_sticky: true
author_profile: false
---

## <i class="fas fa-bullseye"></i> Objective

 Learn to use:

  - <i class="fab fa-java"></i> **Java**

    <i class="fa fa-quote-left" aria-hidden="true"></i> 
    *Is a general-purpose programming language that is class-based, object-oriented and designed to have as few implementation dependencies as possible.* 
    <i class="fa fa-quote-right" aria-hidden="true"></i>
    <br>
    <i class="fab fa-wikipedia-w"></i>
    [Wikipedia](https://en.wikipedia.org/wiki/Java_(programming_language)) 
    <i class="fas fa-external-link-square-alt"></i>

  - <i class="fas fa-code-branch"></i> **Git**

    <i class="fa fa-quote-left" aria-hidden="true"></i> 
    *Is a distributed version-control system for tracking changes in source code during software development.* 
    <i class="fa fa-quote-right" aria-hidden="true"></i>
    <br>
    <i class="fab fa-wikipedia-w"></i>
    [Wikipedia](https://en.wikipedia.org/wiki/Git) 
    <i class="fas fa-external-link-square-alt"></i>

  - <i class="fas fa-terminal"></i> **Command Line**

    <i class="fa fa-quote-left" aria-hidden="true"></i> 
    *A command-line interface or command language interpreter (CLI), also known as command-line user interface, console user interface and character user interface (CUI), is a means of interacting with a computer program where the user (or client) issues commands to the program in the form of successive lines of text (command lines).* 
    <i class="fa fa-quote-right" aria-hidden="true"></i>
    <br>
    <i class="fab fa-wikipedia-w"></i>
    [Wikipedia](https://en.wikipedia.org/wiki/Command-line_interface) 
    <i class="fas fa-external-link-square-alt"></i>

## <i class="fa fa-arrow-circle-down" aria-hidden="true"></i> Downloads

  **Links of updated programs to 2019-04-20.**
  {: .notice--danger} 

  - <i class="fab fa-java"></i> [Java](https://www.java.com/es/download/)

    - <i class="fab fa-windows"></i> [Windows](https://download.oracle.com/otn/java/jdk/8u211-b12/478a62b7d4e34b78b671c754eaaf38ab/jdk-8u211-windows-x64.exe)
    - <i class="fab fa-apple"></i> [Mac](https://download.oracle.com/otn/java/jdk/8u211-b12/478a62b7d4e34b78b671c754eaaf38ab/jdk-8u211-macosx-x64.dmg)
    - <i class="fab fa-linux"></i> [Linux](https://download.oracle.com/otn/java/jdk/8u211-b12/478a62b7d4e34b78b671c754eaaf38ab/jdk-8u211-linux-x64.tar.gz)
      - <i class="fas fa-terminal"></i> **Command**
        
        ```bash
        sudo apt install openjdk-8-jdk
        ```

  - <i class="fas fa-code-branch"></i> [Git](https://git-scm.com/downloads)

    - <i class="fab fa-windows"></i> [Windows](https://github.com/git-for-windows/git/releases/download/v2.21.0.windows.1/Git-2.21.0-64-bit.exe) 
    - <i class="fab fa-apple"></i> [Mac](https://sourceforge.net/projects/git-osx-installer/files/git-2.21.0-intel-universal-mavericks.dmg/download?use_mirror=autoselect)
    - <i class="fab fa-linux"></i> [Linux](https://git-scm.com/download/linux)
      - <i class="fas fa-terminal"></i> **Command**
        
        ```bash
        sudo apt-get install git
        ```

  - <i class="fas fa-terminal"></i> Command Line
   
    - <i class="fab fa-windows"></i> **Windows**

      1. Keys: **Windows + R**
      2. <i class="fas fa-terminal"></i> **Command**
         
         ```bash
         Cmd
         ```
    
    - <i class="fab fa-apple"></i> **Mac**
    
      1. Keys: **Shift + Cmd + U**
      2. <i class="fas fa-terminal"></i> **Command**

         ```bash
         Terminal
         ```
    
    - <i class="fab fa-linux"></i> **Linux**
    
      - Locally:
        - Keys: **Alt+F1~7**<br>
        or
        - <i class="fas fa-terminal"></i> **Command**
          
          ```bash
          Terminal
          ```
      - Remotely:
        - <i class="fas fa-terminal"></i> **Command**
          
          ```bash
          ssh ip-address
          ```
          or
          ```bash
          ssh name-of-system
          ```

## <i class="fab fa-java"></i> Java

   - ### <i class="fas fa-code-branch"></i> Version validation

     - <i class="fas fa-terminal"></i> **Command**
       
       ```bash
       javac --version
       ```
     - <i class="fab fa-windows"></i> **Windows**
       ![](/assets/images/posts/javac_version_windows.png)
     - <i class="fab fa-apple"></i> **Mac**
       ![](/assets/images/posts/javac_version_mac.png)
     - <i class="fab fa-linux"></i> **Linux**
       ![](/assets/images/posts/javac_version_linux.png)

  - ### <i class="fas fa-edit"></i> Program creation

    - <i class="fas fa-code"></i> Code (Principal.java)

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

  - ### <i class="fas fa-eye"></i> Program display

    - <i class="fab fa-windows"></i> **Windows**
      ![](/assets/images/posts/show_source_windows.png)
    - <i class="fab fa-apple"></i> **Mac**
      ![](/assets/images/posts/show_source_mac.png)
    - <i class="fab fa-linux"></i> **Linux**
      ![](/assets/images/posts/show_source_linux.png)

  - ### <i class="fas fa-edit"></i> Program modification

    - <i class="fab fa-windows"></i> **Windows**
      - Notepad
    - <i class="fab fa-apple"></i> **Mac** 
      - vi, vim
      - nano
    - <i class="fab fa-linux"></i> **Linux**
      - vi, vim
      - nano

  - ### <i class="fas fa-filter"></i> Program compilation

    - <i class="fab fa-windows"></i> **Windows**
      ![](/assets/images/posts/compile_windows.png)
    - <i class="fab fa-apple"></i> **Mac**
      ![](/assets/images/posts/compile_mac.png)
    - <i class="fab fa-linux"></i> **Linux**
      ![](/assets/images/posts/compile_linux.png)

  - ### <i class="fas fa-microchip"></i> Program execution

    - <i class="fab fa-windows"></i> **Windows**
      ![](/assets/images/posts/run_windows.png)
    - <i class="fab fa-apple"></i> **Mac**
      ![](/assets/images/posts/run_mac.png)
    - <i class="fab fa-linux"></i> **Linux**
      ![](/assets/images/posts/run_linux.png)

## <i class="fab fa-git-square" aria-hiddden="true"></i> Git

  - ### <i class="fas fa-code-branch"></i> Version validation

    - <i class="fas fa-book"></i> [The Command Line](https://git-scm.com/book/en/v2/Getting-Started-The-Command-Line) <i class="fas fa-external-link-square-alt"></i>

    - <i class="fas fa-terminal"></i> **Command**
      
      ```bash
      git --version
      ```
      
    - <i class="fab fa-windows"></i> **Windows**
      ![](/assets/images/posts/git_version_windows.png)
    - <i class="fab fa-apple"></i> **Mac**
      ![](/assets/images/posts/git_version_mac.png)
    - <i class="fab fa-linux"></i> **Linux**
      ![](/assets/images/posts/git_version_linux.png)

  - ### <i class="fas fa-folder"></i> Repository initialization

    - <i class="fas fa-book"></i> [Getting a Git Repository](https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository#_getting_a_repo) <i class="fas fa-external-link-square-alt"></i>

    - <i class="fas fa-terminal"></i> **Command**
      
      ```bash
      git init
      ```
      
    - <i class="fab fa-windows"></i> **Windows** | <i class="fab fa-apple"></i> **Mac** | <i class="fab fa-linux"></i> **Linux**
      ![](/assets/images/posts/git_init_windows.png)

  - ### <i class="fas fa-folder-minus"></i> Ignore include bytecode 

    - <i class="fas fa-book"></i> [Ignoring Files](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository#_ignoring) <i class="fas fa-external-link-square-alt"></i>

    - <i class="fas fa-terminal"></i> **Command**
      
      ```bash
      .gitignore
      ```
      
    - <i class="fab fa-windows"></i> **Windows** | <i class="fab fa-apple"></i> **Mac** | <i class="fab fa-linux"></i> **Linux**
      ![](/assets/images/posts/gitignore_windows.png)

  - ### <i class="fas fa-folder-plus"></i> Adding files

    - <i class="fas fa-book"></i> [Tracking New Files](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository#_tracking_files) <i class="fas fa-external-link-square-alt"></i>

    - <i class="fas fa-terminal"></i> **Command**
      
      ```bash
      git add .
      ```
      
    - <i class="fab fa-windows"></i> **Windows** | <i class="fab fa-apple"></i> **Mac** | <i class="fab fa-linux"></i> **Linux**
      ![](/assets/images/posts/git_add_windows.png)

  - ### <i class="fas fa-toggle-on"></i> Git configuration

    - <i class="fas fa-book"></i> [Your Identity](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup#_your_identity) <i class="fas fa-external-link-square-alt"></i>

    - <i class="fas fa-terminal"></i> **Commands**
      
      ```bash
      git config --global user.email "usuario@correo.com"
      git config --global user.email "Nombre de Usuario"
      ```
      
    - <i class="fab fa-windows"></i> **Windows** | <i class="fab fa-apple"></i> **Mac** | <i class="fab fa-linux"></i> **Linux**
      ![](/assets/images/posts/git_config_windows.png)

  - ### <i class="fas fa-database"></i> Consolidation of changes

    - <i class="fas fa-book"></i> [Committing Your Changes](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository#_committing_changes) <i class="fas fa-external-link-square-alt"></i>

    - <i class="fas fa-terminal"></i> **Command**
      
      ```bash
      git commit -m "Description of the consolidation"
      ```
      
    - <i class="fab fa-windows"></i> **Windows** | <i class="fab fa-apple"></i> **Mac** | <i class="fab fa-linux"></i> **Linux**
      ![](/assets/images/posts/git_commit_windows.png)

  - ### <i class="fas fa-link"></i> Connect repo-local to remote

    - <i class="fas fa-info-circle"></i> **NOTE:** The repository must exist. <br>See example of [Create repository on Github](https://nelbren.com/en/tutorial/Version_Control_of_SoloLearn_in_Github/#2) <i class="fas fa-external-link-square-alt"></i>
      
    - <i class="fas fa-book"></i> [Adding Remote Repositories](https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes#_adding_remote_repositories) <i class="fas fa-external-link-square-alt"></i>
    
    - <i class="fas fa-terminal"></i> **Command**
  :w
    
      ```bash
      git remote add origin https://github.com/USER/PATH.git
      ```
  
    - <i class="fab fa-windows"></i> **Windows** | <i class="fab fa-apple"></i> **Mac** | <i class="fab fa-linux"></i> **Linux**
      ![](/assets/images/posts/git_remote_windows.png)

  - ### <i class="fas fa-external-link-alt"></i> Send changes to the repo-remote

    - <i class="fas fa-book"></i> [Pushing to Your Remotes](https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes#_pushing_remotes) <i class="fas fa-external-link-square-alt"></i>

    - <i class="fas fa-terminal"></i> **Command**
      
      ```bash
      git push -u origin master
      ```
    - <i class="fab fa-windows"></i> **Windows** | <i class="fab fa-apple"></i> **Mac** | <i class="fab fa-linux"></i> **Linux**
      ![](/assets/images/posts/git_push_1de2_windows.png)
      ![](/assets/images/posts/git_push_2de2_windows.png)

  - ### <i class="fa fa-eye"></i> See consolidation in GitHub

    - <i class="fab fa-github"></i> [Repository in GitHub](https://github.com/nelbren/desplegar_321) <i class="fas fa-external-link-square-alt"></i>

    - <i class="fab fa-windows"></i> **Windows** | <i class="fab fa-apple"></i> **Mac** | <i class="fab fa-linux"></i> **Linux**
      ![](/assets/images/posts/github_result.png)

## <i class="fas fa-link" aria-hidden="true"></i> References
  - <i class="fab fa-git-square" aria-hiddden="true"></i> [Pro Git book](https://git-scm.com/book/es/v2) <i class="fas fa-external-link-square-alt"></i>
  - <i class="fab fa-java" aria-hiddden="true"></i> [Java desde Cero](http://mmc.geofisica.unam.mx/cursos/mcst-2007-II/Java/Java%20desde%20Cero.pdf) <i class="fas fa-external-link-square-alt"></i>
  - <i class="fab fa-git-square" aria-hiddden="true"></i> [git - la guía sencilla](http://rogerdudler.github.io/git-guide/index.es.html) <i class="fas fa-external-link-square-alt"></i>
  - <i class="fab fa-java" aria-hiddden="true"></i> [Java Programming Cheatsheet](https://introcs.cs.princeton.edu/java/11cheatsheet/) <i class="fas fa-external-link-square-alt"></i>
  - <i class="fab fa-java" aria-hiddden="true"></i> [Java: manual de referencia, 7ma Edición](ftp://soporte.uson.mx/PUBLICO/02_ING.SISTEMAS.DE.INFORMACION/PPI2/Java%20Manual%20de%20Referencia,%207ma%20Edici%F3n%20-%20Herbert%20Schildt-FREELIBROS.ORG.pdf) <i class="fas fa-external-link-square-alt"></i>

<hr class="small">

![](/assets/images/posts/origin_and_master_merge.jpg)

<hr class="small">

MADE WITH <i class="fas fa-heart"></i> BY **[NELBREN](/en/about/)**
{: .text-center}
{: .notice--success}
