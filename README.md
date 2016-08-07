# Equipment Controller

Code for operating benchtop equipment.

The Arduino serial port configuration is:
9600 baud 8N1

# Arduino Port-to-Equipment Mapping
The ports on the Arduino for controlling the equipment relays are mapped as follows:

| Benchtop Equipment | Arduino Pin |
| -------------------|-------------|
| Main Incubator     | A1          | 
| UV Transilluminator| A2          |
| Overhead Lighting  | D2          |
| Shaker             | D3          |
| Electrophoresis    | D4          |
| Centrifuge         | D5          |
| WL Transilluminator| D6          |
| Shaker Incubator   | D7          |


When the equipment controller is initialized, the equipment relays have the following state:

| Benchtop Equipment | Initial State|
| -------------------|--------------|
| Main Incubator     | On           | 
| UV Transilluminator| Off          |
| Overhead Lighting  | On           |
| Shaker             | Off          |
| Electrophoresis    | Off          |
| Centrifuge         | Off          |
| WL Transilluminator| Off          |
| Shaker Incubator   | On           |


The keyboard commands to turn each of the equipment relays on and off are as follows:

| Benchtop Equipment | On  | Off |
| -------------------|-----|-----|
| UV Transilluminator| '1' | '0' |
| Overhead Lighting  | '4' | '3' |
| Shaker             | '7' | '8' |
| Electrophoresis    | '9' | 'A' |
| Centrifuge         | '5' | '6' |
| WL Transilluminator| 'B' | 'C' |

The Liquid Handling Robot Computer sends these commands to operate the benchtop equipment,
but these commands can also be send manually.
The Equipment Controller operates the Incubators according to a controller which reads the
temperature of each incubator. They cannot be commanded manually. If necessary, they can be tested
using the [Controller Tester](http://github.com/cclrobotics/lhr-testing/tree/master/controller-tester).
The `Enter` Key (or newline character) does not need to be pressed for a command to take effect,
however, if using the Arduino IDE for serial port communication, the `Enter` Key needs to be
pressed for a command to be sent.
When a command has been received by the Arduino, it will be echoed on the terminal to indicate
receipt of the command.
