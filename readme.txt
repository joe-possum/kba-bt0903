
SPP-over-BLE example for BLE SDK 2.7.0

--- how to set up the exmaple ----

1) create "SoC Empty" example for your radio board

2) add the SPP service to the GATT database using BLE GATT Configurator, instructions found in the
   KB article:
    https://www.silabs.com/community/wireless/bluetooth/knowledge-base.entry.html/2017/04/13/spp-over-ble_c_examp-mnoe
   
    Press Generate button after you have completed adding the new service and characteristic to the GATT.
	
   Service UUID value  4880c12c-fdcb-4077-8920-a450d7f9b907
   SPP data : UUID value  fec26ec4-6d71-4442-9f81-55bc21d658d6

2) copy attached files into the project directory:

   spp_client_main.c 
   spp_server_main.c
   spp_utils.c 
   spp_utils.h   
   
3) copy serial drivers from SDK installation tree to your project directory:
   source directory: C:\SiliconLabs\SimplicityStudio\v4\developer\sdks\gecko_sdk_suite\v2.1\hardware\kit\common\drivers\
   
   copy following files to your project:
        retargetio.c 
        retargetserial.c 
        retargetserial.h
		   
4) edit the file hal-config.h in the project directory as follows:

 #define HAL_VCOM_ENABLE                   (1)
 
 (value of HAL_VCOM_ENABLE is changed from 0 to 1)
 
5) edit the main.c of your project as follows:

  * add #include "spp_utils.h" in the beginning of main.c
  
  * add following line after gecko_init() and before the infinite while(1) loop in main.c:
  
    spp_main();

  This will start the SPP example main loop instead of running the default main loop of the SoC-empty example.

  
-------
