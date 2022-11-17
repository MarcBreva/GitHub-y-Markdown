# Instalación y Configuración de Apache
## Indice

1. Primer paso: Instalar Apache
2. Segundo paso: Ajustar el firewall
3. Tercer Paso: Comprobar su servidor web
4. Cuarto paso: Configurar hosts virtuales


### Introduccion
El servidor HTTP Apache es el más usado del mundo. Ofrece muchas características potentes, entre las que se incluyen módulos que se cargan de forma dinámica, una sólida compatibilidad con medios y amplia integración con otras herramientas de software populares.

### Cuerpo

En esta guía, explicaremos cómo instalar el servidor web Apache en su servidor de Ubuntu 20.04.

## Instalar Apache

Apache está disponible en los repositorios de software predeterminados de Ubuntu, lo que permite instalarlo con las herramientas convencionales de administración de paquetes.

Comencemos actualizando el índice de paquetes locales para que reflejen los últimos cambios anteriores:

> $ sudo apt update

A continuación, instale el paquete apache2:

> $ sudo apt install apache2

Una vez confirmada la instalación, apt instalará Apache y todas las dependencias necesarias.

## Ajustar el firewall

Antes de probar Apache, es necesario modificar los ajustes de firewall para permitir el acceso externo a los puertos web predeterminados.

Enumere los perfiles de aplicación ufw escribiendo lo siguiente:

> $ sudo ufw app list

Como lo indica el resultado, hay tres perfiles disponibles para Apache:

    Apache: este perfil abre solo el puerto 80 (tráfico web normal no cifrado)
    Apache Full: este perfil abre el puerto 80 (tráfico web normal no cifrado) y el puerto 443 (tráfico TLS/SSL cifrado)
    Apache Secure: este perfil abre solo el puerto 443 (tráfico TLS/SSL cifrado)

Se recomienda habilitar el perfil más restrictivo, que de todos modos permitirá el tráfico que configuró. Debido a que en esta guía aún no configuramos SSL para nuestro servidor, solo deberemos permitir el tráfico en el puerto 80:

> $ sudo ufw allow 'Apache'

Puede verificar el cambio escribiendo lo siguiente:

> $ sudo ufw status

## Comprobar su servidor web

Al final del proceso de instalación, Ubuntu 20.04 inicia Apache. El servidor web ya debería estar activo.

Realice una verificación con el sistema init systemd para saber si se encuentra en ejecución el servicio escribiendo lo siguiente:

> $ sudo systemctl status apache2

Puede acceder a la página de destino predeterminada de Apache para confirmar que el software funcione correctamente mediante su dirección IP, Intente escribir esto en la línea de comandos de su servidor:

> $ hostname -I

Obtendrá algunas direcciones separadas por espacios. Puede probar cada uno en el navegador web para determinar si funcionan.

Cuando tenga la dirección IP de su servidor, introdúzcala en la barra de direcciones de su navegador:

> http://your_server_ip

Si sale esta imagen Apache ya funciona correctamente:

![](https://assets.digitalocean.com/articles/how-to-install-lamp-ubuntu-16/small_apache_default.png)

## Configurar hosts virtuales

Después de configurar nuestro sitio web, debemos activar el archivo de configuración de hosts virtuales para habilitarlo. Lo hacemos ejecutando el siguiente comando en el directorio del archivo de configuración:

> sudo a2ensite gci.conf


Deberías ver el siguiente resultado:

> Enabling site gci.
   To activate the new configuration, you need to run:
  service apache2 reload
root@ubuntu-server:/etc/apache2/sites-available#

Reiniciamos apache: 

> service apache2 reload

Y deberia estar listo, escribimos nuestro nombre de host en el navegador y fin.
