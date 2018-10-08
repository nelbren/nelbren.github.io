---
title: Super Tiny Colors Library
last_modified_at: 2018-05-13T17:26:00-06:00
ref: super-tiny-colors
locale: en
show-avatar: true
categories:
- terminal
tags:
- github
- bash
- lib
- ansi
- colors
excerpt: "Little library of colors for bash script"
header:
  overlay_image: /assets/images/posts/super-tiny-colors.png
  overlay_filter: 0.5
  teaser: /assets/images/posts/tiny_colors_teaser.png
toc: true
toc_sticky: true
---

# Super Tiny Colors Library

## <i class="fa fa-question-circle" aria-hidden="true"></i> What is it?
It is an ultra-super small compact and minimalist **library** (*done in 7 code lines*) used for scripts of [Bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell)).

## <i class="fa fa-wrench" aria-hidden="true"></i> How does it work?
This uses variables to set the colors, encapsulating in this way the direct use of the [ANSI color codes](https://misc.flogisoft.com/bash/tip_colors_and_formatting), accomplishing quickness, consolidation and independence.

## <i class="fa fa-eye" aria-hidden="true"></i> Wrapper of ANSI color codes:

- <i class="fa fa-thumbs-down" aria-hidden="true" style="color: red;"></i> Use of ANSI color codes:

  > ```bash
echo -e "\e[40;38;5;82m Hello \e[30;48;5;82m World \e[0m"
  ```
  > Example of command execution:
  > ![](/assets/images/posts/tip_colors_and_formatting.png)

- <i class="fa fa-thumbs-up" aria-hidden="true" style="color: green;"></i> Use of the super-tiny-colors:

  > ```bash
git clone git@github.com:nelbren/npres.git
source /usr/local/npres/lib/super-tiny-colors.bash
echo -e "${nG} Hello ${Iy} World $S"
echo -e "${nG} Hello ${Ig} World $S"
echo -e "${nG} Hello ${Ir} World $S"
echo -e "${nG} Hello ${Iw} World $S"
  ```
  > Example of command execution:
  > ![](/assets/images/posts/uso_de_super-tiny-colors.png)

## <i class="fa fa-arrow-circle-down" aria-hidden="true"></i> How do I obtain it?

- Through [github](https://github.com/nelbren/npres.git) (recommended):
  ```bash
  cd /usr/local/
  git clone https://github.com/nelbren/npres.git
  ```
  > <i class="fa fa-quote-left" aria-hidden="true"></i> *Repository of utilities of support of management of [Debian GNU/Linux](https://debian.org).* <i class="fa fa-quote-right" aria-hidden="true"></i>

- Through wget:
  ```bash
  wget https://raw.githubusercontent.com/nelbren/npres/master/lib/super-tiny-colors.bash
  ```

## <i class="fa fa-info-circle" aria-hidden="true"></i> How are the colors defined?

- Identification of colors:

  **Letter** | **Color**
  --- | ---
  w | white
  m | magenta
  b | blue
  r | red
  g | green
  y | yellow
  a | gray

- Format used by the library:

  Description | Background color | Front color | Example
  --- | --- | --- | --- 
  Normal | black | letter | ![](/assets/images/posts/nr.png)
  Normal **bright** | black | **LETTER** | ![](/assets/images/posts/nG.png)
  Inverse | letter | black | ![](/assets/images/posts/ib.png)
  Inverse ***bright color** | letter | black | ![](/assets/images/posts/Iy.png)
  Inverse **bright white** | **LETTER** | **white** | ![](/assets/images/posts/iA.png)

## <i class="fa fa-eye" aria-hidden="true"></i> Examples:

- examples1
  > ```bash
examples1
  ```
  > Example of command execution:
  > ![](/assets/images/posts/examples1.png) 

- examples2
  > ```bash
examples2
  ```
  > Example of command execution:
  > ![](/assets/images/posts/examples2.png) 
