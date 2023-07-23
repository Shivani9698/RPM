# RPM Measurement of Fan Blade using Arduino

This Arduino sketch measures the RPM (Revolutions Per Minute) of a fan blade using an Arduino board and a sensor. The code calculates the RPM based on the time it takes for a specific point on the fan blade to pass the sensor.

## Requirements

- Arduino board (e.g., Arduino Uno, Arduino Mega, etc.)
- Sensor (e.g., an optical sensor or any other suitable sensor for detecting the fan blade)
- Fan with a known width and radius for the point of detection
- Serial communication tool (e.g., Arduino IDE Serial Monitor)

## Installation and Setup

1. Connect the sensor to the Arduino board. Make sure to connect the sensor output to the specified sensorPin as defined in the code.

2. Adjust the variables in the code to match your specific fan configuration:
   - `wid`: Set the width of the fan blade (adjust according to your fan's blade width).
   - `rad`: Set the radius of the point of detection on the fan blade (adjust according to your fan's configuration).

3. Upload the code to your Arduino board using the Arduino IDE or any compatible development environment.

4. Connect the fan to a power source and start the fan at least 3 seconds before the RPM measurement starts.

## How the Code Works

The code continuously measures the RPM of the fan blade while the Arduino is powered on. It follows these steps:

1. The code waits for the fan to start spinning before initializing the RPM measurement.

2. When the fan blade passes the sensor, the code records the current time as `time_1` and waits for 3 seconds to get a sufficient time interval.

3. After the 3-second delay, the code checks if the sensor is no longer blocked by the fan blade, indicating that the fan blade has moved past the sensor. It then records the current time as `time_2`.

4. The time difference between `time_2` and `time_1` is calculated as `diff`.

5. Using the fan blade width and the time difference, the rotation velocity (vel) is calculated.

6. The total time (tnet) for one rotation of the fan blade is computed based on the rotation velocity (vel) and the radius (rad) of the point of detection.

7. Finally, the RPM (revolutions per minute) is calculated by dividing 60000 (conversion from milliseconds to minutes) by the total time (tnet) for one rotation.

8. The calculated RPM value is then displayed on the Serial Monitor.

## Important Notes

- This code assumes that the fan blade moves past the sensor in a consistent and regular manner. Irregular motion or multiple blades may result in inaccurate RPM measurements.

- Make sure to adjust the `wid` and `rad` variables to match your specific fan configuration for accurate RPM measurements.

- The sensor should be appropriately positioned to detect the fan blade's motion accurately.

- Always exercise caution when working with rotating machinery and ensure proper safety measures are in place.

## License

This code is released under the [MIT License](LICENSE).

## Author

Created by Shivani Raj.
