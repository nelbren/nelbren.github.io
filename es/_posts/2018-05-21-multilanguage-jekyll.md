---
title: Hacer Jekyll multilingüe
last_modified_at: 2018-05-21T23:10:00-06:00
ref: jekyll-multilingual
locale: es
categories:
- blog
tags:
- jekyll
- github
- multilingual
excerpt: "Manejar dos lenguages en las páginas"
header:
  overlay_image: /assets/images/posts/jekyll-multilingual.png
  overlay_filter: 0.5
toc: true
toc_sticky: true
---

# Hacer Jekyll multilingüe

## <i class="fa fa-question-circle" aria-hidden="true"></i> ¿Qué es esto?
Jekyll tiene un unico procesamiento de lenguage. La idea entonces es, modificar el comportamiento habitual, para que que se manejen dos publicaciones, una en un lenguaje (español) y la correspondiente contraparte en el otro lenguaje (ingles). Al igual que las otras paginas, como ser el indice, las etiquetas, etc.

## <i class="fa fa-globe" aria-hidden="true"></i> Sitios consultados:

  - <i class="fa fa-link" aria-hidden="true"></i> [Multilingual blog with Jekyll 1.5](http://www.nicoespeon.com/en/2014/04/multilingual-blog-with-jekyll-1-5/)

    ![](/assets/images/posts/external_multilingual_blog_with_jekyll_1.5.png)

  - <i class="fa fa-link" aria-hidden="true"></i> [Build a multilingual website with jekyll](http://chocanto.me/2016/04/16/jekyll-multilingual.html)

    ![](/assets/inages/posts/external_build_a_multilingual_website_with_jekyll.png)

  - <i class="fa fa-link" aria-hidden="true"></i> [How to make Jekyll multilingual](http://migueldavid.eu/en/2017/04/04/how-to-make-jekyll-multilingual/)

    ![](/assets/images/posts/external_how_to_make_jekyll_multilingual.png)

  - <i class="fa fa-link" aria-hidden="true"></i> [Making Jekyll multilingual](https://www.sylvaindurand.org/making-jekyll-multilingual/)

    ![](/assets/images/posts/external_making_jekyll_multilingual.png)

## Personalización requerida:

- ### Paso I: Sistema de archivos

  1. *Organizar las publicaciones en directorios por lenguaje:*
  ```bash
  cd nelbren.github.io
  mkdir -p en/_posts/
  mkdir -p es/_posts/
  ```
  <i class="fa fa-eye" aria-hidden="true"></i> *Ejemplo de estructura de directorios en [repositorio de está publicación](https://github.com/nelbren/nelbren.github.io).*

- ### Paso II: Publicaciones

  1. *Mover las publicaciones al directorio del lenguaje primario:*
  ```bash
  mv _post/* es/_post
  ```
  2. *Copiar las publicaciones del lenguaje primario al secundario.*
  ```bash
  cp es/_post/* en/_post
  ```
  3. *Hacer la traducción respectiva del contenido de cada publicación.*
  ```markdown
  ...
  title: Hacer Jekyll multilingüe
                      |
                      v
  title: Make Jekyll multilingual
  ...
  ```
  4. *Adicionar la metada **ref** y **lang** a cada publicación:*
  ```markdown
  ...
  ref: referencia-unica-compartida-por-la-publicación
  lang: lenguaje
  ...
  ```
  <i class="fa fa-eye" aria-hidden="true"></i> *Ejemplo en [repositorio de está publicación](https://github.com/nelbren/nelbren.github.io/blob/master/en/_posts/2018-05-21-multilanguage-jekyll.md).*

- ### Paso III: Páginas

  1. *Copiar **index.html**, **aboutme.md** y **tags.html** al directorio del lenguaje secundario.*
  ```bash
  cp index.html aboutme.md tags.html es/
  ```
  2. *Hacer la traducción respectiva del contenido de cada página.*
  ```markdown
  ...
  title: About me
            |
            v
  title: Sobre mi
  ...
  ```
  {% assign cb2o = '{{' %}
  {% assign cb2c = '}}' %}
  {% assign cbo = '{' %}
  {% assign cbc = '}' %}
  3. *Modificar en el archivo **index.html**: formato de fecha y enlace **tags.html***
  ```html
  ...
    Posted on {{ cb2o }} post.date | date: "%B %-d, %Y" {{ cb2c }}     
                      |
                      v
    Publicado el
    {{ cbo }}% assign w = post.date | date: "%-w" %{{ cbc }}
    {{ cbo }}% case w %{{ cbc }}
      {{ cbo }}% when '0' %{{ cbc }}Domingo
      {{ cbo }}% when '1' %{{ cbc }}Lunes
      {{ cbo }}% when '2' %{{ cbc }}Martes
      {{ cbo }}% when '3' %{{ cbc }}Miercoles
      {{ cbo }}% when '4' %{{ cbc }}Jueves
      {{ cbo }}% when '5' %{{ cbc }}Viernes
      {{ cbo }}% when '6' %{{ cbc }}Sabado
    {{ cbo }}% endcase %{{ cbc }}
    {{ cbo }}% assign m = post.date | date: "%-m" %{{ cbc }}
    {{ cb2o }} post.date | date: "%-d" {{ cb2c }}
    {{ cbo }}% case m %{{ cbc }}
      {{ cbo }}% when '1' %{{ cbc }}Enero
      {{ cbo }}% when '2' %{{ cbc }}Febrero
      {{ cbo }}% when '3' %{{ cbc }}Marzo
      {{ cbo }}% when '4' %{{ cbc }}Abril
      {{ cbo }}% when '5' %{{ cbc }}Mayo
      {{ cbo }}% when '6' %{{ cbc }}Junio
      {{ cbo }}% when '7' %{{ cbc }}Julio
      {{ cbo }}% when '8' %{{ cbc }}Agosto
      {{ cbo }}% when '9' %{{ cbc }}Septiembre
      {{ cbo }}% when '10' %{{ cbc }}Octubre
      {{ cbo }}% when '11' %{{ cbc }}Noviembre
      {{ cbo }}% when '12' %{{ cbc }}Diciembre
    {{ cbo }}% endcase %{{ cbc }}
    del
    {{ cb2o }} post.date | date: "%Y" {{ cb2c }}
  ...
        <a href="{{ cb2o }} site.baseurl {{ cb2c }}/tags#{{ cb2o }}- tag -{{ cb2c }}">{{ cb2o }}- tag -{{ cb2c }}</a>
                                      |
                                      v
        <a href="{{ cb2o }} site.baseurl {{ cb2c }}/es/tags#{{ cb2o }}- tag -{{ cb2c }}">{{ cb2o }}- tag -{{ cb2c }}</a>
  ...
  ```
  4. *Adicionar la metada **ref** y **lang** a cada página:*
  ```markdown
  ...
  ref: referencia-unica-compartida-por-la-página
  lang: lenguaje
  ...
  ```
  <i class="fa fa-eye" aria-hidden="true"></i> *Ejemplo de páginas en directorio **es** en [repositorio de está publicación](https://github.com/nelbren/nelbren.github.io/tree/master/es).*

- ### Paso IV: Diseños

  1. *Modificar en el archivo **_layouts/post.html**: enlace tags, anterior y siguiente*
  ```html
  ...
            <a href="{{ cb2o }} site.baseurl {{ cb2c }}/tags#{{ cb2o }}- tag -{{ cb2c }}">{{ cb2o }}- tag -{{ cb2c }}</a>
                                         |
                                         v
            <a href="{{ cb2o }} site.baseurl {{ cb2c }}/{{ cbo }}% if page.lang == 'es' %{{ cbc }}es/{{ cbo }}% endif %{{ cbc }}tags#{{ cb2o }}- tag -{{ cb2c }}">{{ cb2o }}- tag -{{ cb2c }}</a>
  ...
        <a href="{{ cb2o }} page.previous.url | prepend: site.baseurl | replace: '//', '/' {{ cb2c }}" data-toggle="tooltip" data-placement="top" title="{{ cb2o }}page.previous.title{{ cb2c }}">&larr; Previous Post</a>
                      |
                      v
        {{ cbo }}% for post in site.posts %{{ cbc }}
          {{ cbo }}% if post.lang == page.lang %{{ cbc }}
            {{ cbo }}% if prev %{{ cbc }}
              <a href="{{ cb2o }} post.url {{ cb2c }}" data-toggle="tooltip" data-placement="top" title="{{ cb2o }} post.url.title {{ cb2c }}">&larr; {{ cbo }}% if page.lang == 'en' %{{ cbc }} Previous Post {{ cbo }}% else %{{ cbc }} Publicación Anterior {{ cbo }}% endif %{{ cbc }}</a>
            {{ cbo }}% endif %{{ cbc }}
            {{ cbo }}% assign prev = false %{{ cbc }}
            {{ cbo }}% if post.id == page.id %{{ cbc }}
              {{ cbo }}% assign prev = true %{{ cbc }}
            {{ cbo }}% endif %{{ cbc }}
          {{ cbo }}% endif %{{ cbc }}
        {{ cbo }}% endfor %{{ cbc }}
  ...
        <a href="{{ cb2o }} page.next.url | prepend: site.baseurl | replace: '//', '/' {{ cb2c }}" data-toggle="tooltip" data-placement="top" title="{{ cb2o }}page.next.title{{ cb2c }}">Next Post &rarr;</a>
                                      |
                                      v
        {{ cbo }}% for post in site.posts reversed %{{ cbc }}
          {{ cbo }}% if post.lang == page.lang %{{ cbc }}
            {{ cbo }}% if next %{{ cbc }}
              <a href="{{ cb2o }} post.url {{ cb2c }}" data-toggle="tooltip" data-placement="top" title="{{ cb2o }}post.url.title{{ cb2c }}">{{ cbo }}% if page.lang == 'en' %{{ cbc }} Next Post {{ cbo }}% else %{{ cbc }} Publicación Siguiente {{ cbo }}% endif %{{ cbc }} &rarr;</a>
              {{ cbo }}% break %{{ cbc }}
            {{ cbo }}% endif %{{ cbc }}
            {{ cbo }}% assign next = false %{{ cbc }}
            {{ cbo }}% if post.id == page.id %{{ cbc }}
              {{ cbo }}% assign next = true %{{ cbc }}
            {{ cbo }}% endif %{{ cbc }}
          {{ cbo }}% endif %{{ cbc }}
        {{ cbo }}% endfor %{{ cbc }}
  ...
  ```
  <i class="fa fa-eye" aria-hidden="true"></i> *Ejemplo de **_layouts/post.html** en [repositorio de está publicación](https://github.com/nelbren/nelbren.github.io/blob/master/_layouts/post.html).*
    
  2. *Modificar en el archivo **_includes/header.html**: el formato de fecha:*
  ```html
  ...
    <span class="post-meta">Posted on {{ cb2o }} page.date | date: "%B %-d, %Y" {{ cb2c }}</span>
                                    |
                                    v
      {{ cbo }}% if page.lang == 'en' %{{ cbc }}
      <span class="post-meta">Posted on {{ cb2o }} page.date | date: "%B %-d, %Y" {{ cb2c }}</span>
      {{ cbo }}% else %{{ cbc }}
        <span class="post-meta">Publicado el 
        {{ cbo }}% assign w = page.date | date: "%-w" %{{ cbc }}
        {{ cbo }}% case w %{{ cbc }}
          {{ cbo }}% when '0' %{{ cbc }}Domingo
          {{ cbo }}% when '1' %{{ cbc }}Lunes
          {{ cbo }}% when '2' %{{ cbc }}Martes
          {{ cbo }}% when '3' %{{ cbc }}Miercoles
          {{ cbo }}% when '4' %{{ cbc }}Jueves
          {{ cbo }}% when '5' %{{ cbc }}Viernes
          {{ cbo }}% when '6' %{{ cbc }}Sabado
        {{ cbo }}% endcase %{{ cbc }}
        {{ cbo }}% assign m = page.date | date: "%-m" %{{ cbc }}
        {{ cb2o }} page.date | date: "%-d" {{ cb2c }}
        {{ cbo }}% case m %{{ cbc }}
          {{ cbo }}% when '1' %{{ cbc }}Enero
          {{ cbo }}% when '2' %{{ cbc }}Febrero
          {{ cbo }}% when '3' %{{ cbc }}Marzo
          {{ cbo }}% when '4' %{{ cbc }}Abril
          {{ cbo }}% when '5' %{{ cbc }}Mayo
          {{ cbo }}% when '6' %{{ cbc }}Junio
          {{ cbo }}% when '7' %{{ cbc }}Julio
          {{ cbo }}% when '8' %{{ cbc }}Agosto
          {{ cbo }}% when '9' %{{ cbc }}Septiembre
          {{ cbo }}% when '10' %{{ cbc }}Octubre
          {{ cbo }}% when '11' %{{ cbc }}Noviembre
          {{ cbo }}% when '12' %{{ cbc }}Diciembre
        {{ cbo }}% endcase %{{ cbc }}
        del
        {{ cb2o }} page.date | date: "%Y" {{ cb2c }}
      </span>
      {{ cbo }}% endif %{{ cbc }}
  ...
    <span class="post-meta">Posted on {{ cb2o }} page.date | date: "%B %-d, %Y" {{ cb2c }}</span>    
                                    |
                                    v
      {{ cbo }}% if page.lang == 'en' %{{ cbc }}
      <span class="post-meta">Posted on {{ cb2o }} page.date | date: "%B %-d, %Y" {{ cb2c }}</span>
      {{ cbo }}% else %{{ cbc }}
      <span class="post-meta">Publicado el 
        {{ cbo }}% assign w = page.date | date: "%-w" %{{ cbc }}
        {{ cbo }}% case w %{{ cbc }}
          {{ cbo }}% when '0' %{{ cbc }}Domingo
          {{ cbo }}% when '1' %{{ cbc }}Lunes
          {{ cbo }}% when '2' %{{ cbc }}Martes
          {{ cbo }}% when '3' %{{ cbc }}Miercoles
          {{ cbo }}% when '4' %{{ cbc }}Jueves
          {{ cbo }}% when '5' %{{ cbc }}Viernes
          {{ cbo }}% when '6' %{{ cbc }}Sabado
        {{ cbo }}% endcase %{{ cbc }}              
        {{ cbo }}% assign m = page.date | date: "%-m" %{{ cbc }}
        {{ cb2o }} page.date | date: "%-d" {{ cb2c }}
        {{ cbo }}% case m %{{ cbc }}
          {{ cbo }}% when '1' %{{ cbc }}Enero
          {{ cbo }}% when '2' %{{ cbc }}Febrero
          {{ cbo }}% when '3' %{{ cbc }}Marzo
          {{ cbo }}% when '4' %{{ cbc }}Abril
          {{ cbo }}% when '5' %{{ cbc }}Mayo
          {{ cbo }}% when '6' %{{ cbc }}Junio
          {{ cbo }}% when '7' %{{ cbc }}Julio
          {{ cbo }}% when '8' %{{ cbc }}Agosto
          {{ cbo }}% when '9' %{{ cbc }}Septiembre
          {{ cbo }}% when '10' %{{ cbc }}Octubre
          {{ cbo }}% when '11' %{{ cbc }}Noviembre
          {{ cbo }}% when '12' %{{ cbc }}Diciembre
        {{ cbo }}% endcase %{{ cbc }}
        del
        {{ cb2o }} page.date | date: "%Y" {{ cb2c }}
      </span>
      {{ cbo }}% endif %{{ cbc }}
  ...
  ```
  <i class="fa fa-eye" aria-hidden="true"></i> *Ejemplo de **_includes/header.html** en [repositorio de está publicación](https://github.com/nelbren/nelbren.github.io/blob/master/_includes/header.html).*
  3. *Modificar en el archivo **_includes/nav.html**: el enlace de la página:*
    ```html
    ...
        <a class="navbar-brand" href="{{ cb2o }} site.url {{ cb2c }}">{{ cb2o }} site.title {{ cb2c }}</a>
                                      |
                                      v
        {{ cbo }}% if page.lang == 'en' %{{ cbc }}
        <a class="navbar-brand" href="{{ cb2o }} site.url {{ cb2c }}/">{{ cb2o }} site.title {{ cb2c }}</a>
        {{ cbo }}% else %{{ cbc }}
        <a class="navbar-brand" href="{{ cb2o }} site.url {{ cb2c }}/es">{{ cb2o }} site.title {{ cb2c }}</a>
        {{ cbo }}% endif %{{ cbc }}
    ...
      <ul class="nav navbar-nav navbar-right">
                                      |
                                      v
      <ul class="nav navbar-nav navbar-right">
      {{ cbo }}% for item in site.data.navigation.languages %{{ cbc }}
        {{ cbo }}% if item.language == page.lang %{{ cbc }}
          {{ cbo }}% for link in item.links %{{ cbc }}
            {{ cbo }}% if link[1] contains "http" %{{ cbc }}
              {{ cbo }}% assign url = link[1] %{{ cbc }}
            {{ cbo }}% else %{{ cbc }}
              {{ cbo }}% assign url = link[1] | relative_url %{{ cbc }}
            {{ cbo }}% endif %{{ cbc }}

            {{ cbo }}% if link[1].first %{{ cbc }}
            <li class="navlinks-container">
              <a class="navlinks-parent" href="javascript:void(0)">{{ link[0] }}</a>
              <div class="navlinks-children">
                {{ cbo }}% for childlink in link[1] %{{ cbc }}
                  {{ cbo }}% for linkparts in childlink %{{ cbc }}
                    {{ cbo }}% include navbarlink.html link=linkparts %{{ cbc }}
                  {{ cbo }}% endfor %{{ cbc }}
                {{ cbo }}% endfor %{{ cbc }}
              </div>
            </li>
            {{ cbo }}% else %{{ cbc }}
              <li>
                {{ cbo }}% include navbarlink.html link=link %{{ cbc }}
              </li>
            {{ cbo }}% endif %{{ cbc }}
          
          {{ cbo }}% endfor %{{ cbc }}
        {{ cbo }}% endif %{{ cbc }}
      {{ cbo }}% endfor %{{ cbc }}

      <li>
        {{ cbo }}% assign pages=site.pages | where: "ref", page.ref %{{ cbc }}
        {{ cbo }}% assign n_pages=pages | size %{{ cbc }}
        {{ cbo }}% if n_pages > 0 %{{ cbc }}
          {{ cbo }}% for page2 in pages %{{ cbc }}
            {{ cbo }}% if page2.lang != page.lang %{{ cbc }}
            <a href="{{ page2.url }}">{{ cbo }}% if page2.lang == 'en' %{{ cbc }}<i class="fa fa-language" aria-hidden="true"></i> English{{ cbo }}% else %{{ cbc }}<i class="fa fa-language" aria-hidden="true"></i> Español{{ cbo }}% endif %{{ cbc }}</a>
            {{ cbo }}% break %{{ cbc }}
            {{ cbo }}% endif %{{ cbc }}
          {{ cbo }}% endfor %{{ cbc }}
        {{ cbo }}% else %{{ cbc }}
          {{ cbo }}% assign posts=site.posts | where: "ref", page.ref %{{ cbc }}
          {{ cbo }}% for post2 in posts %{{ cbc }}
            {{ cbo }}% if post2.lang != page.lang %{{ cbc }}
              <a href="{{ post2.url }}">{{ cbo }}% if post2.lang == 'en' %{{ cbc }}<i class="fa fa-language" aria-hidden="true"></i> English{{ cbo }}% else %{{ cbc }}<i class="fa fa-language" aria-hidden="true"></i> Español{{ cbo }}% endif %{{ cbc }}</a>
            {{ cbo }}% endif %{{ cbc }}
          {{ cbo }}% endfor %{{ cbc }}
        {{ cbo }}% endif %{{ cbc }}
      </li>
    ...
    ```
    <i class="fa fa-eye" aria-hidden="true"></i> *Ejemplo de **_includes/nav.html** en [repositorio de está publicación](https://github.com/nelbren/nelbren.github.io/blob/master/_includes/nav.html).*

- ### Paso V: Configuración

  1. *Crear el archivo **_data/navigation.yml** con el contenido:*
  ```markdown
  languages:
    - language: "en"
      links:
        About me: aboutme
        projects:
          - Nagios Check Status (NCS): en/nagios/2018/05/10/NCS_nagios_check_status
    - language: "es"
      links:
        Sobre mi: es/aboutme
        proyectos:
          - Estado de comprobación de Nagios (NCS): es/nagios/2018/05/10/NCS_nagios_check_status
  ```
  <i class="fa fa-eye" aria-hidden="true"></i> *Ejemplo de **_layouts/post.html** en [repositorio de está publicación](https://github.com/nelbren/nelbren.github.io/blob/master/_data/navigation.yml).*
    
  2. *Modificar en el archivo **_config.yml**:*
  ```markdown
  ...
  url: "http://nelbren.github.io"
                     |
                     v
  url: ""                                     
  ...
  ```
  <i class="fa fa-eye" aria-hidden="true"></i> *Ejemplo de **_config.yml** en [repositorio de está publicación](https://github.com/nelbren/nelbren.github.io/blob/master/_config.yml).*
