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
	1. Communication
		1. Input
			1. User control
			2. Jetson control
		2. Output
			1. Motors
			2. State (Traffic light)
5. Physical Layout - Ezra
	1. Modular
		1. All parts must be easy to access and remove. 
			- Server rack? Layers?
	2. Security
		1. All parts must not disconnect during a mission. 
			- Critical components must be secured via xyz if needed
	3. Wiring
		1. Prioritise shorter signal paths.
		2. Self-documenting
			1. Colour coding standard
			2. Stickers
		3. Prioritise shielding over cable connections.
	4. Cooling
		1. Main box does not require cooling as of yet
		2. ESC
			1. ESC must not melt in all climates. 
	5. Waterproofing
		1. Cable glands
		2. Box
		3. Components
