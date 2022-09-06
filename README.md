# Flow5-NodeRed-API
Este repositorio contiene el ejercicio del flow 5 de NodeRed, basandose en el contenido de Internet de las cosas de [Codigo IoT](http://edu.codigoiot.com "Codigo IoT")

## Introducción
Este flow consisten en un tablero que representa en forma de gráficos,  la información de temperatura y humedad locales. Para ello se recibe información con la ayuda de un API en [openweathermap.org](https://openweathermap.org/api "openweathermap.org")
## Material necesario
- [Ubuntu 20.04](https://releases.ubuntu.com/20.04/ "Ubuntu 20.04")
- [NodeJS](https://nodejs.org/es/ "NodeJS")
 - [NPM](https://www.npmjs.com/ "NPM")
 - [NodeRed](https://nodered.org/ "NodeRed")
 - [Nodos de Dashboard](https://flows.nodered.org/node/node-red-dashboard "Nodos de Dashboard")
- [Mosquito MQTT](https://mosquitto.org/ "Mosquito MQTT")
- [Cuenta en OpenWeather](https://openweathermap.org/ "Cuenta en OpenWeather")

## Referencias
Enlaces de apoyo para las configuraciones:
- [Instalación de Virtual Box y Ubuntu 20.04](https://edu.codigoiot.com/course/view.php?id=812 "nstalación de Virtual Box y Ubuntu 20.04")
- [Instalación de NodeRed](https://edu.codigoiot.com/course/view.php?id=817 "Instalación de NodeRed")
- [Introducción de NodeRed](https://edu.codigoiot.com/course/view.php?id=278 "Introducción de NodeRed")
- [Introducción a Mosquitto](https://edu.codigoiot.com/course/view.php?id=851 "Introducción a Mosquitto")
- [APIs de OpenWather](https://openweathermap.org/api "APIs de OpenWather")

## Instrucciones
### Requisitos previos
1. **Instalación de NodeJS. **Se recomienda tener instalado NodeJS en alguna versión LTS. Al momento de creación de este documento, se usó la versión 16.17.0LTS. Esta instalación debe incluir las Build-Tools para hacer uso de NPM
2. **Instalación de NodeRed.**La instalación se realiza por NPM. Al momento de la creación de este contenido, se usó la versión 3.0.2
3. **Instalación de nodos node-red-dashboard.** Para ello, dirigete a la opcion "Manage Palet" de NodeRed y en la pestaña Install busca node-red-dashboard. Finalmente haz clic en instalar.
4. **Instalación de Broker local Mosquitto MQTT.**
5. **Cuenta de OpenWeather.** Es necesario tener una cuenta creada en OpenWeather, la cual nos proporcionará la información de temperatura y humedad.
6. **Coordenadas (latitud y longitud) de algún lugar. **
7. **Usar HiveMQ como broker público**

### Intrucciones de preparación del entorno
1. Arrancar NodeRed con el comando `node-red`
2. Importar el flow desde el repositorio
3. Agregamos un nodo inject y un http request
4. Actualizar la IP del broker público.
5. Hacer clic en el boton Deploy.

### Intrucciones de operación
- Para observar el resultado del flow, es necesario abrir un navegador  y dirigirse a localhost:1880/ui
- Con la API que obtenemos en la documentación `https://api.openweathermap.org/data/2.5/weather?lat={lat}&lon={lon}&appid={API key}`, colocamos las coordenadas de latitud en (lat) y longitud en (lon), así como la API key que obtenes al crear la cuenta en OpenWeather.
- Para poder actualizar la IP del broker público, utilizamos el comando `nslookup broker.hivemq.com` (aunque podemos utilizar cualquier broker público ).
- Colocamos la URL en el nodo http request.
- En el inject (timestamp) configuramos el intervalo para que este mande un mensaje cada minuto al nodo http request.
- Cambiamos los nodos de function con el siguiente código `msg.payload = msg.payload.main.temp;`
### Notas

Fue necesario que varios usuarios se conectaran al broker HiveMQ, así todos estarían enviando datos del clima de su localidad cercana (o cualquier localidad de referencia).

### Resultados y Evidencias
**Nodos del flow**
![](https://github.com/HilarioBarcenas/flow5-NodeRed-Clima/blob/main/Capturas%20de%20pantalla/NodosFlow5.png?raw=true)

**Tablero resulado del flow**
![](https://github.com/HilarioBarcenas/flow5-NodeRed-Clima/blob/main/Capturas%20de%20pantalla/DashboardFlow5.png?raw=true)

**Tablero resultado del flow público con múltiples usuarios**
![](https://github.com/HilarioBarcenas/flow5-NodeRed-Clima/blob/main/Capturas%20de%20pantalla/DashboardFlow5P%C3%BAblico.png?raw=true)

### Evidencias

[YouTube](https://www.youtube.com/watch?v=F3Sx-XV14Nk "YouTube")

### Créditos
**Desarrollado por** `Hilario Barcenas`
[Github](https://github.com/HilarioBarcenas "Github")