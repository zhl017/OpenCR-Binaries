# OpenCR_binaries
Collection of binary files for platforms using OpenCR

## How to upload to OpenCR
More info : [ROBOTIS-eManual](https://emanual.robotis.com/docs/en/platform/turtlebot3/opencr_setup/#opencr-setup-2)

1. Connect the OpenCR to the Rasbperry Pi using the micro USB cable.

2. Install rquired packages on the Raspberry Pi to upload the OpenCR firmware.

   ```
   $ sudo dpkg --add-architecture armhf
   $ sudo apt-get update
   $ sudo apt-get install libc6:armhf
   ```

3. Depending on the platform, use either `burger` or `waffle` for the OPECNR_MODEL name.

   ```
   $ export OPENCR_PORT=/dev/ttyACM0
   $ export OPENCR_MODEL=burger_noetic    # change model name what you want to download.
   $ rm -rf ./opencr_update.tar.bz2 && rm opencr_update.tar.bz2
   ```

4. Download the firmware and loader, then extract the file.

   ```
   $ wget https://github.com/zhl017/OpenCR-Binaries/raw/idm-devel/turtlebot3_idm_custom/ROS1/latest/opencr_update.tar.bz2
   $ tar -xvf opencr_update.tar.bz2
   ```

5. Upload firmware to the OpenCR.

   ```
   $ cd ./opencr_update
   $ ./update.sh $OPENCR_PORT $OPENCR_MODEL.opencr
   ```

6. Check terminal show `[OK] jump_to_fw` message, then it done.

## Update log

- ROS1 F/W idm-2.3.8 (2023. Aug. 17th)
  - Add turtlebot3_idm_custom
    
    - Add TB3 ROS1 mecanum example
    - Add TB3 ROS1 fet example

- ROS2 F/W V0.2.1 (2023. Jan. 27th)
  - Fixes TB3 ROS2 Odometry issue fixed (See [here](https://github.com/ROBOTIS-GIT/Dynamixel2Arduino/releases/tag/0.6.2) for more related threads)
