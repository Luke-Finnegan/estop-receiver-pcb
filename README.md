# estop-receiver-pcb (WIP)
Emergency Stop Receiver Board
A 2-layer PCB designed for Sooner Competitive Robotics' autonomous robot platform. The board receives a wireless emergency-stop signal over LoRa RF and translates it into a CAN bus message and a MOSFET-switched output to safely halt robot operation.
Overview
Safety-critical robots require a reliable, interference-resistant method to halt all motion on command. This board was designed to replace a more complex multi-board solution with a single compact receiver that handles RF reception, protocol conversion, and power switching in one unit.
Hardware
ComponentPartFunctionMicrocontrollerSTM32C092Central processing, CAN and SPI coordinationRF ModuleRFM95 LoRaWireless e-stop signal receptionCAN TransceiverMAX3051CAN bus interface to robot subsystemsVoltage RegulatorREG1117-3.312V to 3.3V regulationOutput StageZXMP3A16GTA P-channel MOSFETsSafety-critical switched output
Board dimensions: 1.52" × 2.85"
Layers: 2
Designed in: Altium Designer
Schematic
Show Image
PCB Layout
Show Image
Board Photo
Show Image
Design Decisions
Hierarchical schematic structure — the design is split across three sheets (Power, Controller, MOSFET) tied together at the top level. This keeps each subsystem readable independently and reflects how the board actually functions as three distinct stages.
SMA antenna connector — a panel-mount SMA connector was chosen for the RFM95 antenna interface to allow a proper external antenna rather than a PCB trace antenna, improving range and reliability in an electrically noisy robot environment.
Separate MOSFET output stage — the switched output is isolated from the controller stage so that a fault in the output circuit cannot directly affect the microcontroller or RF receiver.
Bring-Up Notes
Board was hand-soldered and validated using a bench power supply and multimeter. Hardware faults were encountered during initial bring-up and diagnosed using bench equipment. A backup circuit path was implemented to meet competition deadline. The board successfully operated at IGVC 2026 where the team placed 6th out of 22 teams.
Tools

Altium Designer
STM32 ecosystem
Bench multimeter, oscilloscope, power supply
