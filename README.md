# diseño_cambio_color
Diseño de un programa con IP core que cambia el color de una imagen (HDMI PYNQ-Z2)

## Objetivo
Diseño de un programa con IP Cores para cambiar el color, en caso de desearlo, de una imagen/señal de un ordenador recibida a través de HDMI. El objetivo es modificar los colores de cada píxel en la imagen y visualizar el resultado en una pantalla auxiliar conectada a la salida HDMI de la placa PYNQ.
<br><br>

## Requisitos
### Requisitos de Hardware
- **Placa PYNQ-Z2**: Emplearemos los puertos HDMI de entrada y salida para recibir y mostrar la señal/imagen.
- **Monitor con entrada HDMI**: Para visualizar la imagen modificada.
- **Fuente de señal HDMI**: Un ordenador o dispositivo con salida HDMI que sirva de fuente de imagen.
- **Cables HDMI**: Para conectar la fuente de señal HDMI a la placa PYNQ-Z2 y la salida HDMI del PYNQ-Z2 al monitor.
- **Cable Ethernet**: Para acceder a Jupyter en la PYNQ-Z2.

### Requisitos de Software
- **Vivado** (versión 2022.1): Necesario para el diseño y síntesis del sistema FPGA, así como para la creación de los IP Cores y la configuración del diagrama de bloques.
- **Vitis HLS**: Para el diseño del IP Core que gestiona y realiza el cambio de color en la señal HDMI.
- **Jupyter Notebook**: Para ejecutar y controlar el diseño.

### Dependencias adicionales
- **Bibliotecas de Python**:
  - `pynq`: Biblioteca principal para interactuar con la placa PYNQ-Z2, cargar el bitstream y manejar la FPGA.
  - `pynq.lib.video`: Para el manejo y procesamiento la señal HDMI.
  - `pynq.lib.AxiGPIO`: Para interactuar con los GPIO de la FPGA, los switches.

### Requisitos de configuración
- El entorno de desarrollo debe estar configurado para trabajar con la FPGA y los IP Cores utilizados en el proyecto.
- La placa PYNQ-Z2 debe arrancarse* desde la tarjeta SD, asegurándose de que la imagen de arranque de PYNQ esté correctamente instalada en ella.
- Para acceder a Jupyter, la placa PYNQ-Z2 debe estar conectada a la red local a través del cable Ethernet.
- Es necesario **cargar el archivo `.bit`** y el archivo **`.hwh`** generados en Vivado en la placa PYNQ-Z2 para que el diseño y los IP Cores funcionen correctamente. 
  <br><br>
  
## Estructura del proyecto
### Vivado
El archivo del proyecto `.xpr` se encuentra ubicado en: \vivado\prueba\PYNQ\boards\Pynq-Z2\base.

Este proyecto emplea dos repositorios ip, localizados en: \vivado\prueba\PYNQ\boards.

- **ip**: contiene los IP Cores necesarios para el procesamiento HDMI.
- **color**: contiene el IP Core que realiza el cambio de color.

### Jupyter Notebook
El notebook empleado `hdmi_prueba.ipynb` se ubica en \jupyter
<br><br>

## IP Core "color"
Este IP Core está diseñado para recibir una señal de video en formato RGB y modificar el color de los píxeles de la imagen. Se implementó utilizando **Vitis HLS** y se integra con otros componentes del sistema FPGA en Vivado.

### Funciones principales:
#### Si alguno o los dos switches de la PYNQ estan a 0:
- recibe la señal de video en formato de 24 bits por píxel (RGB) y la envia sin modificar hacia la salida HDMI.
#### Si los dos switches de la PYNQ estan a 1:
- Modifica los valores de los píxeles de la señal HDMI en tiempo real.
- Ajusta los valores RGB para proporcionar los pixeles en escala de grises.
- Recibe la señal de video en formato de 24 bits por píxel (RGB) y la procesa para transmitirla modificada a la salida HDMI.
<br><br>

## Instrucciones
### Clonar el repositorio
Clona el repositorio a tu máquina local para obtener todos los archivos necesarios:
```bash
git clone https://github.com/AndreaUGR/dise-o_cambio_color.git

