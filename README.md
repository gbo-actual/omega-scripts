# omega-scripts
Quick utility scripts for working with the Onion Omega.

## Compatibility

These are `bash` scripts intended for use on Linux. If you want to use these on Mac, they will most likely work; if not, they should only need very minor tweaks for certain commands.

**I don't have a Mac to play with, so pull requests are welcome! :)**

## Installation

Clone the repo somewhere to your computer. Then make these executable:

``` bash
chmod +x omega-*
```

Then run them from the repo or add the repo to your PATH: https://askubuntu.com/questions/60218/how-to-add-a-directory-to-the-path

## Usage

### omega-serial

Used to connect to Omegas over serial (Expansion Dock, Mini Dock only).

Enter the device number of the Omega to which you wish to connect. The numbers start at 0 and (typically) go up in the order you plugged them in.

If no argument specified, will try to connect to the first (or only) USB serial device available (`/dev/ttyUSB0`).

``` bash
omega-serial            # /dev/ttyUSB0
omega-serial 2          # /dev/ttyUSB2
```

### omega-ssh

Used to connect to Omegas over SSH (required for Power Dock, Arduino Dock, Breadboard Dock).

For use with Omegas whose hostnames follow the default pattern below:

`omega-ABCD.local`

Where `ABCD` are the last 4 digits of the Omega's MAC address. On Omega2s, these will be printed in **bold** on a sticker on both the box and the unit itself.

If no argument specified, will print an error message and exit.

``` bash
omega-ssh 2821          # omega-2821.local
```



### omega-upload

Uploads the current directory into the `/root` folder of the target Omega. Same arguments and usage as `omega-ssh`.

Good for testing or throwing an app/repo onto the Omega.

``` bash
omega-upload 5F4E       # root@omega-5F4E.local:/root
```