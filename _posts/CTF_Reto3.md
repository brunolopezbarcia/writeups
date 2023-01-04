---
title: 'Reto 3 CTF'
excerpt: 'En la siguiente captura de tráfico hay múltiples conexiones a páginas web. En una de dichas páginas tienes la clave que necesitas.

¿Cuál es la palabra clave?'
coverImage: '/assets/blog/CTF_RETO3/img/cover.png'
date: '2023-01-03T12:35:07.322Z'
author:
  name: Bruno Lopez Barcia
  picture: 'https://avatars.githubusercontent.com/u/78624459?v=4'
ogImage:
  url: ''
---

---

## Presentacion del CTF

En la siguiente captura de tráfico hay múltiples conexiones a páginas web. En una de dichas páginas tienes la clave que necesitas.

¿Cuál es la palabra clave?

## Recursos

[Archivo Captura](/assets/blog/CTF_RETO3/files/captura.pcap)

## Resolucion del CTF

Lo primero que debemos de hacer es tener una maquina __kali linux__ o similares; una vez tenemos la maquina debemos de añadir el archivo que hemos descargado a la maquina.

### Analizar archivo con Wireshark

Lo primero que debemos de hacer es abrir el archivo anterior con wireshark o alguna aplicacion, por el estilo. En nuestro caso usaremos __wireshark__ en su version con GUI

![file captura](/assets/blog/CTF_RETO3/img/1.jpg)

Como podemos ver en la captura anterior en la captura de red hay mucho trafico el cual no nos importa. Como sabemos que la palabra clave esta en una conexion de una pagina web, filtraremos por trafico __HTTP__. Como en la captura siguiente:

![filtrando por http](/assets/blog/CTF_RETO3/img/2.jpg)

Ahora solo debemos de buscar la traza de red donde este la palabra como es una
respuesta del servidor tenemos que buscar que el origen sea distinto a nuestra ip. Sabemos
que nuestra IP es la __192.168.99.4__ debido a que es de donde sale el primer paquete http
registrado. Por lo tanto debemos de buscar una traza con la ip de origen que sea,
__192.168.99.10__. Una vez localizamos el traza de red, debemos de buscar en el protocolo
http, el codigo enviado por el servidor de la pagina y es ahí donde estara la palabra clave.

![Imagen con la solución](/assets/blog/CTF_RETO3/img/3.jpg)

Como podemos ver en el codigo de la respuesta de la pagina web aparece la palabra clave del reto.


## Flag Reto 

La flag de este reto es *__perrito__*

