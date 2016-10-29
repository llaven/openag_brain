OpenAg Brain
==============

Este repositorio contiene el código que se ejecuta en la tarjeta principal de la computadora de alimentos OpenAg (usualmente se utiliza un Raspberry Pi). El código se ejecuta sobre el sistema operativo [ROS](http://www.ros.org) y utiliza [CouchDB](http://couchdb.apache.org/) para el almacenamiento de datos.


Instalación (Raspberry Pi)
--------------------------

A partir de la siguiente imagen Docker pre-construida se puede ejecutar la base de código necesaria en las máquinas ARM. La mayoría de los usuarios deberían usar esta imagen. Para la configuración y puesta en marcha puedes seguir las siguientes instrucciones que se indican en [este repositorio](https://github.com/OpenAgInitiative/openag_brain_docker_rpi).


Si estas planeando realizar modificaciones en el código sería conveniente instalar el software directamente en tu máquina en vez de ejecutar todo en el contenedor del Docker. Si utilizas Raspberry Pi puedes hacer lo anterior siguiendo las instrucciones en [este repositorio](https://github.com/OpenAgInitiative/openag_brain_install_rpi.git).




Instalación (Manual)
-----------------------------

Si por cualquier razón ni el script para instalar o la imagen Docker te funcionan, puedes installar cada componente del sistema de forma manual. Aquí las instrucciones que debes realizar:

Primero, instala el sistema operativo ROS Indigo en tu máquina. [Aquí las instrucciones para instalar ROS](http://wiki.ros.org/indigo/Installation/). Para máquinas Raspberry Pi [Aquí las instrucciones](http://wiki.ros.org/ROSberryPi/Installing%20ROS%20Indigo%20on%20Raspberry%20Pi).

Segundo, instala la instancia de CochDB. [Instrucciones para instalar CouchDB](http://docs.couchdb.org/en/1.6.1/install/index.html). Si utilizas Ubuntu (13.10 o superior) puedes utilizar el comando 'apt-get install couchdb'.

Tercero, crea un área de trabajo para usar el comando catkin como se describe [aquí](http://wiki.ros.org/catkin/Tutorials/create_a_workspace/) e instala el código desde el repositorio en el área de trabajo con los siguientes comandos:

    cd ~/catkin_ws/src
    git clone https://github.com/OpenAgInitiative/openag_brain.git -b ros
    cd ..
    catkin_make
    catkin_make install
    rosdep install -i openag_brain


Para ejecutar cualquier compando openag, primero debes activar el área de trabajo de catkin de la siguiente manera:

    source ~/catkin_ws/devel/setup.bash

Quinto, debes instalar `platformio`. `platformio` y `rosserial` usan diferentes versiones de `pyseial`, así que instala ambas en 
la misma máquina. `platformio` deberá instalarce en un ambiente virtual de python, aquí te compartimos un script en `openag_brain` para realizarlo:

    rosrun openag_brain install_pio


Ejecutar
--------

Una vez realizado estos pasos (sin utilizar el Docker) y con el área de trabajo de catkin activada, el proyecto puede ser ejecutado con el siguiente comando:


    rosrun openag_brain main
