## SparkFun LSM9DS1 Particle Library

Firmware library SparkFun's Photon IMU Shield and the LSM9DS1 Breakout.

About
-------------------

This is a firmware library for [SparkFun's Photon IMU Shield](https://www.sparkfun.com/products/13629).

[![Photon IMU Shield](https://cdn.sparkfun.com//assets/parts/1/1/0/1/6/13629-01.jpg)](https://www.sparkfun.com/products/13629).

The Photon IMU Shield connects the Photon WiFi development board up to an [ST LSM9DS1]() 9DOF IMU - providing it access to an accelerometer, gyroscope, and magnetometer.

Repository Contents
-------------------

* **/doc** - Additional documentation for the user. These files are ignored by the IDE. 
* **/firmware** - Source files for the library (.cpp, .h).
* **/firmware/examples** - Example sketches for the library (.cpp). Run these from the Particle IDE. 
* **spark.json** - General library properties for the Particel library manager. 

Example Usage
-------------------

Include the library, declare an IMU object, and set it up with these snippets of code:

	#include "SparkFunLSM9DS1/SparkFunLSM9DS1.h"

	// Use the LSM9DS1 class to create an object. [imu] can be
	// named anything, we'll refer to that throught the sketch.
	LSM9DS1 imu;

	// SDO_XM and SDO_G are both pulled high, so our addresses are:
	#define LSM9DS1_M	0x1E // Would be 0x1C if SDO_M is LOW
	#define LSM9DS1_AG	0x6B // Would be 0x6A if SDO_AG is LOW

	void setup() 
	{
	  Serial.begin(115200);
	  
	  // Before initializing the IMU, there are a few settings
	  // we may need to adjust. Use the settings struct to set
	  // the device's communication mode and addresses:
	  imu.settings.device.commInterface = IMU_MODE_I2C;
	  imu.settings.device.mAddress = LSM9DS1_M;
	  imu.settings.device.agAddress = LSM9DS1_AG;
	  // The above lines will only take effect AFTER calling
	  // imu.begin(), which verifies communication with the IMU
	  // and turns it on.
	  if (!imu.begin())
	  {
		Serial.println("Failed to communicate with LSM9DS1.");
		Serial.println("Double-check wiring.");
		Serial.println("Default settings in this sketch will " \
					  "work for an out of the box LSM9DS1 " \
					  "Breakout, but may need to be modified " \
					  "if the board jumpers are.");
		while (1)
		  ;
	  }
	}

Check out the example files in the [examples directory](https://github.com/sparkfun/SparkFun_LSM9DS1_Particle_Library/tree/master/firmware/examples) for more guidance.

Recommended Components
-------------------

* [Particle Photon](https://www.sparkfun.com/products/13345)
* [SparkFun Photon IMU Shield](https://www.sparkfun.com/products/13629)


License Information
-------------------

This product is _**open source**_! 

Please review the LICENSE.md file for license information. 

If you have any questions or concerns on licensing, please contact techsupport@sparkfun.com.

Distributed as-is; no warranty is given.

- Your friends at SparkFun.