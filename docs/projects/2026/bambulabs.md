# circuitpython-bambulabs

## Project Overview

The `circuitpython-bambulabs` is a library to query your Bambu Labs 3D printer and retrive the JSON response in easy to use methods. The user does not need to worry about setting up MQTT, which is handled by the library (assuming they've entered the settings correct in `settings.toml`).

- Source code: [https://github.com/prcutler/circuitpython-bambulabs](https://github.com/prcutler/circuitpython-bambulabs)
- ReadtheDocs: [https://circuitpython-bambulabs.readthedocs.io/](https://circuitpython-bambulabs.readthedocs.io/)

## About

I follow [todbot](https://github.com/todbot) on GitHub and one day he starred the [BambuHelper](https://github.com/Keralots/BambuHelper) application, which was written in Arduino. That got me thinking that if it could be done in Arduino, it could be done in CircuitPython. I started out building my own project to parse the JSON and display it on a Qualia board, but after giving it some thought, I created a library that just parses the JSON response. This way users can build their own user interfaces depending on the microcontroller and display they have, whether it's a Qualia display, LED Matrix, or a Reverse-TFT Feather.

The MQTT setup is all handled by the library, the user just needs to update their `settings.toml` with their printer settings (which does require some hoops to jump through.) You can [read more about the library in this blog post](https://www.paulcutler.org/blog/2026/03/29/bambu-labs-circuitpython-library/).

This was also the first CircuitPython library I've written and contributed to the [CircuitPython Community Bundle](https://circuitpython.org/libraries).

## Usage

To install using `circup`: `circup install circuitpython-bambulabs`

An example on how to use the library and print to serial the percentage complete of an active print job:

`printer = bl.BambuPrinter(device_id)`
`printer.connect()`

`status = printer.pushall()`

`print(status.print_percentage)`

To print all the raw JSON returned from the printer:

`print(json.domps(status.raw))`

For a full list of commands, [see the documentation](https://circuitpython-bambulabs.readthedocs.io/).

## Demo

![Qualia showing Bambu Labs stats in real-time](qualia.jpeg)

## Credits

Inspired by the BambuHelper application and a number of other GitHub projects that communicate with a Bambu Labs 3D printer. A special thank you to todbot for helping me refactor the MQTT code to make it build in CI.

This library was written with the assistance of Claude.  (I know, I know.)
