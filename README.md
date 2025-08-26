# Real-time hdmi color change
Diseño de un sistema basado en IP Core para la FPGA PYNQ-Z2 que procesa señales de video HDMI y modifica los valores de color de cada píxel en tiempo real.
<br>
## Objetivo
Diseñar e implementar un sistema basado en IP Cores sobre la FPGA de la placa PYNQ-Z2 que permita modificar selectivamente los valores de color de cada píxel de una señal de video digital recibida vía HDMI desde un ordenador. El sistema procesará la señal de video en tiempo real, aplicando transformaciones de color como conversión a escala de grises, y transmitirá la señal resultante a un monitor auxiliar conectado a la salida HDMI de la placa. La activación de la modificación de color se controlará mediante los switches de la PYNQ-Z2, permitiendo alternar entre la señal original y la señal procesada.
<br>

## Requisitos
### Requisitos de Hardware
- **Placa PYNQ-Z2**: Plataforma FPGA utilizada para el procesamiento de la señal HDMI; se emplean sus puertos HDMI de entrada y salida para recibir y transmitir la señal de video en tiempo real.  
- **Monitor con entrada HDMI**: Para visualizar la señal de video procesada por la FPGA.  
- **Fuente de señal HDMI**: Ordenador u otro dispositivo con salida HDMI que proporcione la señal de video original.  
- **Cables HDMI**: Conexión entre la fuente de señal y la entrada HDMI de la PYNQ-Z2, así como entre la salida HDMI de la placa y el monitor.  
- **Cable Ethernet**: Para establecer comunicación con la PYNQ-Z2 y acceder al entorno Jupyter Notebook, permitiendo control y monitoreo del sistema.

### Requisitos de Software
- **Vivado (versión 2022.1)**: Entorno de desarrollo FPGA utilizado para el diseño, síntesis y generación del bitstream del sistema, así como para la creación, configuración e integración de los IP Cores en el diagrama de bloques.  
- **Vitis HLS**: Herramienta de síntesis de alto nivel para diseñar y generar el IP Core encargado del procesamiento y modificación de los valores de color de la señal HDMI en tiempo real.  
- **Jupyter Notebook**: Entorno de control y ejecución sobre la PYNQ-Z2 que permite cargar el bitstream, gestionar los IP Cores y monitorear el procesamiento de la señal de video.

### Dependencias adicionales
- **Bibliotecas de Python**:  
  - `pynq`: Biblioteca principal para la interacción con la placa PYNQ-Z2, carga del bitstream y gestión de los recursos de la FPGA.  
  - `pynq.lib.video`: Para la captura, procesamiento y transmisión de señales de video HDMI en tiempo real.  
  - `pynq.lib.AxiGPIO`: Para la interacción con los periféricos de la FPGA, incluyendo la lectura de switches y control de GPIO.


### Requisitos de configuración
- El entorno de desarrollo debe estar correctamente configurado para soportar la FPGA y los IP Cores implementados en el proyecto.  
- La placa PYNQ-Z2 debe iniciarse desde la tarjeta SD, asegurándose de que la imagen de arranque de PYNQ esté correctamente instalada y operativa.  
- Para acceder al entorno Jupyter Notebook, la PYNQ-Z2 debe estar conectada a la red local mediante un cable Ethernet.  
- Es necesario **cargar en la FPGA los archivos `.bit` y `.hwh`** generados en Vivado, los cuales contienen la configuración del diseño y la descripción de los IP Cores, garantizando el correcto funcionamiento del sistema.
  <br>
  
## Estructura del proyecto
### Vivado
El archivo del proyecto `.xpr` se encuentra en: `\vivado\prueba\PYNQ\boards\Pynq-Z2\base`.  

El proyecto utiliza dos repositorios de IP localizados en: `\vivado\prueba\PYNQ\boards`  

- **ip**: Contiene los IP Cores necesarios para la captura, procesamiento y transmisión de la señal HDMI.  
- **color**: Contiene el IP Core responsable de la modificación de color de la señal de video.  

### Jupyter Notebook
El notebook utilizado `hdmi_prueba.ipynb` se encuentra en: `\jupyter`.  
Se emplea para cargar el bitstream en la FPGA, configurar los IP Cores y controlar el procesamiento de la señal HDMI en tiempo real.  
<br>
## IP Core "color"
Este IP Core está diseñado para recibir una señal de video en formato RGB de 24 bits por píxel y modificar los valores de color de cada píxel.  
Se implementó utilizando **Vitis HLS** y se integra con los demás componentes del sistema FPGA a través de Vivado.  

### Funciones principales:

#### Si alguno o ambos switches de la PYNQ están en 0:
- La señal de video se recibe y transmite hacia la salida HDMI **sin modificación**.  

#### Si ambos switches de la PYNQ están en 1:
- Modifica los valores de cada píxel de la señal HDMI en **tiempo real**.  
- Ajusta los valores RGB para convertir los píxeles a **escala de grises**.  
- Procesa la señal de video de 24 bits por píxel y la transmite modificada a la salida HDMI.
<br>

## Instrucciones
### Clonar el repositorio
Clona el repositorio a tu máquina local para obtener todos los archivos necesarios:
```bash
git clone https://github.com/AndreaUGR/dise-o_cambio_color.git

