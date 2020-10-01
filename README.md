# interactivo

**Sistema de gestión telefónica interactiva**

## Instalación

**Antes de empezar:** Se asume que el sistema operativo tiene instaladas las utilidades para los comandos `wget` y `unzip`. Se usarán los puertos 8081 para la gestión web y el 9090 para el AGI.

1. Ejecutar:

`mkdir /opt/interactivo ; mkdir /opt/interactivo/bd ; mkdir /opt/interactivo/web ; mkdir /opt/interactivo/bin ; mkdir /opt/interactivo/log ; wget -O /opt/interactivo/bin/interactivo https://github.com/saulortega/interactivo/releases/download/v0.1/interactivo ; chmod +x /opt/interactivo/bin/interactivo ; wget -O /opt/interactivo/web/interactivo.web.zip https://github.com/saulortega/interactivo/releases/download/v0.1/interactivo.web.zip ; unzip /opt/interactivo/web/interactivo.web.zip -d /opt/interactivo/web/`

2. Opción A - Aplica para Vicidial:

`mv /opt/interactivo/web/dist /srv/www/htdocs/interactivo ; echo $'#! /bin/sh\n\n/opt/interactivo/bin/interactivo >> /opt/interactivo/log/interactivo.log' > /etc/init.d/interactivo ; chmod +x /etc/init.d/interactivo ; ln -s /etc/init.d/interactivo /etc/rc5.d/S70interactivo`

2. Opción B - Otros:

(En otros sistemas operativos puede cambiar las rutas del servidor web y de init.d)

3. Reiniciar.

4. Ingresar a 1.2.3.4/interactivo y establecer la contraseña inicial.
