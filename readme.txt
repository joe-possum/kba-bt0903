
SPP-over-BLE example for BLE SDK 2.11.0

--- how to set up the example ----

1) create "SoC Empty" example for your radio board

2) add the SPP service to the GATT database using BLE GATT Configurator, instructions found in the
   KB article:
    https://www.silabs.com/community/wireless/bluetooth/knowledge-base.entry.html/2017/04/13/spp-over-ble_c_examp-mnoe
   
    Press Generate button after you have completed adding the new service and characteristic to the GATT.
	
   Service UUID value  4880c12c-fdcb-4077-8920-a450d7f9b907
   SPP data : UUID value  fec26ec4-6d71-4442-9f81-55bc21d658d6

2) copy attached files into the project directory:

   app.c (overwrites the default app.c in the soc-empty project)
   spp_client_main.c 
   spp_server_main.c
   spp_utils.c 
   spp_utils.h   
   		   
3) edit the file app.h in the project root directory as follows:

 #define DEBUG_LEVEL 1
 
 (value of DEBUG_LEVEL is changed from 0 to 1)
 
That's it! When you program the application to your development kit, you should see this print at the serial 
output:
>* SPP server mode *

Keeping button PB0 or PB1 pressed during reset will select client mode, in that case the print will be:
>* SPP client mode *
 
-------
