

![Austral Ingenieria](https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcQooGo7vQn4t9-6Bt46qZF-UY4_QFpYOeh7kVWzwpr_lbLr5wka)


# Proyecto 32-button-led

### IntroComp - 2022 - EAM


## Secciones

- [Objetivo](#objetivo)
- [Hardware](#hardware)
- [Programa](#programa)
- [platformio.ini](#platformio.ini)
- [Biblioteca](#biblioteca)
- [Constantes](#constantes)
- [WiFi](#wifi)
- [Links](#links)
- [Videos](#videos)


## Objetivo

>   Crear una página de Web residente en el ESP32  
>   Mediante la misma, se podrá prender o apagar un led mediante un único botón.  
>   Por lo tanto, el control que implica es dependiente del estado (stateful)  

## Hardware

  Conectar Anodo de LED a GPIO "LED"  
  Conectar Catodo de LED a un extremo de resistor de 220 ohm  
  Conectar el otro extremo del resistor de 220 ohm a GND  

## Programa

 El programa es una modificación respecto del proyecto _31-web-led_.  

 No se necesita biblioteca adicional, solo las ya incluidas propias de Arduino  
  
  
 Se incluyen los siguientes archivos:  
   (16) _Wifi.h_       [del sistema Arduino]  
   (17) _WebServer.h_  [del sistema arduino]  
   (19) _wifi_ruts.h_  [que se encuentra en este mismo directorio]  

 Macro para mayor legibilidad  
   (21) _HEADING_  

 Creación de objetos:  
   (28) _server_ de tipo _WiFiServer_ en port 80  
   (29) _client_ de tipo _WiFiClient_  

 Variables privadas del módulo  
   (35) _header_ de tipo _String_ para almacenar el pedido del cliente  
   (36) _output_led1_state_ de tipo _String_ inicializada en "off" para guardar el estado actual del LED  

 Definiciones:  
   Aquellas definidas en _platformio.ini_  
   (47) Define _LED_ON_ como el complementario de _LED_OFF_ definido en platformio.ini  

 [49-92] Funciones privadas del módulo:  
   (53-68)   _http_header_ok_: normal HTTP header  
   (70-92)   _take_action_: basado en el mensaje del cliente, prende o apaga el LED  
   (94-135)  _display_html_page_: muestra la página de Web  
   (137-163) _message_form_client_: lee caracter por caracter del cliente  

 [165-201] Funciones públicas del módulo  
  [169-179] Función _setup_  
   (172)  Inicializa _Serial_  
   (174)  Programa GPIO "LED" como salida  
   (175)  Apaga el "LED"  
   (177)  Se conecta a WiFi  
   (178)  Pone en funcionamiento el servidor  

  [181-201] Función _loop_  
   (184)  Lee para ver si hay cliente disponible  
   (186)  Verifica si está disponible  
   (188)  Si se recibió un mensaje completo del cliente ...  
   (190)  Se muestra el header 
   (191)  Se procesa la acción  
   (192)  Se muestra la nueva página  
   [194-199]  Se ejecuta en caso de desconexión del cliente  




## platformio.ini

   Se definen tres constantes:

   _LED_OFF_: define si el nivel de apagado es _LOW_ o _HIGH_ dependiendo de como se conecte el LED  
   _LED_: define en qué GPIO está conectado el LED  
   _SERIAL_BAUD_: define el baud rate de la conexión serie haciendola igual a _monitor_speed_  

## Biblioteca

   No se definen bibliotecas externas; existen solamente las del ecosistema Arduino  

## Constantes

   Las declaradas en _platformio.ini_

## WiFi

 Para acceso a WiFi simplificado usado en este proyecto, ver archivo _esp32wifi.md_ en este mismo directorio.

## Links

  Este programa fue tomado de esta página, simplificado a un solo LED y organizado el programa para mayor legibilidad

  [ESP32 Web Server](https://randomnerdtutorials.com/esp32-web-server-arduino-ide/)

## Videos

  [Build an ESP32 Web Server](https://www.youtube.com/watch?v=ApGwxX6VVzk)

