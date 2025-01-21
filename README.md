# diseño_cambio_color
Diseño de un programa con IP core que cambia el color de una imagen (HDMI Pynq-Z2)

## Objetivo
Diseño de un programa con IP Cores para cambiar el color, en caso de desearlo, de una imagen/señal de una pantalla de un ordenador recibida a través de HDMI. El objetivo es modificar los colores de cada píxel en la imagen y visualizar el resultado en una pantalla auxiliar conectada a la salida HDMI de la placa PYNQ.

## Herramientas
- **Vitis HLS**: Para el diseño del IP Core que gestiona y realiza el cambio de color.
- **Vivado**: Para el diseño del sistema en la FPGA, diagrama de bloques.
- **Jupyter**: Para interactuar con el diseño (PS-PL) y controlar la modificación de la imagen.

## Requisitos
### Entrada y salida de video:
- Capturar video de entrada a través del puerto HDMI y devolver el video procesado al puerto HDMI de salida.
### Procesamiento de color:
- Implementar funciones básicas de cambio de color: escala de grises.
### Control del procesamiento:
- Permitir al usuario decidir si realizar o no el cambio de color.
### Procesamiento en tiempo real:
- Garantizar que el procesamiento de cada frame sea continuo y sin interrupciones.
### Compatibilidad con resoluciones comunes:
- Soportar al menos resoluciones de 720p y 1080p.

## Estructura del proyecto
### Vivado
El archivo del proyecto `.xpr` se encuentra ubicado en: \vivado\prueba\PYNQ\boards\Pynq-Z2\base.

Este proyecto emplea dos repositorios ip, localizados en: \vivado\prueba\PYNQ\boards.

- **ip**: contiene los IP Cores necesarios para el procesamiento HDMI.
- **color**: contiene el IP Core que realiza el cambio de color.

### Jupyter Notebook
El notebook empleado `hdmi_prueba.ipynb` se ubica en \jupyter

## Instrucciones
### Clonar el repositorio
Clona el repositorio a tu máquina local para obtener todos los archivos necesarios:
```bash
git clone https://github.com/AndreaUGR/dise-o_cambio_color.git

