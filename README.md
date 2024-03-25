
# ESPhome packages
ESPhome [packages](https://esphome.io/guides/configuration-types.html#packages) are `includes` on steroids. Here is my handy collection of packages distributed into two "categories" being:
* `lib`: reusable components, usually safe to use multiple times per package, for example when you have more than one sensor of the same type.
* `presets`: a bundle of `includes` of common configurations for some boards.

## Usage
1. Read ESPHome [packages' documentation](https://esphome.io/guides/configuration-types.html#packages).
2. Clone this repo under your `esphome` directory
3. Include the packages and presets as needed

## Examples
### Bed sensor with two HX711
```
substitutions:
	name: mb-bedsensor
	friendly_name: "Master Bedroom Bed Sensor"

packages:
	d1_mini: !include presets/d1_mini.yaml
	hx711_left: !include
		file: lib/hx711.yaml
		vars:
			dout_pin: D2
			clk_pin: D1
			scale_name: "Left Side"
			scale_id: left_side
	hx711_right: !include
		file: lib/hx711.yaml
		vars:
			dout_pin: D6
			clk_pin: D5
			scale_name: "Right Side"
			scale_id: right_side
```
### ESP32-WROOM-32 BLE Proxy
```
substitutions:
	name: ble-proxy-living-room
	friendly_name: BLE Proxy (Living Room)

packages:
	esp32_wroom_32u: !include presets/esp32_wroom_32u.yaml
	ble_full: !include lib/ble/ble_full.yaml
```
### [Apollo MSR1](https://github.com/ApolloAutomation/MSR-1) preset
```
substitutions:
	name: apollo-msr-1-alpha
	friendly_name: Apollo MSR-1 (Alpha)
	version: "24.1.10.1"

packages:
	apollo_msr1: !include presets/apollo_msr1.yaml
```