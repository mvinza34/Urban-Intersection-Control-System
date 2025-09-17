# Urban-Intersection-Control-System
A PLC-based traffic light control system for a four-way intersection, built in Siemens TIA Portal with HMI visualization. The project combines ladder logic and structured text to implement a modular, scalable control system that incorporates safety and emergency handling features.

<img width="2048" height="1406" alt="image" src="https://github.com/user-attachments/assets/ad31b016-b17d-4a79-b0ee-18cdac25eb4d" />

## Current Features 🚦
### Four-Way Core Traffic Control
- Implemented as a four-phase state machine (East → West → South → North).
- Each direction has a 20-second cycle:
  - 0–15s: Green light active.
  - 15–20s: Yellow light active.
  - After 20s, the Red light turns on, and the state machine transitions to the next phase.
- All opposite/cross directions remain Red during each active phase.
### Emergency Stop Function
- Immediately resets all outputs to Red for safety.
- Ensures that the system halts in a fail-safe state.
### HMI Visualization
- Graphical intersection display with live signal indicators.
- Timer values displayed per direction.
- Start/Stop buttons for operator control.
## Technologies Used 🛠
- **PLC**: Siemens S7-1500 (tested with PLCSIM)
- **HMI**: Siemens KTP Basic panel simulation
- **Programming Languages**:
  - Ladder Logic (core logic, timers, signals)
  - Structured Text (planned for state machine refinements, pedestrian, and emergency logic)

## Project Roadmap 📌
| Component |	Implementation Language	| Status / Notes
| --------- | ----------------------- | ------------ | 
| Basic Light Control (4-way)	| Ladder Logic |	✅ Implemented
| Pedestrian Walk Request Output | Ladder Logic |	⏳ Planned
| State Machine (modes/transitions) | Structured Text |	✅ Implemented for core traffic ⏳ Planned for other steps
| Emergency Vehicle Override Logic | Structured Text |	⏳ Planned
| Pedestrian Queue / Delay Logic |Structured Text |	⏳ Planned
| Timers and Flashing Signals |	Ladder Logic |	✅ Basic timers in place; flashing TBD
| HMI Visualization (per step) | Ladder Logic + HMI |	✅ Implemented for core traffic ⏳ Planned for other steps

## Next Steps 🚀
1) Extend the system with **pedestrian signal logic** (Ladder + ST).
2) Add **emergency vehicle override logic** to preempt normal cycles.
3) Implement **pedestrian queuing and delays** for more realistic crossings.
4) Add **flashing red/yellow signals** for nighttime or fault conditions.
5) Expand **HMI visualization** with pedestrian crossings, emergency states, and system diagnostics.
