# Temperature-sensor
In the beginning, we had a program that contains all the STM32 basic sensors (Temperature,pressure,humidity,GYRO). In this project, we removed all the functions related to other sensors in order to make a program that is only related to the temperature one. This simplification shows that we fully understood the main program so that we are able now to write a program for each sensor independently.
# Wifi client server
Client-server is a relationship in which one program (the client) requests a service or resource from another program (the server).
In this project, we see how the functions form this program.
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
