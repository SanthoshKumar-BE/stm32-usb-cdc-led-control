STM32 USB CDC LED Control
A simple STM32 project that demonstrates USB CDC (Communication Device Class) functionality for controlling an LED via serial commands.
🚀 Features

USB Virtual COM Port: STM32 appears as a serial device on your computer
LED Control: Turn LED ON/OFF using simple text commands
Real-time Feedback: Get confirmation messages for each command
Plug & Play: No additional drivers needed on most modern systems

🔧 Hardware Requirements

STM32F103 development board (or compatible)
LED connected to GPIO pin (configurable)
USB cable for connection to PC

📋 Software Requirements

STM32CubeIDE or compatible development environment
STM32 HAL Library
USB Device Library (CDC class)
Serial terminal software (PuTTY, Tera Term, Arduino IDE Serial Monitor, etc.)

🛠️ Setup & Configuration
1. Hardware Connections

Connect LED to the designated GPIO pin (check LED_GPIO_Port and LED_Pin in code)
Connect STM32 to PC via USB

2. STM32CubeMX Configuration

Enable USB Device functionality
Configure USB as CDC (Communication Device Class)
Set up GPIO pin for LED output
Configure system clock for USB operation

3. Build and Flash

Open project in STM32CubeIDE
Build the project
Flash to your STM32 board

🎮 Usage
1. Connect to Serial Port

Connect STM32 to your computer via USB
Open Device Manager (Windows) to find the COM port number
Open your preferred serial terminal application
Connect to the COM port with any baud rate (USB CDC ignores baud rate)

2. Available Commands

ON - Turns the LED ON
OFF - Turns the LED OFF

3. Expected Behavior
STM32 is Ready to Receive Data
> ON
Turning ON LED
> OFF
Turning OFF LED
📁 Project Structure
├── Core/
│   ├── Src/
│   │   ├── main.c              # Main application logic
│   │   ├── usbd_cdc_if.c       # USB CDC interface implementation
│   │   └── ...
│   └── Inc/
│       ├── main.h
│       ├── usbd_cdc_if.h
│       └── ...
├── USB_DEVICE/
│   └── ...                     # USB device stack files
└── README.md
🔍 Key Functions
main.c

toggleLED(): Processes ON/OFF commands and controls LED
main(): Initializes hardware and handles command processing loop

usbd_cdc_if.c

CDC_Receive_FS(): Handles incoming USB data
CDC_Transmit_FS(): Sends data back to PC via USB

⚠️ Troubleshooting
Initial Message Not Appearing
If "STM32 is Ready to Receive Data" doesn't show up:

Try increasing the initial delay in main.c
Ensure your serial terminal is connected before the message is sent
Send the first command (ON/OFF) to verify connection

LED Not Responding

Check GPIO pin configuration in STM32CubeMX
Verify LED wiring and polarity
Ensure commands are sent as plain text without extra characters

USB Not Recognized

Install STM32 VCP drivers if needed
Try a different USB cable (ensure it's data-capable)
Check USB device configuration in STM32CubeMX

🛡️ Code Safety Features

Buffer overflow protection
Null termination safety for string operations
USB busy state checking before transmission
Proper memory management for received data

🔄 Extending the Project
This basic framework can be extended to:

Control multiple LEDs
Add more complex commands
Implement sensor data logging
Create a simple command-line interface
Add PWM control for LED brightness

📜 License
This project is provided as-is for educational and development purposes. Feel free to modify and use in your own projects.
🤝 Contributing
Feel free to submit issues, fork the repository, and create pull requests for any improvements.
📞 Support
If you encounter any issues or have questions about this project, please open an issue in the GitHub repository.

Happy coding! 🎉
