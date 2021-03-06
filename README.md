# IoT Hub Intel Edison Client application
[![Build Status](https://travis-ci.com/Azure-Samples/iot-hub-c-intel-edison-client-app.svg?token=5ZpmkzKtuWLEXMPjmJ6P&branch=master)](https://travis-ci.com/Azure-Samples/iot-hub-c-intel-edison-client-app)

> This repo contains the source code to help you get familiar with Azure IoT using the Microsoft IoT Pack for Intel Edison Starter Kit. You will find the [lesson-based tutorials on Azure.com](#).

This repo contains an arduino application that runs on Intel Edison with a Grove temperature sensor, and then sends these data to your IoT hub. At the same time, this application receives Cloud-to-Device message from your IoT hub, and takes actions according to the C2D command. 

## Set up your edison
Follow [this page](#) to set up your edison and enable SSH.

## Build Azure IoT SDK
Clone this repo into your Intel Edison, then navigate to the repo folder to run the following command to build Azure IoT SDK

```bash
sed -i -e 's/\r$//' buildSDK.sh
chmod 755 buildSDK.sh
buildSDK.sh
```

## Connect your sensor with your edison
### Connect with a physical Grove temperature sensor and LED
You can follow the image to connect your Grove temperature sensor and a LED with your Intel Edison.

![Grove temperature sensor](#)

### DON'T HAVE A PHYSICAL Grove temperature sensor?
You can use the application to simulate temperature data and send to your IoT hub.
1. Open the `config.h` file.
2. Change the `SIMULATED_DATA` value from `0` to `1`.


## Running this sample
### Build the sample code
Build the sample code by the following command:

```bash
cmake . && make
```

### Run your client application
Run the client application with root priviledge, and you also need provide your Azure IoT hub device connection string, note your connection should be quoted in the command.

```bash
sudo ./app '<your Azure IoT hub device connection string>'
```

### Send Cloud-to-Device command
You can send a C2D message to your device. You can see the device prints out the message and blinks once receiving the message.

### Send Device Method command
You can send `start` or `stop` device method command to your Pi to start/stop sending message to your IoT hub.