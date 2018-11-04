---
title: Mini Tutorial - Código de SoloLearn a Github
last_modified_at: 2018-10-25T00:40:00-06:00
ref: mini_tutorial_code_of_sololearn_to_github
locale: es
show-avatar: true
categories:
- tutorial
tags:
- github
- sololearn
- bash
- c
- python
- ruby
- php
excerpt: "Mini Tutorial : Código de SoloLearn a Github"
header:
  overlay_image: /assets/images/posts/sololearn2github.png
  overlay_filter: 0.5
  show_overlay_excerpt: false
  teaser: /assets/images/posts/sololearn2github_teaser.png
toc: true
toc_sticky: true
---

# Mini Tutorial : Código de SoloLearn a Github

# Tabla de contenido
  * [1. Requisitos previos](#1)
  * [2. Crear repositorio en Github](#2)
  * [3. Configurar llave pública y privada](#3)
  * [4. Subir archivos al repositorio](#4)
  * [5. Resultados de cambios](#5)

## 1. Requisitos previos <a name="1"></a>
   - Cuentas en:
     - GitHub
     - SoloLearn

## 2. Crear repositorio en Github <a name="2"></a>
   - Clickear en **New**
     ![](images/new_repository_1.png)
   - Escribe el nombre del repositorio **my_codes_in_sololearn** y clickear en **Create repository**
     ![](images/new_repository_2.png)
   - Seleccionar el método de conexión a GitHub **https** o **ssh**
     ![](images/new_repository_3.png)
  
   > **NOTA:** En el caso de un proyecto propio, aconsejo usar **ssh** con el uso de llaves pública y privada.
  
   ### Al usar https, al obtener cambios del repositorio no se requiere contraseña. Solo es requerida cuando se envíen cambios al repositorio.
    
## 3. Configurar llave pública y privada <a name="3"></a>
   - Crear llaves usando linea de comando (Linux o MAC)

   ```bash
   ssh-keygen -t dsa
   ``` 

   - Crear llaves usando PuTTYgen (Windows)

     ![](images/puttygen.png)

   > Ver instrucciones en [PUTTYGEN - KEY GENERATOR FOR PUTTY ON WINDOWS](https://www.ssh.com/ssh/putty/windows/puttygen)   

  - Asignar llave publica a Github

    - Clickear en **Settings**

      ![](images/ssh_keys_01.png)
       
    - Clickear en **SSH and GPG keys**
      
      ![](images/ssh_keys_02.png) 

    - Clickear en **New SSH key**
      ![](images/ssh_keys_03.png) 
    
    - Copiar la **llave pública** generada al portapapeles
      ![](images/ssh_keys_04.png)
    
    - Pegar la **llave pública** del portapapeles y asignarle un **titulo**, clickear **Add SSH key**
      ![](images/ssh_keys_05.png)

    - Confirmar la asignación con la **contraseña** de la cuenta
      ![](images/ssh_keys_06.png)
 
## 4. Subir archivos al repositorio <a name="4"></a>
   - Por primera vez - [v0.0.1](#v0.0.1)
   
     ```bash
     git init
     git add .
     git commit -m "Mi primera vez!"
     git remote add origin git@github.com:nelbren/my_codes_in_sololearn.git
     git push -u origin master
     ``` 
     ![](images/git_init.png)
   - Por segunda vez - [v0.0.2](#v0.0.2)
   
     ```bash
     git status
     echo shift_cipher.c.bin > .gitignore
     git add .
     git commit -m "Update to v0.0.2"
     git push
     ``` 
     ![](images/git_push_v0.0.2.png)
   - Por tercera vez - [v0.0.3](#v0.0.3)
   
     ```bash
     rm shift_cipher.c.bin
     git status
     git add .
     git commit -m "Update to v0.0.3"
     git push
     ``` 
     ![](images/git_push_v0.0.3.png)     
     
## 5. Resultados de cambios <a name="5"></a> 
   -  [Github](https://github.com) (**control de versiones**) versus [SoloLearn](https://sololearn.com) (**ambiente de ejecución**)

   |Versión|Github         | SoloLearn  |Lenguaje| Descripción|
   |------:|:--------------|:-----------|:------:|:-----------|
   |[0.0.1](https://github.com/nelbren/my_codes_in_sololearn/tree/3bc139e905140e61c67cc7f756efa9df88cdfa90)<a name="v0.0.1"></a>|[heart.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/3bc139e905140e61c67cc7f756efa9df88cdfa90/heart.rb)|[heart.rb\_v0.0.1](https://code.sololearn.com/csr5mCY6joG9/#rb)|Ruby|DisplayAHeart-FirstTry!|
   | |[shift\_cipher.c](https://github.com/nelbren/my_codes_in_sololearn/blob/3bc139e905140e61c67cc7f756efa9df88cdfa90/shift_cipher.c)|[shift\_cipher\_v0.0.1.c](https://code.sololearn.com/cNGVi1MaeYJ6/#c)|C|UseShiftCipherIn28lines|
   | |[shift\_cipher.c_compile.bash](https://github.com/nelbren/my_codes_in_sololearn/blob/3bc139e905140e61c67cc7f756efa9df88cdfa90/shift_cipher.c_compile.bash)| - |Bash|Bash4CompileCProgram|
   | |[shift\_cipher.php](https://github.com/nelbren/my_codes_in_sololearn/blob/3bc139e905140e61c67cc7f756efa9df88cdfa90/shift\_cipher.php)| [shift\_cipher\_v0.0.1.php](https://code.sololearn.com/w5I5CvnY7TOs/#php)|PHP|UseShiftCipherIn13lines|   
   | |[shift\_cipher.py](https://github.com/nelbren/my_codes_in_sololearn/blob/3bc139e905140e61c67cc7f756efa9df88cdfa90/shift_cipher.py)| [shift\_cipher\_v0.0.1.py](https://code.sololearn.com/c2DTb4Eiz4qP/#py)|Python|UseShiftCipherIn10lines|
   | |[shift\_cipher.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/3bc139e905140e61c67cc7f756efa9df88cdfa90/shift_cipher.rb)| [shift\_cipher\_v0.0.1.rb](https://code.sololearn.com/cRNWQ2J4He6o/#rb)|Ruby|UseShiftCipherIn20lines|  
   | |[string\_rotations.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/3bc139e905140e61c67cc7f756efa9df88cdfa90/string_rotations.rb)| [string\_rotations\_v0.0.1.rb](https://code.sololearn.com/cZu14adYWt4Q/#rb)|Ruby|UsingSubstring|    
   |[0.0.2](https://github.com/nelbren/my_codes_in_sololearn/tree/d32be705aae9f67bc0535c747cda2ce562c70734)<a name="v0.0.2"></a>\|[diff](https://github.com/nelbren/my_codes_in_sololearn/commit/d32be705aae9f67bc0535c747cda2ce562c70734#diff-b41048bdbaf2311019d6726e7e2c6912)|[heart.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/d32be705aae9f67bc0535c747cda2ce562c70734/heart.rb)|[heart.rb\_v0.0.2](https://code.sololearn.com/cvgkNxueAUCI/#rb)|Ruby|DisplayAHeart-UseShortenedIf!|
   | |[shift\_cipher.c](https://github.com/nelbren/my_codes_in_sololearn/blob/d32be705aae9f67bc0535c747cda2ce562c70734/shift_cipher.c)|[shift\_cipher\_v0.0.2.c](https://code.sololearn.com/cOmOJZmV2Fsa/#c)|C|UseTernaryOperatorIn15lines|
   | |[shift\_cipher.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/d32be705aae9f67bc0535c747cda2ce562c70734/shift_cipher.rb)| [shift\_cipher\_v0.0.2.rb](https://code.sololearn.com/cxVFVuRK9z79/#rb)|Ruby|UseTernaryOperatorIn13lines|  
   | |[string\_rotations.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/d32be705aae9f67bc0535c747cda2ce562c70734/string_rotations.rb)| [string\_rotations\_v0.0.2.rb](https://code.sololearn.com/cKtyRTM49lLc/#rb)|Ruby|UsingRotate|
   |[0.0.3](https://github.com/nelbren/my_codes_in_sololearn/tree/80414f98e31ffb6b18f198c7c491141597cf0117)<a name="v0.0.3"></a>\|[diff](https://github.com/nelbren/my_codes_in_sololearn/commit/80414f98e31ffb6b18f198c7c491141597cf0117?diff=split)|[heart.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/80414f98e31ffb6b18f198c7c491141597cf0117/heart.rb)|[heart.rb\_v0.0.3](https://code.sololearn.com/c0or8DjaVS2N/#rb)|Ruby|DisplayAHeart-UseShortBlocks1|
   | |[shift\_cipher.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/80414f98e31ffb6b18f198c7c491141597cf0117/shift_cipher.rb)| [shift\_cipher\_v0.0.3.rb](https://code.sololearn.com/cpkKE1Vfo4v0/#rb)|Ruby|UseShorthandOperIn11lines|  
   | |[string\_rotations.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/80414f98e31ffb6b18f198c7c491141597cf0117/string_rotations.rb)| [string\_rotations\_v0.0.3.rb](https://code.sololearn.com/cN3W06aB6fDw/#rb)|Ruby|UsingRegex| 
   |[0.0.4](https://github.com/nelbren/my_codes_in_sololearn/tree/b837bb11609c7159e91972b970354c5fbb5f94af)<a name="v0.0.4"></a>\|[diff](https://github.com/nelbren/my_codes_in_sololearn/commit/b837bb11609c7159e91972b970354c5fbb5f94af#diff-b41048bdbaf2311019d6726e7e2c6912)|[heart.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/b837bb11609c7159e91972b970354c5fbb5f94af/heart.rb)|[heart.rb\_ v0.0.4](https://code.sololearn.com/cjy7I5Qx9B1A/#rb)|Ruby|DisplayAHeart-UseShortBlocks2|
   | |[shift\_cipher.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/b837bb11609c7159e91972b970354c5fbb5f94af/shift_cipher.rb)| [shift\_cipher\_v0.0.4.rb](https://code.sololearn.com/cQN4bIY8A81y/#rb)|Ruby|UseBracketSyntaxIn7lines|  
   | |[string\_rotations.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/b837bb11609c7159e91972b970354c5fbb5f94af/string_rotations.rb)| [string\_rotations\_v0.0.4.rb](https://code.sololearn.com/c382KXDa3l22/#rb)|Ruby|UsingSubstringAndOnlyOneAssing|
   |[0.0.5](https://github.com/nelbren/my_codes_in_sololearn/tree/64ac756c6bbc6f16a9fe4fca47bfdb74a187b86b)<a name="v0.0.4"></a>\|[diff](https://github.com/nelbren/my_codes_in_sololearn/commit/64ac756c6bbc6f16a9fe4fca47bfdb74a187b86b?diff=split)|[heart.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/64ac756c6bbc6f16a9fe4fca47bfdb74a187b86b/heart.rb)|[heart.rb\_ v0.0.5](https://code.sololearn.com/cTcEJusa6pwj/#rb)|Ruby|DisplayAHeart-UseCase2Array|
   | |[string\_rotations.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/64ac756c6bbc6f16a9fe4fca47bfdb74a187b86b/string_rotations.rb)| [string\_rotations\_v0.0.5.rb](https://code.sololearn.com/cwGgkvm4839e/#rb)|Ruby|UsingSubstringAndOnlyOneAssingInside|
   |[0.0.6](https://github.com/nelbren/my_codes_in_sololearn/tree/ced9cee8a6aabedf0301a0d290b2ec52f882232e)<a name="v0.0.6"></a>\|[diff](https://github.com/nelbren/my_codes_in_sololearn/commit/ced9cee8a6aabedf0301a0d290b2ec52f882232e)|[heart.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/ced9cee8a6aabedf0301a0d290b2ec52f882232e/heart.rb)|[heart.rb\_ v0.0.6](https://code.sololearn.com/c86Uo1h25mD2/#rb)|Ruby|DisplayAHeart-UseMultipleAssign|
   | |[string\_rotations.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/ced9cee8a6aabedf0301a0d290b2ec52f882232e/string_rotations.rb)| [string\_rotations\_v0.0.6.rb](https://code.sololearn.com/cWa639epbOuy/#rb)|Ruby|UsingAnCustomFunction|      
   |[0.0.7](https://github.com/nelbren/my_codes_in_sololearn/tree/8b59281b8b81d16404185c31f1a91350d4e11ca2)<a name="v0.0.7"></a>\|[diff](https://github.com/nelbren/my_codes_in_sololearn/commit/8b59281b8b81d16404185c31f1a91350d4e11ca2)|[heart.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/8b59281b8b81d16404185c31f1a91350d4e11ca2/heart.rb)|[heart.rb\_ v0.0.7](https://code.sololearn.com/cwosAyRtEccI/#rb)|Ruby|DisplayAHeart-GlobalVarsToLocal|
   |[0.0.8](https://github.com/nelbren/my_codes_in_sololearn/tree/9f7d1e2928c2fc02ffb1ee55148bc0c9ca90b90a)<a name="v0.0.8"></a>\|[diff](https://github.com/nelbren/my_codes_in_sololearn/commit/9f7d1e2928c2fc02ffb1ee55148bc0c9ca90b90a)|[heart.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/9f7d1e2928c2fc02ffb1ee55148bc0c9ca90b90a/heart.rb)|[heart.rb\_ v0.0.8](https://code.sololearn.com/c1ril3v0sx5e/#rb)|Ruby|DisplayAHeart-Array2NewAssign''|
   |[0.0.9](https://github.com/nelbren/my_codes_in_sololearn/tree/5a3e08868a7b381d43fa04ea857841a13675244c)<a name="v0.0.9"></a>\|[diff](https://github.com/nelbren/my_codes_in_sololearn/commit/5a3e08868a7b381d43fa04ea857841a13675244c)|[heart.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/5a3e08868a7b381d43fa04ea857841a13675244c/heart.rb)|[heart.rb\_v0.0.9](https://code.sololearn.com/c6Ke3H0Avdh0/#rb)|Ruby|DisplayAHeart-ReplaceIfForTwoIf|

<center><strong>Hecho</strong> con <img src="images/icons8-corazones-24.png" alt="drawing" height="18px" style="display: inline-block; vertical-align: middle;"> <strong>por</strong> Martin <a href="https://nelbren.com" style="color: black; text-decoration: none;"><strong>Nelbren</strong></a> Cuellar</center>
