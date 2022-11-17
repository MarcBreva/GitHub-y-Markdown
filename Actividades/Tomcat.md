# COMO INSTALAR APACHE TOMCAT EN UBUNTU.

## Como instalarlo?

Para instalar Apache Tomcat en ubuntu seguiremos estos pasos:

## Paso 1: Actualizar los repositorios del sistema

> sudo apt update

## Paso 2: Instalación de Java

> sudo apt install openjdk-11-jdk

Despues de esto verificamos la versión que tenemos instalada de Java:

> java -version

## Paso 3: Verificamos la disponibilidad del paquete apache

> sudo apt-cache search tomcat

## Paso 4: Instala Apache Tomcat en Ubuntu

>  sudo apt install tomcat9 tomcat9-admin

Escribimos una S para continuar cuando nos lo pida.

## Paso 5: Comprobamos los puertos

En Ubuntu 22.04, el servidor Apache Tomcat comienza a funcionar automáticamente después de completar la instalación. Para validar esta operación, puede utilizar el comando "ss" para mostrar.

> ss -ltn


El puerto predeterminado para el servidor Apache Tomcat es "8080".

## Paso6: Abrimos puertos para el servidor Apache Tomcat

> sudo ufw allow from any to any port 8080 proto tcp

## Paso 7: Prueba de funcionamiento del servidor Apache Tomcat

Si has seguido los pasos, deberia estar todo listo.
