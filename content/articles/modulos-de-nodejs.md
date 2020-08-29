---
title: Módulos de NodeJS
description: Qué son los módulos de NodeJS y para qué se usan.
img: https://res.cloudinary.com/alvarooncode/image/upload/v1598735198/alvarosaavedradiaz/assets/images/18699-15-percent_os3dwk.jpg
alt: Módulos de NodeJS

tags: [javascript, nodejs]
---

## ¿Qué son los módules de NodeJS?

Un módulo, o `module`, es simplemente un fichero de JavaScript que contiene código reutilizable. Cada `module` su funcionalidad específica. Podemos pensar en los módulos como en librerías.

Por ejemplo, si quisiéramos separar todo lo relacionado con la entidad `Invitados` de una hipotética app tendríamos que crear un módulo específico para ello. El cual se encargaría de manejar todas las librerías de datos sobre los `Invitados`.

La manera en la que usamos los módulos en NodeJS es mediante `require`, o `import` si usas ECMAScript® 2015 o superior.

```js
// Forma tradicional
var miSuperModulo = require("./modulos/mi-super-modulo");

// ECMAScript® 2015 o superior
import miOtroModulo from "./modulos/mi-otro-modulo.js";
```

Al final del artículo anterior [Primeros pasos con NodeJS](https://alvarosaavedradiaz.com/blog/primeros-pasos-en-nodejs), escribíamos un servidor web simple que también es un `module`.

Hay dos tipos principales de módulos en NodeJS.

## Módulos del core de NodeJS

Los módulos del core son los que están construídos en NodeJS y vienen incluídos con la instalación de NodeJS. Hay un montón de módulos en el core de NodeJS pero por destacar algunos mencionaremos [Debugger](https://nodejs.org/api/debugger.html), [File System](https://nodejs.org/api/fs.html), [HTTP](https://nodejs.org/api/http.html), [Path](https://nodejs.org/api/path.html)
[Process](https://nodejs.org/api/process.html) o [Events](https://nodejs.org/api/events.html).

## Módulos personalizados

Estos módulos son los que creamos nosotros encima de NodeJS. Uno de los puntos fuerte de NodeJS es precisamente el inmenso ecosistema que lo envuelve, en el que podemos encontrar módulos para casi cualquier cosa que necesitemos.

Como ya imaginarás, podemos construir uno nosotros mismos o usar uno de terceros. Dos de los gestores de paquetes más populares son [npm](https://www.npmjs.com/) y [yarn](https://yarnpkg.com/).

¿Quieres saber cuáles son los `modules` más descargados en **npm**? Echa un vistazo [aquí](https://www.npmjs.com/browse/depended).

Nos vemos pronto.

--

Créditos

<a class="credits" href='https://www.freepik.es/fotos/tecnologia'>Foto de Tecnología creado por pressfoto - www.freepik.es</a>
