# Getting Started

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
