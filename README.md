# Real-time HDMI Color Change
Design of an IP Core-based system for the PYNQ-Z2 FPGA that processes HDMI video signals and modifies the color values of each pixel in real time.  


## Objective
Design and implement an IP Core-based system on the PYNQ-Z2 FPGA board that allows selective modification of the color values of each pixel in a digital video signal received via HDMI from a computer. The system will process the video signal in real time, applying color transformations such as grayscale conversion, and transmit the resulting signal to an auxiliary monitor connected to the board’s HDMI output. The activation of the color modification will be controlled via the PYNQ-Z2 switches, allowing switching between the original and processed signals.  
<br>

## Requirements
### Hardware
- **PYNQ-Z2 Board**: FPGA platform used for HDMI signal processing; its HDMI input and output ports are used to receive and transmit the video signal in real time.  
- **Monitor with HDMI input**: To display the video signal processed by the FPGA.  
- **HDMI Signal Source**: Computer or other device with HDMI output providing the original video signal.  
- **HDMI Cables**: To connect the signal source to the PYNQ-Z2 HDMI input and the board HDMI output to the monitor.  
- **Ethernet Cable**: To communicate with the PYNQ-Z2 and access the Jupyter Notebook environment for system control and monitoring.  
### Software
- **Vivado (version 2022.1)**: FPGA development environment used for design, synthesis, and bitstream generation, as well as for creating, configuring, and integrating IP Cores in the block diagram.  
- **Vitis HLS**: High-Level Synthesis tool used to design and generate the IP Core responsible for processing and modifying the HDMI signal’s color values in real time.  
- **Jupyter Notebook**: Control and execution environment on the PYNQ-Z2 that allows loading the bitstream, managing IP Cores, and monitoring video signal processing.  
### Additional Dependencies
- **Python Libraries**:  
  - `pynq`: Main library for interacting with the PYNQ-Z2 board, loading the bitstream, and managing FPGA resources.  
  - `pynq.lib.video`: For real-time HDMI video signal capture, processing, and transmission.  
  - `pynq.lib.AxiGPIO`: For interacting with FPGA peripherals, including reading switches and GPIO control.  
### Configuration
- The development environment must be properly configured to support the FPGA and IP Cores implemented in the project.  
- The PYNQ-Z2 board must boot from the SD card, ensuring the PYNQ boot image is correctly installed and operational.  
- To access the Jupyter Notebook environment, the PYNQ-Z2 must be connected to the local network via an Ethernet cable.  
- The FPGA must **load the `.bit` and `.hwh` files** generated in Vivado, which contain the design configuration and IP Core descriptions, ensuring proper system functionality.  
<br>

## Project Structure
### Vivado
The project file `.xpr` is located at: `\vivado\prueba\PYNQ\boards\Pynq-Z2\base`.  
The project uses two IP repositories located at: `\vivado\prueba\PYNQ\boards`  
- **ip**: Contains the IP Cores required for HDMI signal capture, processing, and transmission.  
- **color**: Contains the IP Core responsible for modifying the video signal’s color.  
### Jupyter Notebook
The notebook `hdmi_prueba.ipynb` is located at: `\jupyter`.  
It is used to load the bitstream onto the FPGA, configure the IP Cores, and control real-time HDMI signal processing.  
<br>

## IP Core "color"
This IP Core is designed to receive a 24-bit RGB video signal and modify the color values of each pixel.  
It was implemented using **Vitis HLS** and integrates with the FPGA system components via Vivado.  
### Main Functions:
#### If one or both PYNQ switches are 0:
- The video signal is received and transmitted to the HDMI output **without modification**.  
#### If both PYNQ switches are 1:
- Modifies the color values of each pixel in the HDMI signal **in real time**.  
- Adjusts RGB values to convert pixels to **grayscale**.  
- Processes the 24-bit per pixel video signal and transmits the modified signal to the HDMI output.  
<br>

## Instructions
### Clone the Repository
Clone the repository to your local machine to obtain all necessary files:  
```bash
git clone https://github.com/andbantri/hdmi-color-change-pynq.git

