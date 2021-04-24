# Taller TINY GS
Este repositorio contiene el código, información y documentación necesaria para montar un mini-recepor de señal de satélite con modulación LoRa.

El tipo de receptor se basa en los estándares del proyecto [tinyGS](https://github.com/G4lile0/tinyGS) creado por:
- [4m1g0](https://github.com/4m1g0)
- [G4lile0](https://github.com/G4lile0)
- [gmag11](https://github.com/gmag11)

TinyGS se define como una red abierta de estaciones terrestres distribuidas por todo el mundo para recibir y operar satélites LoRa, sondas meteorológicas y otros objetos voladores, utilizando módulos baratos y versátiles.

## Montaje del receptor
<img src="./img/Photo 8-11-20, 12 58 03.jpg" width=600 align="center" />

El procedimiento de instalación está en constante evolucion por lo que voy a señalar los bloques principales sin entrar en detalles. Que si podrás consultar en los enlaces correspondientes.
- dddd
- 

### Mi instalación

(pendiente)

## Dashbord de control (NOC en Node-RED)
[Node-RED](https://nodered.org/) es una herramienta de programación visual. Muestra gráficamente relaciones entre objetos (nodos) que son funciones que transforman el mensaje que les llega de los nodos precedentes. 
Utilizando nodos estándar, el usuario no necesita programar. Aunque si puede quiere, pued crear funciones programando en JavaScript. En definitiva permite, desde un navegador web, construir flujos para procesar información y comunicarla a través de infinidad de integraciones.

Vamos a montar un _dashboard_ que nos permitirá monitorizar hasta dos estaciones TinyGS. Es nuestro NOC personal que nos permitirá:
- Saber qué satélite estamos estamos escuchando. 
- Cual fué el último satélite recibido
- Saber los parámtros de conexión del modem.
- Analizar la señal recibida a través del historico de los indicadores.
- Recibir avisos:
-- Receptor caído. No se conecta a la red WiFi
-- Satélite recibido.

![Node-RED NOC TinyGS dashboard](/nodered/nodered_ui_dashboard4TINYGS.png)

### Node-RED
En primer lugar necesitaremos tener [instalada una instancia de Node-RED](https://nodered.org/docs/getting-started/). La recomendación más actual es la hacerlo en un contetenedor Docker. Pero utilizar una Single Board Computer como la Raspberry Pi es muy adecuado porque los requisitos de capacidad de proceso y memoria son muy bajos.
![Node-RED install options](/nodered/nodered_instalation.png)

También vamos a necesitar algunos 'nodos' adicionales a los que la instalación incluye.
- [node-red-dashboard](https://flows.nodered.org/node/node-red-dashboard) Nos suministra los nodos necesarios para construir el interface del usuario.
- [node-red-contrib-ui-media](https://flows.nodered.org/node/node-red-contrib-ui-media/in/590bc13ff3a5f005c7d2189bbb563976) Nos permite mostrar las imágenes en el Interface de Usuario
- [node-red-node-mysql](https://flows.nodered.org/node/node-red-node-mysql) Nos permitirá acceder a una base de datos MySQL. En nuestro caso para guardar mensajes recibidos.

## IFTTT
Para recibir los avisos vamos a usar el servicio de [If This Then That](https://ifttt.com/home) que se integrará fácilmente en Node-RED usando el nodo de petición HTTP.

```

```

El servicio a configurar es simple. Utilizaremos el componente Webhooks para captar el evento y las notificaciones para que salte el aviso en nuestro dispositivo: móvil, smartwatch...

### Montaje final
Una vez configurado el servidor Node-RED y nuestro evento en IFTTT. Nos queda tres últimos pasos: 
1. Crear la tabla en la BBDD MysSQL:
```

```
2. Importar en Node-RED el fichero [nodered_dashboard4TINYGS.json](/nodered_dashboard4TINYGS.json) que contiene todos los flujos.
3. Configurar las credenciales y hash para acceder a:
-- Servidor MQTT
-- Servidor MySQL
-- Llamada a IFTTT


