# Proyecto: Simulación de Lluvia Atmosférica (Geant4)

Este repositorio contiene el código fuente y la configuración necesaria para ejecutar una simulación de lluvias cósmicas/atmosféricas utilizando **Geant4**. 

## Requisitos Previos

Antes de comenzar, asegúrate de tener instalado docker en tu sistema (preferiblemente un entorno Linux/Ubuntu):


##  Instalación y Despliegue

### 1. Descargar la imagen de Docker

La imagen ya contiene el entorno de Geant4 compilado y el código fuente del proyecto integrado. Descárgala desde Docker Hub con el siguiente comando:

```bash
docker pull aarm2034/andres-rivera
```

Para que Geant4 pueda abrir las ventanas de visualización (Qt/OpenGL) desde adentro del contenedor, debes permitir que Docker se conecte al servidor de pantalla de tu máquina local:

```bash
xhost +local:docker
```

### **2. Ejecutar el contenedor**

Inicia un contenedor:

```bash
docker run -it -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix aarm2034/andres-rivera:latest bash
```

Una vez dento del contenedor entra hasta la carpeta:

```bash
cd /geant4lab/proyecto_lluvias_cosmicas/build
```

En esta imagen se tienen archivos de compilación, se puede ejecutar directamente
```bash
./sim
```

O eliminar su contenido con el comando
```bash
rm -rf *
```

Con esto ultimo se debe crear de nuevo el archivo vis.mac
```bash
nano vis.mac
```

Y copia su contenido que está colocado en este repositorio de github

Luego, compila el proyecto:

```bash
cmake ..
make
```

Y ejecútalo:

```bash
./sim
```
