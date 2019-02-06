# rpi-balena

Repository showcasing how to deploy the [rpi-server](https://github.com/gbbirkisson/rpi) to a RaspberryPi running on [balena.io](https://www.balena.io/).

## Setting up a balena project

Follow the [get started](https://www.balena.io/docs/learn/getting-started/raspberrypi3/go/) instructions provided by [balena.io](https://www.balena.io/).

## Deploy rpi to balena

1. Clone this repository: `git clone https://github.com/gbbirkisson/rpi-balena.git`
2. Add balena remote: `git remote add balena <USERNAME>@git.balena-cloud.com:<USERNAME>/<APPNAME>.git`
3. Push to balena: `git push balena master`

## Enabling services

To enable services on [balena.io](https://www.balena.io/) you have to set device configuration and device service variables.

### GPIO

* Device Service variables
    * `RPI_GPIO_ENABLED`: `true`
    * `RPI_GPIO_OPEN`: `true` if you want to open the GPIO pins on startup

### Pi Camera

* Device Configuration
    * `RESIN_HOST_CONFIG_gpu_mem`: `128`
    * `RESIN_HOST_CONFIG_start_x`: `1`
* Device Service variables
    * `RPI_PICAM_ENABLED`: `true`
    * `RPI_MODPROBE`: `bcm2835-v4l2`
    * `RPI_PICAM_OPEN`: `true` if you want to turn on the camera on startup

### Ngrok tunnel

* Device Service variables
    * `RPI_NGROK_ENABLED`: `true`
    * `RPI_NGROK_TOKEN`: `<your ngrok token>`
    * `RPI_NGROK_REGION`: `us` if you want to use a different region 

## Updating rpi version

1. Change `ENV RPI_VERSION="vX.X.X"` in the [Dockerfile.template](./Dockerfile.template) to your desired version.
2. Commit the change: `git commit -am "Update version"`
3. Push to balena: `git push balena master`