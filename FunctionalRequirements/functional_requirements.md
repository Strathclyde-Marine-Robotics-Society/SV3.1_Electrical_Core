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
	4.1 Input
		4.1.1 User control
			a. The microcontroller must be able to receive commands for the thrusters from the RC controller
			b. The microcontroller must check the commands from the RC controller regularly for changes
			c. The microcontroller must process the commands into signals to send to the thrusters
			d. The microcontroller must be able to receive a signal informing of control delegation (autonomous or manual)
			e. The microcontroller must be able to respond to a killswitch and stop processes immediately 
		4.1.2. Jetson control
			a. The microcontroller must be able to receive inputs from the Jetson's USB-C port as commands for the thrusters
			b. The microcontroller must be able to inform the Jetson when SV is in autonomous mode or not
 	4.2 Output
		4.2.1 Thrusters
			a. The microcontroller must be able to send commands to the thrusters that are acceptable for the ESCs
		4.2.2 State (Traffic light)
			a. The microcontroller must know which state SV is in at the current moment - Autonomous, Manual, Off (?)
			b. The microcontroller must display this through controlling a relay for the 'Traffic Light'
		4.2.3 Diagnostic System
			a. The microcontroller must be able to send the thruster controls (from jetson or RC) to the Diagnostic System
   
6. Physical Layout - Ezra
	1. Modularity
		1. All parts must be easy to access and remove
			1. Server rack like system - further research required
			2. layered racked system - further research required
		2. Subsystems are positioned such that they can be visually distinguished
		3. Internal components are placed in positions that make them unable to interfere with other systems (Power cables far from ICs)
	2. Security
		1. All ICs, cables and components will remain connected and in place during normal operation
			- Components at risk of vibration or moving will be secured (via reusable zip ties, duct tape, screws, or server rack mechanism mentioned above)
	3. Wiring
		1. Shorter signal paths will be prioritised
		2. Shielding over cable connections where possible
		3. Self-documenting
			1. All cables will be colour coded with a standardised, well documented system
			2. Stickers/Labels will be placed on key/large cables and on cables that are frequently disconnected for maintenance 
	4. Cooling
		1. Main box(es) maintains standard operating temperature (-5°C to 45°C)
		2. ESCs are able to maintain standard operating temperature (-5°C to 65°C)
			1. ESC Compartment will be made of a reflective material
			2. Need to asses need or possibility for active cooling (passive heatsinks + active airflow)?
	5. Waterproofing
		1. All cable connections passing in/out of housing compartments will have waterproof cables glands
		2. Any Boxes or compartments used to house electric components will be waterproof
		3. Components that are not in a waterproof compartment will be waterproofed themselves
