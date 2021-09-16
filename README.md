# Fully autonomous AI powered drone
This repository contains ready to use and extensively real life tested code for flying advanced quadcopters autonomosly

![Tracking demo gif](https://github.com/sieuwe1/Autonomous-AI-drone-scripts/raw/main/demo_media/flight.gif)

## Hardware 

Our quadcopter is fitted with a [Jetson Nano](https://www.nvidia.com/en-us/autonomous-machines/embedded-systems/jetson-nano/) running advanced AI models and algorithms real time on the edge on the quadcopter itself. This makes our quadcopter able to work fully autonomsly without the need of a data connection to offload heavy workloads. Because of optimizations our algorithms can work in the computational limited environment of the [Jetson Nano](https://www.nvidia.com/en-us/autonomous-machines/embedded-systems/jetson-nano/).

![Drone image](https://github.com/sieuwe1/Autonomous-AI-drone-scripts/raw/main/demo_media/216C5829-F7F0-4B80-9CDA-27B1BF304F7F.jpeg)

![Drone image](https://github.com/sieuwe1/Autonomous-AI-drone-scripts/raw/main/demo_media/F819741B-72A1-48B6-A64A-C11C24E5973E.jpeg)

## Packages

We use these [python](https://www.python.org/) packages to make our drone fly autonomously:

- Jetson Inference from https://github.com/dusty-nv/jetson-inference, install by using [these instructions](https://github.com/dusty-nv/jetson-inference/blob/master/docs/building-repo-2.md)
- OpenCV-python
- NumPy
- Dronekit
- pyserial
- keyboard

Install the packages using the following command:

```sh
python -m pip install --upgrade pip
python -m pip install scikit-build cmake opencv-python numpy dronekit pyserial keyboard
```

## Scripts

### Follow person

The follow person script can autonomously follow a person using a live RGB camera feed and a MobileNet AI model. This model can detect a person and use the centerpoint to calculate the `yaw` commands for the drone. `roll` commands are calculated by using a TF Luna solid state LiDAR. This LiDAR can measure the distance between the person and the drone. Both axis commands are generated using PID controllers.

#### Usage

Ensure the ArduCopter is in guided mode, then execute the following command:

```sh
sudo python3 follow_person_main.py --mode=flight --debug_path=debug/flight1
```

For ArduPilot SITL simulator testing, you can have to set the mode to `test`, this can be done by changing the `--mode` parameter from `flight` to `test`.

Press Q to exit the script, the drone will automatically land. Note: this is currently not working in real flight! Switch ArduPilot to `Loiter` mode and then manually land the drone.

### Data plotter

A script was also made to plot the debug data from the PID controllers.

#### Usage

Execute the following command to debug the data from the PID controllers:

```sh
python3 data_plotter.py
```

Ensure the file name in the script is set to the correct debug file. This can be done by editing the `data_plotter.py` script.

## Note

This project is still under heavy development. All code is experimental so please use the code with caution! We are not responsible for damage to people or property from the usage of these scripts.
