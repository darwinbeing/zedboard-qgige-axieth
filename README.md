zedboard-qgige-axieth
=====================

Example design for the [Quad Gigabit Ethernet FMC](http://ethernetfmc.com "Ethernet FMC") on the [ZedBoard](http://zedboard.org "ZedBoard") using AXI Ethernet

### Description

This project demonstrates the use of the Opsero [Quad Gigabit Ethernet FMC](http://ethernetfmc.com "Ethernet FMC").
The design contains 4 AXI Ethernet blocks configured with DMAs.

![All AXI Ethernet](http://ethernetfmc.com/wp-content/uploads/2014/10/qgige_all_axi_ethernet.png "Ethernet FMC Quad Gig Ethernet All AXI Ethernet")

### Requirements

* Vivado 2014.3.1 (see Library modifications below)
* [Ethernet FMC](http://ethernetfmc.com "Ethernet FMC")
* [ZedBoard](http://zedboard.org "ZedBoard")
* [Xilinx Soft TEMAC license](http://ethernetfmc.com/getting-a-license-for-the-xilinx-tri-mode-ethernet-mac/ "Xilinx Soft TEMAC license")

### Library modifications for Vivado 2014.3.1

To use this project, a modification must be made to the lwIP libraries
provided by the Xilinx SDK. The modification can be made either to the
BSP code of your SDK workspace, or to the SDK sources. I personally
recommend modifying the SDK sources as every rebuild of the BSP results
in the BSP sources being overwritten with the SDK sources.

#### Modification to xaxiemacif_dma.c 

Open the following file:

`C:\Xilinx\SDK\2014.3.1\data\embeddedsw\ThirdParty\sw_services\lwip140_v2_2\src\contrib\ports\xilinx\netif\xaxiemacif_dma.c`

Replace this line of code:

`DMAConfig = XAxiDma_LookupConfig(XPAR_AXIDMA_0_DEVICE_ID);`

With this one:

`DMAConfig = XAxiDma_LookupConfig(xemac->topology_index);`

### License

Feel free to modify the code for your specific application.

### Fork and share

If you port this project to another hardware platform, please send me the
code or push it onto GitHub and send me the link so I can post it on my
website. The more people that benefit, the better.

### About the author

I'm an FPGA consultant and I provide FPGA design services to innovative
companies around the world. I believe in sharing knowledge and
I regularly contribute to the open source community.

Jeff Johnson
[FPGA Developer](http://www.fpgadeveloper.com "FPGA Developer")