# Urban-Intersection-Control-System
A PLC-based traffic light control system for a four-way intersection, built in Siemens TIA Portal with HMI visualization. The project combines ladder logic and structured text to implement a modular, scalable control system that incorporates safety and emergency handling features.

<img width="3000" height="1699" alt="image" src="https://github.com/user-attachments/assets/a90a5222-9a87-4cb5-acaf-5748899211fa" />

## System Overview ⚙
The system is built around a **state-machine-driven traffic controller** that governs all signal phases and transitions. Pedestrian logic, HMI behavior, and safety systems are derived from this state machine to ensure deterministic, stable operation.

The architecture separates responsibilities into distinct functional layers:
- Core traffic phase control
- Pedestrian operations
- Emergency handling
- Visualization and operator control
- System coordination and supervision

## Current Features 🚦
### Four-Way Core Traffic Control
- Implemented as a **four-phase state machine**
  - East → West → South → North
- Each direction has a 20-second cycle:
  - 0–15s: Green light active.
  - 15–20s: Yellow light active.
  - Transition → Red
- All conflicting directions remain Red during each active phase.
- Fully deterministic sequencing (no race conditions, no conflicting greens).
### State Machine Architecture
- Centralized traffic phase control logic
- All timing, transitions, and permissions derive from state
- Eliminates dependency on signal-level logic for coordination
- Enables safe integration of pedestrian and emergency systems
### Emergency Stop Function
- Immediately resets all outputs to Red for safety.
- Ensures that the system halts in a fail-safe state.
### HMI Visualization
- Graphical intersection display with live signal indicators.
- Timer values displayed per direction.
- Start/Stop buttons for operator control.
## Technologies Used 
- **PLC**: Siemens S7-1500 (tested with PLCSIM)
- **HMI**: Siemens KTP Basic panel (simulation)
- **Development Environment**: Siemens TIA Portal
- **Programming Languages**:
  - **Ladder Logic**
    - Core traffic sequencing
    - Timers
    - Signal control
    - Safety logic
  - **Structured Text**
    - State machine coordination
    - Pedestrian logic
    - Queue handling
    - System-level orchestration
   
## Project Architecture 🛠
```
PLC_UICS_01 [CPU 1512C-1 PN]
├── Main
│     ├── Main_Control_System_DB
│       ├── Traffic_Light_Operations_DB (State Machine Core)
│       │   ├── Phase sequencing
│       │   ├── Signal control
│       │   ├── Timers
│       │   ├── Status_Reset_DB
│       │   └── Reset / safety logic
│       │
│       ├── Pedestrian_Operations_DB
│       │   ├── Pedestrian_Crossing_MainStEast_DB
│       │   │   ├── Pedestrian request handling
│       │   │   ├── Queue logic
│       │   │   ├── Crossing authorization
│       │   │   └── Walk / Don't Walk control
│       │   ├── Pedestrian_Crossing_MainStWest_DB
│       │   │   ├── Pedestrian request handling
│       │   │   ├── Queue logic
│       │   │   ├── Crossing authorization
│       │   │   └── Walk / Don't Walk control
│       │   ├── Pedestrian_Crossing_CrossStSouth_DB
│       │   │   ├── Pedestrian request handling
│       │   │   ├── Queue logic
│       │   │   ├── Crossing authorization
│       │   │   └── Walk / Don't Walk control
│       │   ├── Pedestrian_Crossing_CrossStNorth_DB
│       │   │   ├── Pedestrian request handling
│       │   │   ├── Queue logic
│       │   │   ├── Crossing authorization
│       │   │   └── Walk / Don't Walk control
│ 
└── HMI_1 [KTP1200 Basic PN]
        ├── Visualization
        ├── Operator commands
```

## Project Roadmap 📌
| Component |	Implementation Language	| Status / Notes
| --------- | ----------------------- | ------------ | 
| Basic Light Control (4-way)	| Ladder Logic |	✅ Implemented
| Pedestrian Walk Request Output | Ladder Logic |	✅ Implemented
| State Machine (modes/transitions) | Structured Text |	✅ Implemented for core traffic and pedestrian operations
| Pedestrian Queue / Delay Logic | Structured Text |	✅ Implemented
| Timers and Flashing Signals |	Ladder Logic |	✅ Implemented
| HMI Visualization (per step) | HMI + Ladder Logic + Structured Text |	✅ Implemented for core traffic and pedestrian operations

## Next Steps 🚀
1) Add **extra safety checks** that must be satisfied before starting the traffic system.
2) TBD
