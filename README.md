# Gantry Robot

**Gantry Robot** is an automated assembly cell project developed using **Siemens S7-300**, **TIA Portal V20**, **S7-PLCSIM**, and **Factory I/O**.

The project demonstrates PLC-based control of a virtual assembly process using the **Assembly / Assembler Control** scene in Factory I/O.

## Project Overview

The goal of the project is to develop and test an automated assembly sequence without using physical industrial equipment.

The PLC program controls the complete assembly cycle, including:

* base and lid feeding;
* conveyor control;
* part position detection;
* base and lid clamping;
* Gantry Robot movement along the X and Z axes;
* part grabbing and transfer;
* finished product detection and exit.

The control logic is implemented in **LAD (Ladder Logic)** and executed on a simulated **Siemens S7-300 PLC** using S7-PLCSIM.

## System Architecture

```text
Factory I/O
Assembly / Assembler Control
        │
        │ I/O communication
        ▼
    S7-PLCSIM
        │
        ▼
 Siemens S7-300
 TIA Portal V20
      OB1 / LAD
```

Factory I/O acts as the 3D digital representation of the assembly cell, while the PLC logic is developed in TIA Portal and executed through S7-PLCSIM.

## Technologies

* Siemens S7-300
* Siemens TIA Portal V20
* S7-PLCSIM
* Factory I/O
* LAD (Ladder Logic)
* PLC Programming
* Industrial Automation
* Digital Twin Simulation

## Main I/O

Some of the main signals used by the system are:

| Address | Signal         | Description                    |
| ------- | -------------- | ------------------------------ |
| I0.0    | Moving X       | X-axis movement feedback       |
| I0.1    | Moving Z       | Z-axis movement feedback       |
| I0.3    | Lid at place   | Lid position sensor            |
| I0.4    | Lid clamped    | Lid clamp feedback             |
| I0.6    | Base at place  | Base position sensor           |
| I0.7    | Base clamped   | Base clamp feedback            |
| I1.1    | Part leaving   | Finished part leaving the cell |
| I1.2    | Start          | System start                   |
| I1.3    | Reset          | System reset                   |
| Q0.0    | Move X         | Gantry X-axis movement         |
| Q0.1    | Move Z         | Gantry Z-axis movement         |
| Q0.2    | Grab           | Gantry gripper                 |
| Q0.3    | Lids conveyor  | Lid conveyor                   |
| Q0.4    | Clamp lid      | Lid clamp                      |
| Q0.6    | Bases conveyor | Base conveyor                  |
| Q0.7    | Clamp base     | Base clamp                     |
| Q1.4    | Base emitter   | Base part emitter              |
| Q1.5    | Lids emitter   | Lid part emitter               |

## Operating Sequence

The automated cycle consists of the following main stages:

1. **Start** — the PLC receives the system start command.
2. **Feed** — base and lid components are introduced into the assembly cell.
3. **Position** — sensors detect when the components reach their required positions.
4. **Clamp** — the base and lid are secured.
5. **Move** — the Gantry Robot moves along the X and Z axes.
6. **Grab / Assembly** — the robot performs the required handling and assembly sequence.
7. **Exit** — the completed part leaves the assembly cell.

## PLC Program

The main control logic is implemented in **OB1** using Ladder Logic.

The program uses internal memory markers and IEC **TON timers** to control the sequence and timing of operations.

Main timers include:

* `T0` — 3 s
* `T1` — 1 s
* `T2` — 3 s
* `T3` — 100 ms

## Project Files

| File                           | Description                           |
| ------------------------------ | ------------------------------------- |
| `Assembler Control_Almaz.ap20` | TIA Portal V20 project                |
| `Passport_GantryRobot.docx`    | Project passport / user documentation |
| `TechDoc_GantryRobot.md`       | Detailed technical documentation      |
| `Presentation_GantryRobot.pdf` | Project presentation                  |
| `Program_Export.pdf`           | Export of the PLC program             |
| `Github.txt`                   | Link to the GitHub repository         |

Additional presentation materials used during the project defense are also preserved in the repository.

## Documentation

For detailed information about the PLC logic, I/O mapping, timers, system operation, and troubleshooting, see:

**[TechDoc_GantryRobot.md](TechDoc_GantryRobot.md)**

Project passport:

**[Passport_GantryRobot.docx](Passport_GantryRobot.docx)**

Project presentation:

**[Presentation_GantryRobot.pdf](Presentation_GantryRobot.pdf)**

## Repository

GitHub repository:

**https://github.com/ViyeiraAlmaz/Gantry-Robot**

## Project Result

The project demonstrates the integration of PLC programming and 3D industrial simulation. The developed control logic manages the main stages of the automated assembly process and can be tested using S7-PLCSIM and Factory I/O without requiring a physical PLC or assembly station.

