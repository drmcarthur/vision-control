## Pixhawk Firmware Mods for Vicon Position Control ##

### ADD FILES ###
*	src/modules/mc_vicon_pos_control/mc_vicon_pos_control.cpp
  *	Used …modules/mc_pos_control as a starting point
*	src/modules/mc_vicon_pos_control/modules.mk
  *	Used …modules/mc_pos_control/modules.mk as starting point
*	src/modules/vicon_receiver/vicon_receiver.c
  *	Custom app to receive vicon data via XBee on Serial 5
  * In the future, will use mavlink. Sample code for starting mavlink on SERIAL4 (see “pixhawk.org/firmware/apps/mavlink” for more details:
    *	mavlink stream -d /dev/ttyS6 -s CUSTOM_STREAM_NAME -r 50
 * src/modules/vicon_receiver/modules.mk
	- see ‘modules.mk’ above...

### MODIFY FILES ###
 * makefiles/config_px4fmu-v2_default.mk
	- Add mc_vicon_pos_control under Vehicle Control


### BUILD CODE ###
* First time (use -j6 to run builder with 6 threads):
  *	cd /path/to/Firmware
  * make archives
  * make
  * make -j6 upload px4fmu-v2_default
* Subsequent builds:
  * make -j6 upload px4fmu-v2_default