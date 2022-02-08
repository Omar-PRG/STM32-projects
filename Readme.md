# Temperature-sensor
In the beginning, we had a program that contains all the STM32 basic sensors (Temperature,pressure,humidity,GYRO). In this project, we removed all the functions related to other sensors in order to make a program that is only related to the temperature one. This simplification shows that we fully understood the main program so that we are able now to write a program for each sensor independently.



						       `		Temperature Program ! :)
				 -------------------------------------------------------------------------------------------------


			In this file we show the different layers of the temperature program.The indent means a function nested in the one just before.
			The following notes show the hierarchical structure of the functions :


			1.Temperature_test(void)
			   1.1 BSP_TSENSOR_init() Initialize the sensor
				1.1.1 SENSOR_IO_Init( initialize I2C communication bus) Low level and tells whether the sensor 
									 is was well initialised or not(it returns TSENSOR_OK)

			   1.2 Serial_Scan(uint32_t value) It's used to get numeric values from hyperterminal(termit) with a maximum value allowed.
				1.2.1 getchar(); It returns tmp which is the value given by the user.
			   1.3 BSP_TSENSOR_ReadTemp return the temperature read thanks to I2C protocol. The value type returned "tsensor_drv" is static.
				1.3.1 ReadTemp(TSENSOR_I2C_ADDRESS) is a float variable that belongs to the TSENSOR_DRV structure, and equal to HTS221_I2C_ADDRESS, 
								    defined in the stm32I475e_iot01.h as (uint8_t)0xBE.	
								    This function reads directly from the bus the temperature values.



				-----------------------------------------------------------------------------------------------

# Wifi client server
Client-server is a relationship in which one program (the client) requests a service or resource from another program (the server). In this project, we try to find the different layers that make up our program. 
The following notes show the hierarchical structure of the functions :
-------------------------------------------------------------------------------
          1_HAL_Init();
          /Reset of all peripherals, Initializes the Flash interface and the Systick.
		
  				2_SystemClock_Config();
 			    /Configure the system clock

					3_BSP_LED_Init(Led2)
					/Configuration de Led2
							
					4_BSP_COM_Init()
			    /enable GBIO,USART CLOCK, TX AND RX alternate functions
					
					5 Wifi_Init
					6 WIFI_GetMAC_Address(MAC_Addr)
					7 wifi_Connect
						7.1 ES_WIFI_Connect()
							7.1.1 AT_ExecuteCommand()
						7.2 ES_WIFI_GetnetworkSettings()
							7.2.1 AT_ExecuteCommand
							7.2.2 AT_ParseConnSettings
					8   WIFI_GetIP_Address()
						8.1 ES_WIFI_IsConnected()
							8.1.1 AT_ExecuteCommand()
							8.1.2 AT_ParseIsConnected()
					9 WIFI_OpenClientConnection
						9.1 ES_WIFI_StartClientConnection
							9.2 AT_ExecuteCommand
				 	10  WIFI_ReceiveData
						10.1 ES_WIFI_ReceiveData
							10.1.1 AT_ExecuteCommand
							10.1.2 AT_RequestReceiveData
					11 WIFI_SendData
						11.1 ES_WIFI_SendData
							11.1.1 AT_ExecuteCommand
							11.1.2 AT_RequestSendData
--------------------------------------------------------------------------
