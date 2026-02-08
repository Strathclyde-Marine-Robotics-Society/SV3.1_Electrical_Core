# Meeting 3

**Meeting Date**: 05/01/2026
**Actual time of writing this document**: 08/02/2026.
**Attendees**: Sandy, Alfie, Ezra, Eli, Michael, Owen.
**Absences**: Sandy.

1. Assign owners of tasks on the To-Do. 
	- DONE
2. Discussion of thruster layout from previous general meeting. 
	- DONE
3. Refine Functional Requirements. 
	- Added Physical Layout Requirement
	- Possibly removed Anttenae requirement
	- Renamed MCU to Control
		- Control concerns state management, thruster control, user inputs. 

### Ben's MCU for Control
- Heat dispersion down converter
- SBUS is inverted UART - Schmitt trigger helps this
- I2C communication
- 3 UART 
- 5V to 3V3 LDO
- POWER DESIGNER WEBENCH
- USB-C connection
- NRST and BOOt0 allow programming - resets code

### General Meeting
- Notes can be found on the disc
