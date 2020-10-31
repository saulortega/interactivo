# interactivo

**Sistema de gestión telefónica interactiva**

## Instalación

**Antes de empezar:** El sistema operativo debe tener instaladas las utilidades `wget` y `unzip`. Se usarán los puertos 8081 para la gestión web y el 9090 para el AGI. Se creará un directorio `/interactivo` en la raiz del servidor web que servirá como administración web.

**Si está actualizando el binario de una versión previa:**

`rm /opt/interactivo/bin/interactivo`

Reiniciar el servidor o matar el proceso anterior de *interactivo*.

**Si está actualizando la interfaz web de una versión previa:**

`rm /opt/interactivo/web/interactivo.web.zip ; rm -r /srv/www/htdocs/interactivo ; rm -r /opt/interactivo/web/dist`

**1. Opción A - Aplica si el servidor tiene acceso a internet:**

`mkdir /opt/interactivo ; mkdir /opt/interactivo/bd ; mkdir /opt/interactivo/web ; mkdir /opt/interactivo/bin ; mkdir /opt/interactivo/log ; wget -O /opt/interactivo/bin/interactivo https://github.com/saulortega/interactivo/releases/download/v0.3/interactivo ; chmod +x /opt/interactivo/bin/interactivo ; wget -O /opt/interactivo/web/interactivo.web.zip https://github.com/saulortega/interactivo/releases/download/v0.3/interactivo.web.zip ; unzip /opt/interactivo/web/interactivo.web.zip -d /opt/interactivo/web/`

**1. Opción B - Aplica si el servidor no tiene acceso a internet, desde Linux:**

Desde el computador local Linux (cambiar 1.1.1.1 por la IP del servidor. Pedirá contraseña del servidor):

`wget -O ./interactivo https://github.com/saulortega/interactivo/releases/download/v0.3/interactivo ; wget -O ./interactivo.web.zip https://github.com/saulortega/interactivo/releases/download/v0.3/interactivo.web.zip ; scp ./interactivo root@1.1.1.1:/tmp/interactivo ; scp ./interactivo.web.zip root@1.1.1.1:/tmp/interactivo.web.zip ; rm ./interactivo ; rm ./interactivo.web.zip`

Entrar al servidor y ejecutar:

`mkdir /opt/interactivo ; mkdir /opt/interactivo/bd ; mkdir /opt/interactivo/web ; mkdir /opt/interactivo/bin ; mkdir /opt/interactivo/log ; mv /tmp/interactivo /opt/interactivo/bin/interactivo ; mv /tmp/interactivo.web.zip /opt/interactivo/web/interactivo.web.zip ; chmod +x /opt/interactivo/bin/interactivo ; unzip /opt/interactivo/web/interactivo.web.zip -d /opt/interactivo/web/`

**1. Opción C - Aplica si el servidor no tiene acceso a internet, desde Mac:**

Desde el computador local Mac (cambiar 1.1.1.1 por la IP del servidor. Pedirá contraseña del servidor):

`curl -sL https://github.com/saulortega/interactivo/releases/download/v0.3/interactivo -o ./interactivo ; curl -sL https://github.com/saulortega/interactivo/releases/download/v0.3/interactivo.web.zip -o ./interactivo.web.zip ; scp ./interactivo root@1.1.1.1:/tmp/interactivo ; scp ./interactivo.web.zip root@1.1.1.1:/tmp/interactivo.web.zip ; rm ./interactivo ; rm ./interactivo.web.zip`

Entrar al servidor y ejecutar:

`mkdir /opt/interactivo ; mkdir /opt/interactivo/bd ; mkdir /opt/interactivo/web ; mkdir /opt/interactivo/bin ; mkdir /opt/interactivo/log ; mv /tmp/interactivo /opt/interactivo/bin/interactivo ; mv /tmp/interactivo.web.zip /opt/interactivo/web/interactivo.web.zip ; chmod +x /opt/interactivo/bin/interactivo ; unzip /opt/interactivo/web/interactivo.web.zip -d /opt/interactivo/web/`

**2. Opción A - Aplica para Vicidial:**

`mv /opt/interactivo/web/dist /srv/www/htdocs/interactivo ; echo $'#! /bin/sh\n\n/opt/interactivo/bin/interactivo >> /opt/interactivo/log/interactivo.log' > /etc/init.d/interactivo ; chmod +x /etc/init.d/interactivo ; ln -s /etc/init.d/interactivo /etc/rc.d/rc5.d/S70interactivo`

**2. Opción B - Otros:**

*(En otros sistemas operativos puede cambiar las rutas del servidor web y de init.d)*

**3. Reiniciar**

**4. Ingresar a http://ip.ser.vi.dor/interactivo y establecer una contraseña de administración.**

**5. Invocarlo:**

Desde Vicidial, en un Call Menu, llamarlo como un AGI: `http://localhost:9090,NOMBRE_ENTRADA`, donde `NOMBRE_ENTRADA` es el nombre de una entrada establecida en el sistema interactivo. `localhost` puede ser la IP del servidor en caso de que se instale en otro servidor diferente al propio Vicidial.