# Functional Requirements

1. Power
	1. Voltage rails
	2. Safety
		1. BMS
		2. Fusebox
	3. Battery
2. Antennae - Ben
	1. User
		1. Remote control
		2. Remote control reciever
	2. Network (software)
	3. Diagnostics
3. Diagnostics - Eli, Michael
	- 3.1 Sensing
		- 3.1.1 The device must measure the temperature inside ESC enclosures.
		- 3.1.2 The device must measure the temperature inside the main electronics enclosure.
		- 3.1.3 The device must detect water ingress in the main electronics enclosure.
		- 3.1.4 The device should communicate with the Battery Management System to obtain cell and array status data.
		- 3.1.5 The device must receive data from the Jetson, including GPS position.
		- 3.1.6 The device should communicate with the Control system to obtain thruster output commands.
		- 3.1.7 The device should measure power delivered to thrusters.
	- 3.2 Transmission of Data
		- 3.2.1 All sensor data must be periodically polled and formatted into a standard packet structure.
		- 3.2.2 Data packets must be transmitted at regular intervals over radio.
		- 3.2.3 Packet structure must include a checksum to allow for verification of data integrity.
		- 3.2.4 Radio signals must be of sufficient power and appropriate frequency to be reliably received at 500m with line-of-sight (to shore).
		- 3.2.5 Transmission should be resilient to interference, by implementing Frequency Hopping Spread Spectrum (FHSS) or equivalent technique.
	- 3.3 Receiving Data
		- 3.3.1 The receiving radio must decode the radio signal and provide this as a USB interface.
		- 3.3.2 The received data must be saved to a file on a shore computer as a log.
		- 3.3.3 The data must be displayed in real-time on the screen of a shore computer for monitoring.
		- 3.3.4 The shore computer should provide a graphical user interface for real-time monitoring of diagnostic data.
4. Control - Alfie
	- 4.1. Input
		- 4.1.1. User control
			- a. The microcontroller must be able to receive commands for the thrusters from the RC controller
			- b. The microcontroller must check the commands from the RC controller regularly for changes
			- c. The microcontroller must process the commands into signals to send to the thrusters
			- d. The microcontroller must be able to receive a signal informing of control delegation (autonomous or manual)
			- e. The microcontroller must be able to respond to a killswitch and stop processes immediately 
		- 4.1.2. Jetson control
			- a. The microcontroller must be able to receive inputs from the Jetson's USB-C port as commands for the thrusters
			- b. The microcontroller must be able to inform the Jetson when SV is in autonomous mode or not
 	- 4.2. Output
		- 4.2.1. Thrusters
			- a. The microcontroller must be able to send commands to the thrusters that are acceptable for the ESCs
		- 4.2.2. State (Traffic light)
			- a. The microcontroller must know which state SV is in at the current moment - Autonomous, Manual, Off (?)
			- b. The microcontroller must display this through controlling a relay for the 'Traffic Light'
		- 4.2.3. Diagnostic System
			- a. The microcontroller must be able to send the thruster controls (from jetson or RC) to the Diagnostic System
5. Physical Layout - Ezra, Sandy
	- 	5.1. The design and placement of the components/subsystems on the boad shall be modular.
		- 	5.1.1. All parts shall be easy to access and remove
 			- 5.1.1.1. Server rack like system - further research required?
			- 5.1.1.2. layered racked system - further research required?
			- 5.1.1.3. Seperate box system - like alex said?
  		- 5.1.2. Subsystems shall be positioned such that their nature is visually distinguishable
			- 5.1.2.1. Subsystems shall be colour coded
			- 5.1.2.2. Subsystems shall be placed in positions that do not overlap and have clear seperation
		- 5.1.3. Internal components shall placed in positions that minimise interference and clutter

	- 5.2. The mechanical connections of subsystems and components to the boat shall be secure.
		- 5.2.1. All ICs, cables and components shall remain connected and in place during normal operation
		- 5.2.2. Mechanical stresses induced by vibration, corrosion, heat etc. shall be minimised
			- 5.2.2.1. Dampening systems shall be used where required to reduce stresses on securely connected pieces.
		- 5.2.3. Wiring connections shall be secure.
			- 5.2.3.1. Cables/wires which will not require diconnection for maintainance (and are not on a PCB) shall be soldered or otherwise fixed in place
			- 5.2.3.2. Cables/wires which do require disconnection for maintenance shall use safe and reliable terminal connectors (screw terminals etc., NOT dupont or a breadboard :(. Fuck dupont cables).

	- 5.3. The wiring organisation on the boat shall be considered.
		- 5.3.1. Shorter signal paths shall be prioritised.
		- 5.3.2. Shielding shall be present over cable connections where possible.
		- 5.3.3. The wiring shall be self-documenting.
			- 5.3.3.1. All cables shall be colour coded with a standardised, well documented system
			- 5.3.3.2. Stickers/Labels shall be placed on key/large cables and on cables that are frequently disconnected for maintenance
		- 5.3.4. The wiring shall be organised in a manner which minimises interference
			- 5.3.4.1. High voltage cables (especially high frequency) shall be considerably positioned from information cables (maximally far, or shielded, or wrapped around ground etc.).
			- 5.3.4.2. Cables shall be arranged in forms that reduce parasitic capacitance/inductance and other forms of energy loss.
		- 5.3.5. The wiring shall not be cluttered.
			- 5.3.5.1. The wiring shall be organised, w good cable management.
			- 5.3.5.2. The wiring shall not interfere or coincide with any moving/potentially damaging parts (fans, hot parts etc.)
   
	- 5.4. Cooling
		- 5.4.1. Main box(es) shall maintain standard operating temperature (-5°C to 45°C)
		- 5.4.2. ESCs are able to maintain standard operating temperature (-5°C to 65°C)
			- 5.4.2.1. ESC Compartment shall be made of a reflective material
			- 5.4.2.2. Need to asses need or possibility for active cooling (passive heatsinks + active airflow)?
   
	- 5.5. Waterproofing
		- 5.5.1. All cable connections passing in/out of housing compartments shall have waterproof cables glands
		- 5.5.2. Any boxes or compartments used to house electric components will be waterproof
		- 5.5.3. Components that are not in a waterproof compartment will be waterproofed themselves

