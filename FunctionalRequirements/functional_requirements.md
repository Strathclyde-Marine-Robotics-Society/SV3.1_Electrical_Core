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
	1. Collection
		1. Sensors
		2. MCU state and commands
		3. BMS 
	2. Transmission
		1. Radio
		2. Ethernet
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
