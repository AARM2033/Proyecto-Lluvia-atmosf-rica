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
docker run -it --env="LIBGL_ALWAYS_SOFTWARE=1"  --name my_project   --net=host   --env="DISPLAY" --device /dev/dri  -v $HOME/.Xauthority:/root/.Xauthority:rw   -v ${HOME}/geant4-project:/geant4lab  aarm2034/andres-rivera:latest
```

Una vez dento del contenedor entra hasta la carpeta:

```bash
cd /geant4lab/proyecto_lluvias_cosmicas/build
```

Compila el proyecto:

```bash
cmake ..
make
```

Y ejecútalo:

```bash
./sim
```
