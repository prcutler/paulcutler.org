---
title: circuitpython-bambulabs Published!
author: Paul Cutler
type: post
date: 2026-03-30
categories:
  - circuitpython
tags:
  - circuitpython
  - bambulabs
links:
  - blog/posts/2026/2026-03-29-circuitpython-bambulabs-library/index.md
---

Following up on my [blog post from yesterday](https://www.paulcutler.org/blog/2026/03/29/bambu-labs-circuitpython-library/), I spent Sunday preparing the `circuitpython-bambulabs` library to be published.

Unfortunately, I ran into an issue with the CI where it was failing to build.  Thanks to some pointers from todbot, I was able to refactor the library and move the MQTT setup into the `BambuPrinter` class. This makes me happy as the user doesn't have to set up MQTT, assuming they've entered their printer settings in `settings.toml`, the library handles connecting for you.

I also heard from Brent Rubell at Adafruit who confirmed that the MQTT library for CircuitPython uses MQTT 3.1.1 - which is odd, because while MQTTX would connect locally using 3.1.1 (and not 5.0), CircuitPython would not connect locally.  I'll investigate this more as I'm guessing some people would rather connect locally instead of through Bambu Cloud.

Other things I learned:

* The [Creating and sharing a CircuitPython library Learn Guide](https://learn.adafruit.com/creating-and-sharing-a-circuitpython-library/creating-a-library) needs some updates. The process to create docs on ReadtheDocs has changed, libraries use `ruff` now for linting instead of `Pylint` and `black`, and sharing in the Library bundle needs some updates.
* The Learn Guide doesn't cover publishing to PyPi, though the `cookiecutter` template does include the GitHub Actions to publish the library. It took me longer than it probably shoudl to figure out how to enter the secrets in GitHub to allow it to build and upload.  This would be helpful to add to the Learn Guide.
* The section in the Learn Guide on Sharing in a Bundle also needs an update.  The section on verifying didn't work for me, though Updating the Library list did.

Lastly, a big thank you to Foamyguy who merged my pull request to add the library to the Community Libraries right away!  You can find more about the library by:

* Install via `circup`: `circup install bambulabs` to install on your microcontroller. (Just tested it and it's so cool to see that work!)
* [PyPi](https://pypi.org/project/circuitpython-bambulabs/)
* [ReadtheDocs](https://circuitpython-bambulabs.readthedocs.io/en/latest/)
* [GitHub repository](https://github.com/prcutler/CircuitPython_bambulabs) (And if you like it, give it a ⭐️)
