---
title: 'Reto 2 CTF'
excerpt: 'En este CTF tenemos que averiguar la palabra clave que esta contenida en un fichero comprimido en un zip; este zip esta corrupto, por lo que debemos de primero de corregir el ZIP'
coverImage: ''
date: '2022-11-16T12:35:07.322Z'
author:
  name: Bruno Lopez Barcia
  picture: 'https://avatars.githubusercontent.com/u/78624459?v=4'
ogImage:
  url: '/assets/blog/CTF_RETO2/1.jpeg'
---

---

## Presentacion del CTF

En este CTF tenemos que averiguar la palabra clave que esta contenida en un fichero comprimido en un zip; este zip esta corrupto, por lo que debemos de primero de corregir el ZIP

## Recursos

[Archivo Notese](/assets/blog/CTF_RETO2/files/notese)

## Resolucion del CTF

Lo primero que debemos de hacer es tener una maquina __kali linux__ o similares; una vez tenemos la maquina debemos de añadir el archivo que hemos descargado a la maquina.

### Descorromper el archivo

Ahora para comprobar el tipo de archivo utilizaremos el comando __file notese__, esto nos permite saber datos acerca del archivo que le pasamos como parametro.

![file notese](/assets/blog/CTF_RETO2/img/1.jpeg)

Como podemos ver en la captura anterior el archivo es un zip. Tras buscar información he encontrado la herramienta _hexedit_ que permite modificar los datos de un archivo en hexadecimal y con esto podemos solventar el error que nos da el archivo. Para instalarla utilizaremos el comando **sudo apt install hexedit**.

![sudo apt install hexedit](/assets/blog/CTF_RETO2/img/2.jpeg)

Una vez instalado utilizamos el comando **hexedit notese** y nos mostrara los datos en hexadecimal

Aqui podeis ver la imagen con los valores **MAL**:

![Imagen valores mal](/assets/blog/CTF_RETO2/img/3.jpeg)

Y aqui se muestra la imagen con los valores **correctos**:

![Imagen valores correctos](/assets/blog/CTF_RETO2/img/4.jpeg)


Como se puede comprobar los datos al principio estaban como __50 4B 03 0A__ y nosotros debemos de ponerlos como __50 4B 03 04__. 

Ahora si volvemos a ejecutar el comando __file notese__ como podemos comprobar cambia la salida del comando.

![file notese_2](/assets/blog/CTF_RETO2/img/5.jpeg)

### Romper la password del archivo

Como ya tenemos corregido el archivo ya podemos pasar al paso de romper la contraseña en nuestro caso podemos usaremos _john_, para obtener el hash de la contraseña del zip utilizaremos el comando __zip2john notese__. Este hash que nos saldra es el que luego romperemos.

![zip2john notese](/assets/blog/CTF_RETO2/img/6.jpeg)

Este hash que acabamos de conseguir, yo soy partidario de introducir todos los hash y usuarios en archivos, por lo que es lo que haremos. Una vez añadido el hash a un archivo utilizaremos el comando __john claves__. Este comando rompera el hash, no es necesario indicarle ningun diccionario debido a que con esta comando john utilizara el diccionario por defecto que trae configurado.

![john claves](/assets/blog/CTF_RETO2/img/7.jpeg)

Una vez que tenemos la clave podemos ya unzipear el archivo con el comando **unzip notese** y nos pedira introducir la clave que acabamos de consegir. La introducimos y nos sacara el archivo que tiene la palabra secreta. Utilizaremos el comando __cat notese__ y ya podemos ver la palabra clave. 

![cat notese](/assets/blog/CTF_RETO2/img/8.jpeg) 



## Flag Reto 

La flag de este reto es *__gatito__*

