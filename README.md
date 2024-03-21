# Freenove ESP32-S3-WROOM custom ESPHome camera component

The default camera component that ships with ESPHome won't work with the
Freenove ESP32 camera-enabled microcontroller.  Thanks to the work of
@MichaKersloot, this component exists and is now updated to work with
the latest ESPHome.  Notably, the `on_image` event from the ESP32
camera component is now supported.

Derived from: https://github.com/MichaKersloot/esphome_custom_components/

Usage in a sketch:

```yaml
# Example configuration entry
esp32:
  board: esp32-s3-devkitc-1
  framework:
    type: arduino
    version: 2.0.7  # needed for this board.

# ...

external_components:
  - source:
      type: git
      url: https://github.com/Rudd-O/esphome_freenove_camera_component
    components: [ esp32_camera ]

esp32_camera:
  external_clock:
    pin: GPIO15
    frequency: 20MHz
  i2c_pins:
    sda: GPIO4
    scl: GPIO5
  data_pins: [GPIO11, GPIO9, GPIO8, GPIO10, GPIO12, GPIO18, GPIO17, GPIO16]
  vsync_pin: GPIO6
  href_pin: GPIO7
  pixel_clock_pin: GPIO13

  # Image settings
  name: My Camera
```
