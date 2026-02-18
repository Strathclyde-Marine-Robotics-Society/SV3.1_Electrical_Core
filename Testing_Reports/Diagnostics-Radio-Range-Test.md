# Radio Range and Data Integrity Testing - Diagnostic System
Michael Thompson - 18th Feb 2026

## Test objective
Evaluate the suitability of the "_Holybro SiK Telemetry Radio V3_" for meeting the design requirement 3.2.4 (_"Radio signals must be of sufficient power and appropriate frequency to be reliably received at 500m with line-of-sight (to shore)."_)

## Test method
This method tests if data sent from the telemetry radio can be received intact at a distance from SV3. The method used was as follows:

1. Generate a byte stream consisting of a predicable sequence so that the received data can be verified as intact.
2. Transmit data via the _Holybro SiK Telemetry Radio V3_
3. Recieve data on a matching radio at a distance greater than 500m
4. Verify the sequence is as expected (sequence received with no bytes/packets lost)

## Data sequence
An ascending series of uint32_t integers, starting at 0, were generated using a microcontroller (the RP2040 on a Pico Board was used instead of an arduino as it uses 3V3 logic levels as required by the telemetry radio).
This data type is 4 bytes wide, so was sent as a burst of 4 bytes at a time. The RP2040 uses "little-Endian" format, meaning the least-significant-bytes are sent first.

This was achieved using this simple program (using the C++ SDK for Pico).

```Cpp
#include <stdio.h>
#include "pico/stdlib.h"
#include "hardware/uart.h"

int main()
{
    stdio_init_all();

    uint actual_baud = uart_init(uart0, 57600);

    gpio_set_function(0,GPIO_FUNC_UART);
    gpio_set_function(1,GPIO_FUNC_UART);

    uint32_t packet_no = 0;

    while (true) {
        uart_write_blocking(uart0,reinterpret_cast<const uint8_t*>(&packet_no),sizeof(packet_no));
        packet_no++;
        sleep_ms(2);
    }
}

```

It can be verified that the data is received without losses if the received sequence consists of consecutive numbers. A python script running on a laptop connected to the receiving radio's USB port was used to verify this.

## Test setup

The transmitting radio and Pico were placed in an East-facing window of the 13th floor of the Livingston Tower.
<img width="1279" height="963" alt="image" src="https://github.com/user-attachments/assets/78ef04fd-1823-40f9-9afd-dd52ead4f7b1" />

I then walked to a point on the Necropolis 690m (straight-line distance), as shown.
<img width="2291" height="1535" alt="digimap_roam" src="https://github.com/user-attachments/assets/191c5374-66f8-4c5a-96b3-7312d8fb52a7" />

I then repeated the test at just over 1km (1020m straight-line distance). Note that line-of-sight was slightly obstructed by buildings.
<img width="2293" height="1542" alt="digimap_roam(1)" src="https://github.com/user-attachments/assets/5cbac0bf-93f9-4e1a-8ad2-05231013e5f2" />

## Results
Data was received at 690m with no lost or corrupted packets. 53281 uint32_t numbers were received during the short test, which is 213,124 bytes (213.124KB).

Testing at 1km was not required in order to meet the design requirements, but it gave an indication of limits. The data stream could be received without losses if the receiving radio was held up at head-height, although some packets were lost when moving it around.
This is likely worsened by the buildings in the way.

## Conclusions
This test shows that the _Holybro SiK Telemetry Radio V3_ satisfies the design requirement 3.2.4 and for the purposes of near-shore communications within the normal operating distance of SV3, the radio should perform reliably.
As it is possible for data to be lost or corrupted in transmission, the design of the packets must include checksums for verifying data integrity.
