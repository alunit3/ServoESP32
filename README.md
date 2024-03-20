# ServoESP32

![GitHub Release](https://img.shields.io/github/v/release/alunit3/ServoESP32)


Generate RC servo signal on a selected pins with ESP32 device and Arduino framework, fixed support for latest ESP32 core
i made this repo "fork" for personal use, and i will not guarantee any support or updates

Base on [RoboticsBrno ServoESP32 Library](https://github.com/RoboticsBrno/ServoESP32).

## Interface

The interface is similar to Arduino/Servo: https://www.arduino.cc/en/Reference/Servo

But the function `attach()` is different:

```c
bool attach(
    int pin,
    int channel = CHANNEL_NOT_ATTACHED,
    int minAngle = DEFAULT_MIN_ANGLE,
    int maxAngle = DEFAULT_MAX_ANGLE,
    int minPulseWidthUs = DEFAULT_MIN_PULSE_WIDTH_US,
    int maxPulseWidthUs = DEFAULT_MAX_PULSE_WIDTH_US,
    int frequency = DEFAULT_FREQUENCY
);
```

More information in [source code documentation](src/Servo.h).

Example: [04-SimpleServoAngles](examples/04-SimpleServoAngles/04-SimpleServoAngles.ino)

There are also a ServoFloat and ServoDouble variant available. Use one of these when working in radians. 

Example: : [05-SimpleServoRadians](examples/05-SimpleServoRadians/05-SimpleServoRadians.ino)

### IMPORTANT INFO
According testings, the frequency for ESP32 S2/S3/C3 has to be set at least to 200 Hz. Here is an example, how to set just frequency:

```cpp
Servo servo1;
const int servoPin = 4;
const int frequency = 200; // Hz

servo1.attach(
    servoPin, 
    Servo::CHANNEL_NOT_ATTACHED, 
    Servo::DEFAULT_MIN_ANGLE, 
    Servo::DEFAULT_MAX_ANGLE, 
    Servo::DEFAULT_MIN_PULSE_WIDTH_US, 
    Servo::DEFAULT_MAX_PULSE_WIDTH_US, 
    frequency
);
```

For more information look at the [PR25](https://github.com/RoboticsBrno/ServoESP32/pull/25) 

## PlatformIO

You can use this library with PlatformIO. Just add this line to your `platformio.ini`:

```ini
lib_deps =
    ;
    https://github.com/alunit3/ServoESP32.git
```

## Arduino IDE
You can download the code as a ZIP file and then use the "Add .ZIP Library" feature in the Arduino IDE.
or
You can find the library in the Library Manager in the Arduino IDE, named ServoESP32Fix.