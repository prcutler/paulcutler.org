# SongMatrix

##  Project Overview

This project uses a USB microphone plugged into a Raspberry Pi to record a 10 second audio sample every three minutes.  That sample is then sent to Shazam for identification and sends a MQTT message with the artist name and song title.  The MQTT message is received by an Adafruit S3 MatrixPortal which scrolls the song information.  The project was [updated in the summer of 2025](https://www.paulcutler.org/posts/2025/08/updating-songmatrix/) and you can now use one or two LED matrices with the Adafruit S3 MatrixPortal.

Source code: [GitHub](https://github.com/prcutler/songmatrix)

## About

I listen to a lot of music.  If I don't have a record on the turntable, I have the [radio](https://thecurrent.org) on in the background.  I'm not a playlist guy - I like to listen to records front to back.  For that reason, I don't always know a lot of the song titles.

I don't remember what sparked the idea, but I vaguely remember it had something to do with a Mastodon toot that I can no longer remember.  And then I came across the `shazamio` Python library, which made half of this project a breeze.  I hacked together in a Friday night the less than twenty lines of code it took to record an audio sample using a microphone and send it to to Shazam for successful identification.

The challenge was with the CircuitPython code.  The MQTT message loop was blocking, causing the scroll to be extremely slow.  Thankfully Tod Kurt shared some code shwoing how to use MQTT with `asyncio`.  From there I did a lot of playing with how I should send and receive the text, using JSON or just a text string and splitting it.  I encountered a bug with JSON and in the end just split the text string.

Overall the project works well except for the occasional MQTT timeout error.  For next steps I need to clean up the code a bit and create a `systemd` service for the Python program running on the Raspberry Pi.

### Parts Needed

- [ ] Raspberry Pi single board computer (Any will do, I'm using an older Raspberry Pi 2 without issue)
- [ ] USB Microphone ([Adafruit](https://www.adafruit.com/product/3367))
- [ ] Adafruit MatrixPortal (Should work on either the newer [S3](https://www.adafruit.com/product/5778) or older [M4](https://www.adafruit.com/product/4745))
- [ ] Adafruit 32x64 RGB Matrix panel (I'm using a [2.5 pitch panel](https://www.adafruit.com/product/5036)) (1 or 2)
- [ ] [Adafruit IO](https://io.adafruit.com) account
- [ ] (Optional if using two 64x32 panels) [3D printed frame](https://www.printables.com/model/1332041-transit-tracker-frame) from Eastside Urbanism.

### Demo
![Two lines scroll on a RGB matrix, one on top of the other. On the top, the song title, Breathing Underwater, and beneath it, the artist, Metric](480p.gif)

### Credits

* Tod Kurt for sharing some code using MQTT with `asyncio` - it fixed the scrolling blocking problem.
* anecdata for the additional help and troubleshooting in the Adafruit Discord
