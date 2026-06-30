# mr_interfaces

ROS2 message, service, and action definitions for the Marine Robotics stack.

## Messages

### Sensor data (structured N2K topics)

These messages are used by the `/type/path/data_raw` topics published by `read_n2k`.

| Message | Description |
|---------|-------------|
| `Azimuth` | Directional angle with unit, orientation (ENU/NED), and reference (Magnetic/Geographic/Relative) metadata. Sub-message — no header. |
| `AzimuthStamped` | `Header` + `Azimuth`. Used for heading topics. |
| `PolarVector` | `Header` + `Azimuth direction` + `float64 magnitude`. Used for wind and COG/SOG topics. |
| `GNSSMeta` | GNSS metadata companion to `sensor_msgs/NavSatFix`: fix time, GNSS type, method, integrity, num_sats, HDOP, PDOP, geoidal separation. |

### Legacy messages

These messages are used by the older flat topic names and remain unchanged.

| Message | Used for |
|---------|----------|
| `GNSSData` | `gnss_position` topic |
| `Heading` | Heading data |
| `Declination` | Magnetic declination |
| `ROT` | Rate of turn |
| `Depth` | Water depth |
| `Speed` | Water speed |
| `Wind` | Wind data |
| `Temp` | Temperature |
| `Pressure` | Barometric pressure |
| `Humidity` | Relative humidity |
| `N2KInfo` | N2K device info |
| `ADCReading`, `DigitalReading` | GPIO/ADC sensor readings |
| `NodeStatus`, `NetworkInfo`, `NetworkInterface` | System status |
| `PID`, `ControllerTuning`, `SailControllerSettings`, `RoboclawStatus` | Control |
| `LCD` | Display |
| `Position` | Lat/lon position |

## Services

| Service | Description |
|---------|-------------|
| `ReadGPIO` | Read a GPIO pin state |
| `SetGPIO` | Set a GPIO pin state |
| `StateRequest` | Request node state |

## Actions

| Action | Description |
|--------|-------------|
| `GPIO` | GPIO control action |
| `KeelHoming` | Keel homing sequence |
| `MotorPosition` | Move motor to position |
| `SetPeripheral` | Set peripheral state |
| `Sleep` | Sleep action |
| `TogglePeripheral` | Toggle peripheral state |
