# Artix-7 M.2 Hardware Accelerator

A custom M.2 PCIe hardware accelerator based around an (Xilinx) Artix-7 XC7A100T-1FGG484C that I designed in Altium for my own embedded computer vision and DSP projects.

# Motivation

During the Fall 2025 semester, I was a Project Lead for the **Machine Intelligence Lab's** Software team, specifically Computer Vision. For our autonomous submersible (*sub9*), we had a huge stack of CV-algorithms that fed into each other, but I was frustrated with our real-time performance since we're heavily resource constrainted running on an embedded system.

Earlier that year, a friend (shoutout Zack Mendez, best Digital Design TA) showed me how he could write and deploy some video-filtering kernels onto an FPGA ([Zack's RTIPCV Project](https://github.com/zack-mendez/fpgators-rtipcv/tree/main)).

That got me thinking, our computer vision stack for the submersible has several basic pre-processing layers, so if I can move those to a hardware accelerator, I can free up more GPU/CPU resources for the more complex CNNs.

My hardware accelerator would need to be a small form factor with high bandwidth which was how I landed on M.2, which our computer (Jetson Nano) has on newer versions.

What really pushed me forward with this project was seeing an M.2 hardware accelerator built by Phil Salmony using an Artix-7 A35T, and it proved to me that something of this scale was possible.

A final motivation was having a chance to tinker with Altium more, especially with high speed designs. As an Electrical Engineer, I feel like PCB development is one of those quintessential skills that kind of defines us, and is especially useful as an Embedded/Hardware guy.

# Schematic Design (12/20/25 - 01/01/26)

Took a break from my [SystemVerilog I2C-IP project](https://github.com/WithanagePerera/I2C-Interface-IP) to work on this.

Spent this time for my component selection, then designing all of my circuits in Altium like the power distribution for all of my voltage rails, configuration of the FPGA banks, the MGTs for PCIe, DDR3L, QSPI and JTAG, etc.

I plan on taking a break from this to finish off my I2C project, but the next step is validation of my circuits and running some signal integrity checks to check my transmission line effects on the high speed signals, then finally PCB development.

<img src="Images/Overview Page.png">
<figcaption>Block Diagram Overview</figcaption>

<br/>

<div style="display:flex; justify-content:center; gap:20px;">
    <figure style="margin:0; flex:1;">
        <img src="Images/Power Rails Page.png">
        <figcaption>Power Rails</figcaption>
    </figure>
    <figure style="margin:0; flex:1;">
        <img src="Images/Configuration Page.png">
        <figcaption>FPGA Configuration</figcaption>
    </figure>
</div>

<br/>

<div style="display:flex; justify-content:center; gap:20px;">
    <figure style="margin:0; flex:1;">
        <img src="Images/Power Distribution Page.png">
        <figcaption>Power Distribution</figcaption>
    </figure>
    <figure style="margin:0; flex:1;">
        <img src="Images/FPGA GPIO Banks Page.png">
        <figcaption>GPIO Banks</figcaption>
    </figure>
</div>

<br/>

<div style="display:flex; justify-content:center; gap:20px;">
    <figure style="margin:0; flex:1;">
        <img src="Images/DRAM Banks Page.png">
        <figcaption>DRAM Banks</figcaption>
    </figure>
    <figure style="margin:0; flex:1;">
        <img src="Images/DDR3L Config Page.png">
        <figcaption>DDR3L Configuration</figcaption>
    </figure>
</div>

<br/>

<div style="display:flex; justify-content:center; gap:20px;">
    <figure style="margin:0; flex:1;">
        <img src="Images/MGT Config Page.png">
        <figcaption>MGT Configuration</figcaption>
    </figure>
    <figure style="margin:0; flex:1;">
        <img src="Images/M.2 Edge Connector Page.png">
        <figcaption>M.2 M-Key Edge Connector</figcaption>
    </figure>
</div>