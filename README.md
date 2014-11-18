This codebase was created at the Internet of Things HackDay at AWS re:Invent 2014. It was forked from the AWS Arduino SDK to include AWS client code. This project is paired with a UI; the code for the UI is located at https://github.com/jon918/stall-patrol-ui.

For the HackDay, Jon Bass, Ricardo DeMatos, and myself worked on a project using Spark devices (https://www.spark.io/). Our goal was to provide a device with a motion sensor that updated a database every time it sensed motion. A web UI would query that database to show when motion was detected. You could also flash LEDs on the device from the UI.

What's the point of this? We had the silly idea of making a device that would detect whether or not a bathroom stall was occupied and a UI that would display the current occupancy. If someone was taking too long in the stall, you can ping them using the LEDs on the device to give them a heads up that someone is waiting.

# Getting Started

## Setup dfu-util

Make sure dfu-util is installed and in your path. You can install it with macports. Get macports from their web site, make sure it's in your path and do:

`sudo port install dfu-util`

Then make sure /opt/local/bin is in your path so spark can find dfu-util.

## Credentials

    cp src/creds/keys.cpp.sample src/creds/keys.cpp

Fill in keys.cpp accordingly.

## Running the Project

### Put device in DFU mode

1. Press mode and reset buttons on device at the same time.
1. While holding them both down, release the reset button.
1. Keep your finger on the mode button until the main LED blinks yellow

Your device is now ready to program.

### Compile

    spark compile src/stall-patrol.ino src/**/*.{h,cpp}

This results in a firmware*.bin file such as firmware_1415754493885.bin.

### Upload and Run

    spark flash --usb <firmware file>
    
    # e.g., spark flash --usb firmware_1415754493885.bin
