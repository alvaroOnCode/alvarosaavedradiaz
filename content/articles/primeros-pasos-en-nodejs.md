---
title: Primeros pasos en NodeJS
description: Qué es NodeJS y cuáles son sus principales características.
img:
alt: Primeros pasos en NodeJS

tags: [javascript, nodejs]
---

## ¿Qué es NodeJS?

NodeJS es un entorno de ejecución escrito sobre un motor de JavaScript. Es un framework open source, liviano y efeciente usado para trabajar en el lado del servidor. Además, puede ejecutarse desde Linux, macOS y Windows.

Fue creado por Ryan Dahl en 2009. Hasta entonces, JavaScript era usado sobre todo en el lado del cliente pero NodeJS abrió la puerta para que pudiera usarse también en el backend. La llegada de NodeJS trajo consigo el poder desarrollar aplicaciones web completas en un único lenguaje, tanto en el lado del cliente como en el lado del servidor.

Algunos de los puntos fuertes de NodeJS son los siguientes:

- **Programación dirigida por eventos:** Esto significa que el estado de los objectos de JavaScript cambiarán a través de interacciones de usuario tales como un click del ratón o pulsar una tecla.

- **Sin bloqueos:** Esto significa que la aplicación no necesita esperar a que el proceso actual finalice para continuar con la ejecución del código posterior. En otras palabras, NodeJS es asíncrono. Y esto ofrece garantía y rapidez en su ejecución.

- **Único hilo:** Esto significa que todo el código JavaScript de una aplicación NodeJS se ejecuta en un sólo búcle de eventos (event loop). Por lo general, los entornos asíncronos permiten tener varios procesos corriendo en paralelo consecutivamente pero NodeJS gestiona la asincronía de otra forma. El event loop lanza la siguiente función programada cuando ocurra el evento que provoca dicha ejecución.

## Motor V8

NodeJS se ejecuta sobre el motor V8 de JavaScript, creado por _The Chromium Project_ para los navegadores **Google Chrome** y **Chromium**. Es un proyecto open source escrito en C++. Este motor es usado para aplicaciones web escritas en JavaScript tanto en el lado del cliente como en el lado del servidor.

## Programando en NodeJS

Empecemos creado un nuevo proceso de NodeJS. Abramos la terminal y escribamos el siguiente comando:

```
$ node
```

Esto arrancará un nuevo proceso de NodeJS donde podremos escribir código JavaScript. Por ejemplo, probemos a declarar un variable de nombre _autor_ cuyo valor será _'Álvaro'_.

```
> let autor = 'Álvaro';
```

Tras pulsar la tecla enter debe devolvernos _undefined_ pero si escribimos en el prompt el nombre de la variable, en este caso _autor_, debería retornarnos el string _'Álvaro'_.

Además de poder escribir código JavaScript dentro de la `shell` de NodeJS podemos usar el propio comando `node` para ejecutar archivos de tipo _\*.js_.

Por ejemplo, vamos a crear un directorio de nombre _probando-nodejs_ el cual contendrá un fichero llamado _test.js_.

```
$ mkdir probando-nodejs;
$ cd probando-nodejs;
$ touch test.js;
$ node test.js;
```

Al estar vacío el archivo _test.js_, no se nos devuelve nada. Añadamos algo de JavaScript al fichero:

```
console.log('Hello, World!');
```

Y volvamos a ejecutar el archivo con NodeJS:

```
$ node test.js;
```

Ahora sí podemos ver que nos devuelve la cadena _'Hello, World!'_.

Todo esto está muy bien pero lo realmente potente y relevante de NodeJS es que también nos ofrece herramientas para ejecutar un entorno del lado del servidor. NodeJS integra un módulo que nos permite habilitar un servidor HTTP asíncrono. Veamos cómo sería el código para un server que escucha en el puerto _8088_ de nuestro _localhost_:

```
const http = require('http');

const data = {
  port: 8088,
  host: '127.0.0.1'
};

http.createServer(function(req, res) {
  res.writeHead(200, {
    'Content-type': 'text/plain'
  });

  res.end('Hello, World!\n');
}).listen(data.port, data.host);

console.log(`Server running at http://${data.host}:${data.port}`);
```

Lo primero que hemos hecho en este fragmento de código es traernos el módulo _http_ que nos dará acceso a sus funciones definidas y guardarlo en una constante del mismo nombre. Lo segundo que hemos hecho es definir otra constante para almacenar la configuración de nuestro servidor (puerto y host). Después, mediante la función `createServer`, hemos creado un servidor que devolverá como respuesta un código **200** y un texto que no será otro sino el mítico _'Hello, World!'_ cada vez que se haga una petición a la url indicada.

Ahora, volvamos a arrancar el archivo con el comando `node` y veremos que el prompt se queda en ejecución tras lanzar el log:

```
$ node test.js
Server running at http://127.0.0.1:8088
|
```

Ahora es el momento de ver si hemos configurado bien nuestro servidor escrito en NodeJS yendo al navegador y tratando de ir a la dirección _localhost:8088_ o _127.0.0.1:8088_ que, como sabemos, es lo mismo.

Si ves como salida el texto _Hello, World!_ lo has consegido.

Para salir de la aplicación NodeJS pulsaremos `Ctrl+C` dos veces y recuperaremos el control de la terminal.

Nos vemos pronto.
