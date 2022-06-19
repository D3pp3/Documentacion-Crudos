Zeus-Web
===============

Tener en cuenta que mostraremos como levantar el proyecto en el sistema operativo Linux, que es el que proporciona la empresa. Aunque la empresa brinde soporte para el IDE eclipse la mayoria usamos IntelliJIdea por lo que los ejemplos siempre estaran hechos con ese IDE.

Requerimientos
---------------

Para correr proyecto necesitamos:
    - Java versión 8
    - Maven version 3.6.0 como minimo.
    - IDE IntelliJIdea

Java
---------------

Instalaremos la versión de Java 8 mediante la consola.

.. code-block:: console
    $ sudo apt install openjdk-8-jdk openjdk-8-jre

La ubicación por defecto de la instalación es **/usr/lib/jvm**. Para comenzar a usar esta versi�n ingresaremos en la consola el siguiente comando.

.. code-block:: console
    $ sudo update-alternatives --config java

.. image:: ../img/alternatives.png

Elegimos la opci�n de java 8 y con esto terminamos la instalación de java.

Maven
---------------

Lo más correcto seria tener una carpeta personal para ubicar todos los programas que vallamos necesitando y/o utilizando para mantener un orden y saber donde estan ubicados ya que más adelante necesitaremos saber donde se encuentren por cambios de versión o configuración que vamos a ver mas adelante.

**Ej: /home/mint19/carpetaPersonal/programas/maven**

Por medio de la consola:
.. code-block:: console
    $ cd ~/carpetaPersonal/programas/maven

O por medio de interfaz, lo que mas te guste.

Luego ingresamos a este link,

`Maven <https://maven.apache.org/download.cgi>`_

y buscamos el apartado **Files**

.. image:: ../img/maven.png

de la primera columna clickeamos en la primera fila, se descargara un archivo comprimido, si nos dirigimos **/home/mint19/Descargas** encontraremos el archivo, click derecho extraer aqui y lo movemos a la carpeta que creamos para maven.

Una vez terminado esto debemos agregar al archivo .bashrc que se encuentra por lo general en **/home/mint19/.bashrc**. Esta ruta 

**export PATH=/home/mint19/carpetaPersonal/programas/maven/apache-maven-x.x.x/bin:$PATH**

Por lo general la agregamos al final del archivo. Abrimos una consola y escribimos:

.. code-block:: console
    $ nano .bashrc

Agregamos la linea guardamos con **Ctrl + o** , **ENTER** para confirmar y **Ctrl + x** para salir.

.. code-block:: console
    $ source .bashrc

Con este comando actualizamos los cambios realizados en el archivo de configuración .bashrc, luego escribimos:

.. code-block:: console
    $ mvn -version

Si hicimos todo correctamente nos mostrara la versi�n de maven instalada de la siguiente manera:

.. image:: ../img/mvnVersion.png

Tomcat
---------------

Ingresaremos a este link para descargar la versión 9.

`Tomcat <https://tomcat.apache.org/download-90.cgi>`_

.. image:: ../img/tomcaDownload.png

Damos click en el segundo link tar.gz(pgp, sha512)
    - Nos dirigimos a la carpeta donde descargamos el archivo.
    - Damos click derecho sobre el archivo y seleccionamos **extraer aquí**
    - Creamos una nueva carpeta en nuestra ruta para programas 
    - **/home/mint19/carpetaPersonal/programas/Tomcat**
    - Cortamos la carpeta y la movemos a nuestra carpeta personal creada 

Una vez terminado esto debemos agregar al archivo .bashrc que se encuentra por lo general en **/home/mint19/.bashrc**. Esta ruta 
**export PATH=/home/mint19/carpetaPersonal/programas/Tomcat/apache-tomcat-x.x.xx/bin:$PATH**

Para ingresar a este archivo ingresamos a una terminal y escribimos,

.. code-block:: console
    $ nano .bashrc

Agregamos al final del archivo esta linea y guardamos los cambios.

.. code-block:: console
    $ source .bashrc

Con esto actualizamos los cambios hechos en el archivo .bashrc .

Para verificar que realizamos todo este procedimiento lo correctamente. Nos dirigimos a la carpeta donde tenemos tomcat, entramos a la carpeta bin:
    - Doble click en el archivo **startup.sh**
    - Vamos al navegador e ingresamos la ruta http://localhost:8080
    - Si es correcto nos mostrara la pagina de apache-tomcat
    - Luego damos doble click en el archivo **shutdown.sh**, para parar el servidor.

Levantando Zeus-Web
---------------------

Si ya tenemos el ide instalado y configurado seguimos con este tutorial sino podemos debemos ir al apartado de instalación de IntelliJ

.. toctree::
    IDE

Configurando Proyecto Zeus-Web
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Clonamos el proyecto del repositorio, lo recomendable es organizarnos y armar una carpeta para todos los proyecto que vallamos utilizando de la empresa.
Si realizamos la configuración desde el comienzo podemos crear una nueva carpeta para clonar en ella los proyecto que vallamos utilizando de la empresa.

**/home/mint19/carpetaPersonal/proyectos/zeus-web**

Nos dirigimos a la carpeta.

Abriendo zeus-web en IntelliJ
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: console
    $ cd ~/carpetaPersonal/proyectos/zeus-web

Abrimos IntelliJIDEA y procedemos a abrir el proyecto.
    - file -> New -> Project from existing source...
Y seleccionamos el proyecto que acabamos de clonar.

Mientras termina de indexar el proyecto vamos a ir haciendo algunas configuraciones.
    - file -> Project Structure
    - seleccionamos la versión 8 de java para este proyecto

.. image:: ../img/configuracionJavaIDE.png

Smart Tomcat
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Luego vamos a
    - file -> settings -> plugins
    - Buscamos e instalamos Smart Tomcat

Una vez finalizada la instalación, deberiamos configurar tomcat para levantar zeus-web

.. image:: ../img/configurarSmartTomcat.png

.. image:: ../img/agregarServidor.png

seleccionamos smartTomcat 
    - Name: Colocamos el nombre que nos parezca conveniente
    - Deployment Directory: Se deberia autocompletar pero en el caso que no se autocomplete deberiamos colocar la ruta completa del proyecto más zeus-web/src/main/webapp
    - Content Path: /zeus-web
    - Server Port: 8080
    - Admin Port: 8005
    - VM Options: -Xms512m -Xmx2048m
    - Env Options: No es necesaria su configuración

Heap Size
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Ahora vamos a modificar el heapSize para que no este toda una vida tratando de compilar el proyecto
    - Ctrl + Alt + s
    - Build, Execution, Deployment -> compiler 
        - Modificamos el valor de:
            - Shared build process heap size (Mbytes): 3048

.. image:: ../img/heapSize.png

