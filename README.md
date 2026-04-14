# Urban-Intersection-Control-System
A PLC-based traffic light control system for a four-way intersection, built in Siemens TIA Portal with HMI visualization. The project combines Ladder Logic and Structured Text to implement a modular, scalable control system with safety and emergency-handling features.

<img width="3000" height="1697" alt="UICS_HMI" src="https://github.com/user-attachments/assets/95894d02-b736-4c3f-855c-b5e76be229e7" />

## 🚦 System Overview
This project simulates a real-world urban intersection using industrial PLC programming principles. It features a fully functional four-way traffic system with integrated pedestrian crossings, safety validation, and emergency handling.

The system is built around a **state machine architecture** to ensure predictable and stable behavior across PLC scan cycles.

## Features ✅
### 🚥 Four-Way Core Traffic Control
- Implemented as a **deterministic four-phase state machine**
- Traffic flow sequence:
  - East → West → South → North
- Each direction operates on a **20-second cycle**:
  - 0–15s: Green light active
  - 15–20s: Yellow light active
  - 20s+: Red light active and transition to next phase
- All conflicting directions remain **Red** during each active phase
- Includes automatic **cycle reset logic** for continuous operation
### 🚶 Pedestrian Crossing System
- Implemented using **reusable Structured Text Function Blocks**
- Features:
  - Pedestrian **request detection** (push button + HMI input)
  - **Queue system** (requests persist until safe crossing condition)
  - **Crossing enable logic** tied to traffic state machine
  - **8-second walk timer** with live countdown on HMI
- Fully synchronized with traffic light phases to prevent conflicts
### 🛑 Emergency Stop System
- Immediate system halt via:
  - Physical stop input
  - HMI stop command
  - Fault detection
- Immediately forces all outputs to **Red** for safety
- Ensures that the system halts in a **fail-safe state**
- Includes **latched emergency handling with controlled reset**
### 🛡️ System Safety & Validation
- Pre-operation and runtime validation of:
  - Traffic light signals
  - Pedestrian signals
- Ensures:
  - No conflicting signals (e.g., Red + Green simultaneously)
  - Valid signal states before system start
- Detects faults and triggers **safe shutdown behavior**
### 🧠 Modular Function Block Architecture
- Separation of concerns:
  - `Main` → Entire system (Ladder Logic)
    - `Main_Control_System_DB` → System-level state machine (Ladder Logic)
      - `System_Condition_Check_DB` → Safety validation (ST)
      - `Status_Reset_DB` → Reset logic (Ladder Logic)
      - `Traffic_Light_Operations_DB` → Core traffic logic (Ladder Logic)
        - `Pedestrian_Operations_DB` → Pedestrian coordination (ST)
          - `Pedestrian_Crossing_MainStEast_DB` → Reusable crossing logic for eastern Main St (ST)
          - `Pedestrian_Crossing_MainStWest_DB` → Reusable crossing logic for western Main St (ST)
          - `Pedestrian_Crossing_CrossStSouth_DB` → Reusable crossing logic for southern Cross St (ST)
          - `Pedestrian_Crossing_CrossStNorth_DB` → Reusable crossing logic for northern Cross St (ST)
- Demonstrates **scalable PLC design patterns**
### 🖥️ HMI Visualization
- Real-time graphical intersection display
- Features:
  - Traffic light indicators
  - Pedestrian Walk / Don’t Walk signals
  - Countdown timers
  - Queue indicators
  - Signal condition status indicators
- Operator controls:
  - Start / Stop system
  - Pedestrian crossing requests

## 🛠 Technologies Used 
- **PLC**: Siemens S7-1500 (PLCSIM)
- **HMI**: Siemens KTP Basic (simulation)
- **Programming Languages**:
  - Ladder Logic → Core control, state transitions, safety interlocks
  - Structured Text → Pedestrian logic, reusable FBs, timers
 
## 🧩 Key Engineering Concepts Demonstrated
- Deterministic **state machine design**
- PLC **scan cycle awareness**
- Avoidance of **race conditions and feedback loops**
- Modular **Function Block architecture**
- Separation of **state control vs output logic**
- Safe system design using **fail-safe principles**
- Integration of Ladder Logic and Structured Text in one system

## ⚠️ Challenges Solved
- Eliminated **state machine flickering** in `Main_Control_System_DB` caused by multiple writes in a single scan
- Resolved **pedestrian queue synchronization issues** in `Pedestrian_Operations_DB`
- Fixed **crossing activation during invalid traffic states**
- Stabilized logic using **state-driven control instead of direct signal coupling**
- Debugged **multi-instance timer behavior in Structured Text**
- Prevented **unsafe signal overlaps through validation logic** in `System_Condition_Check_DB`

## 🚀 Status
✅ Fully functional four-way intersection system  
✅ Pedestrian crossing system with queue and timers  
✅ Emergency stop and safety validation implemented  
✅ Stable, scan-safe state machine architecture  
