Cómo instalar JetPack en la Nvidia Jetson
==========================================

## 1. Instalar NVIDIA SDK Manager en tu computador
* El SDK Manager puede descargarse desde la web de NVIDIA (https://developer.nvidia.com/embedded/jetpack). Es necesario tener una cuenta creada del programa de desarrolladores de NVIDIA, a la que tendrás que acceder antes de iniciar la descarga. El SDK Manager requiere un PC con Ubuntu Desktop 16.04 o 18.04 (al menos a la fecha en que escribo esto).

* Una vez se haya descargado el paquete de instalación (.deb), puede instalarse usando
```
sudo dpkg -i sdkmanager_1.0.1-5538_amd64.deb
```
* Cuando se haya instalado el programa, este puede abrirse usando el comando `sdkmanager` en un emulador de terminal.

## 2. Instalar JetPack mediante SDK Manager
* En [este enlace](https://docs.nvidia.com/sdk-manager/install-with-sdkm-jetson/index.html) pueden encontrarse los pasos a seguir para la instalación de JetPack. La descarga de los componentes tomará un tiempo.

* Cuando el instalador este listo, abrirá una ventana indicando que es momento de flashear el SO en la Jetson. El procedimiento varía un poco dependiendo del modelo, pero por lo general es necesario poner el dispositivo en modo recovery. El procedimiento para eso es el siguiente:
1. Apagar el dispositivo. Desconectar el conector de alimentación para asegurarse que la Jetson esté apagada y no suspendida. 
2. Conectar el cable USB al puerto Recovery de la Jetson (USB type-C) mientras el otro extremo se conecta al PC.
3. Conectar la alimentación.
4. Presionar el botón de encendido para prender la Jetson.
5. Presionar y mantener el botón FORCE RECOVERY, mientras se presiona el botón RESET; esperar dos segundos después de soltar este botón para soltar el botón FORCE RECOVERY.
6. Cuando la Jetson esté en modo recovery, el comando `lsusb` mostrará en una línea "NVidia Corp".

* Si todos los componentes en el dispositivo (Target components) se instalan exitosamente, la instalación de JetPack está completa. Puede que falle la instalación de los componentes del host, pero estos no son esenciales si es que no se va a trabajar con las herramientas de desarrollo de Nvidia.

## 3. Instalar TensorFlow (opcional)
* Una vez que JetPack esté instalado, hay que conectar la Jetson a internet. La forma más simple es conectando a un router/switch mediante Ethernet.
* Una vez que este comprobado que la conexión a internet funciona, recomiendo actualizar el sistema con
```
sudo apt update
sudo apt upgrade
```
&nbsp; si es que aún no lo has hecho.
* Para instalar TensorFlow recomiendo seguir la guía que está en la [documentación de Nvidia](https://docs.nvidia.com/deeplearning/frameworks/install-tf-jetson-platform/index.html) al respecto. Debo señalar que no todas las versiones de TF se encuentran disponibles en los repositorios de Nvidia (a la fecha de escritura, para JetPack 4.3 sólo esta TF-1.15 y TF-2.0). Recomiendo usar la instalación dentro de un virtual environment para evitar conflictos futuros con otros paquetes.
