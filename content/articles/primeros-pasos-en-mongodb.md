---
title: Primeros pasos en MongoDB
description: Aprende a crear y a usar bases de datos en MongoDB con este sencillo tutorial.
img: https://res.cloudinary.com/alvarooncode/image/upload/v1597688979/alvarosaavedradiaz/articles/placeholder_f6z0um.png
alt: Primeros pasos en MongoDB

tags: [mongodb]
---

## Arrancando motores 🚀

MongoDB es una base de datos NoSQL que consta de `collections` (tablas o grupos de datos) y `documents` (filas o registros). En este artículo usaremos algunos de los comandos que MongoDB nos ofrece para crear, consultar, modificar y borrar documentos.

Voy a dar por hecho que ya tenemos MongoDB instalado correctamente en nuestro ordenador.

Lo primero de todo es abrir una terminal en nuestro sistema operativo y arrancar el servidor de MongoDB mediante el siguiente comando:

```
$ mongod
```

Tras ello, veremos varios `logs` en la consola emitidos por MongoDB acerca del proceso de arranque. Como es un servicio que se queda escuchando, no nos devolverá el control de la terminal a menos que lo paremos.

A continuación, abriremos otro terminal del sistema operativo y pondremos en marcha la `shell` de MongoDB con este comando:

```
$ mongo
```

Tras mostrarnos la versión de MongoDB que estamos usando así como otros `logs`, la `shell` debería cedernos el control dejando el `prompt` a la espera de nuestras instrucciones. Es aquí donde podemos ver las bases de datos que hayamos creado, si fuera el caso, y las propias que MongoDB necesita para funcionar. Cada base de datos, a su vez, contiene las colecciones (`collections`) y documentos (`documents`) pertinentes.

Para mostrar el listado de las bases de datos que hay, escribiremos en la terminal lo siguiente:

```
> show dbs
```

En mi caso, la `shell` me devuelve esto:

```
admin   0.000GB
config  0.000GB
local   0.000GB
```

Si es la primera vez que arrancamos MongoDB deberíamos ver algo parecido a eso. En esta ocasión, las bases de datos que hay son `admin`, `config` y `local`. Para usar alguna de ellas, escribiremos el siguiente comando:

```
> use <nombre_de_la_base_de_datos_que_queremos_usar>
```

Hay que tener cuidado porque ese comando, en caso de que el nombre de la base de datos aportado no exista, no lanza ningún error. Por el contrario, crea automáticamente una base de datos con ese nombre.

Supongamos que quisiéramos **crear** y directamente **usar** una base de datos para registrar a nuestros **amigos**. El comando para ellos sería:

```
> use amigos
```

Aquí se debe mencionar que dicha base de datos no se registrará como tal hasta que no se le añada algún dato. Si escribiéramos `> show dbs` justo después de `> use amigos` no aparecería en la lista de bases de datos. Así es MongoDB 🤷.

Ahora que ya tenemos nuestra base de datos creada, demos un repaso rápido a los comandos de MongoDB para gestionar los `documents`.

## Añadir registros 📝

El comando `insert` se usa para crear nuevos registros en una `collection`. Añadamos alguno a nuestra base de datos **amigos**. Lo primero sería crear una `collection` en la que almacenar dichos registros, en este caso vamos a crear una colección para alacenar a nuestros amigos de la **infancia**. Para ello, ejecutaremos la siguiente instrucción:

```
> db.infancia.insertOne({
    nombre: 'Manolito',
    desc: 'Manolito fue mi primer amigo de la infancia'
  });
```

Al igual que ocurre con las bases de datos, al añadir un registro a una colección de MongoDB, automáticamente se creará dicha `collection` en caso de que no existiera y después se insertará el dato en la susodicha. Tiene su lado bueno y lado malo, como todo. Agiliza mucho el flujo de trabajo pero puede causarnos un destrozo importante si nos equivocamos.

Justo después de escribir el comando para insertar registros, la `shell` debería devolvernos un **JSON** parecido a este:

```
{
  "acknowledged": true,
  "insertedId": ObjectId("5f107cad6e663f0010ddfa05")
}
```

Cada registro insertado cuenta con un **id** único en MongoDB.

⚠️ Antes de pasar al siguiente apartado, debemos asegurarnos de que tenemos algunos registros en la `collection` **infancia** de la base de datos **amigos**.

A propósito, para cerciorarnos de que estamos usando la base de datos correcta, escribiremos:

```
> db
  amigos
```

Esa instrucción debería devolvernos el nombre de la base de datos que estemos usando en ese momento, que en este caso es **amigos**.

## Consultar registros 📑

El comando para solicitar datos de una colección de una base de datos en MongoDB es `find`. Si repito tanto los términos es para que nos familiaricemos con las palabras clave de Mongo, mis disculpas 😇.

Como es obvio, MongoDB nos permite consultar todos los registros de una colección o sólo aquellos que cumplan una serie de restricciones que nosotros especificaremos en la consulta.

Para solcitar todos los registros añadidos a la colleción **infancia** de la base de datos **amigos** deberíamos usar el siguiente comando:

```
> db.infancia.find();
{"_id":"5f107cad6e663f0010ddfa05","nombre":"Manolito","desc":"Manolito fue mi primer amigo de la infancia"}
{"_id":"5f107cd46e663f0010ddfa06","nombre":"José Ángel","desc":"Mi primer amigo en el colegio"}
```

Un poco complicado de leer, ¿verdad? Probemos a usar la función `pretty()` al final de la consulta:

```
> db.infancia.find().pretty();
{
  "_id": "5f107cad6e663f0010ddfa05",
  "nombre":"Manolito",
  "desc":"Manolito fue mi primer amigo de la infancia"
},
{
  "_id":"5f107cd46e663f0010ddfa06",
  "nombre":"José Ángel",
  "desc":"Mi primer amigo en el colegio"
}
```

¡Mucho mejor así! Ahora podemos leer con más facilidad la salida por consola de MongoDB, que en este caso son dos `documents` los que hay en la `collection` **infancia**.

Si queremos encontrar un `document` concreto, por ejemplo buscando por **nombre**, deberíamos añadir algún parámetro a la consulta:

```
> db.infancia.find({ 'nombre': 'Manolito' }).pretty();
{
  "_id": "5f107cad6e663f0010ddfa05",
  "nombre":"Manolito",
  "desc":"Manolito fue mi primer amigo de la infancia"
}
```

## Modificar registros 📝

Si queremos cambiar el valor de alguna de las propiedades de algún documento, debemos usar el comando `update` y sus derivados. En este caso, vamos a cambiar el valor de la propiedad **desc** del `document` cuyo campo **nombre** es igual a **Manolito**:

```
> db.infancia.updateOne(
  { 'nombre': 'Manolito' },
  {
    $set: { 'desc': 'Manolito fue mi primer amigo de la infancia y no era precisamente pequeño' }
  }
);
```

Si todo va bien, deberíamos ver una salida por consola parecida a esta:

```
{ "acknowledged": true, "matchedCount": 1, "modifiedCount": 1 }
```

Podríamos interpretar ese `log` como que la petición ha sido _admitida_, que había _1 coincidencia_ con la restricción dada y que _ha modificado 1 registro_ con el valor que hemos indicado en la consulta.

## Eliminar registros 🚮

Para cerrar el círculo del **CRUD** que hemos planteado en este artículo vamos a ver cómo eliminar `documents` de una `collection` en MongoDB. Si quiséramos borrar aquellos registros cuya propiedad **nombre** coincidiera con **José Ángel** simplmenete tendríamos que usar este comando:

```
> db.infancia.remove({ 'nombre': 'José Ángel' });
```

Si sólo quisiéramos borrar el primer documento coincidente tendríamos que usar este otro comando:

```
> db.infancia.deleteOne({ 'nombre': 'José Ángel' });
```

Y para borrar todos los registros de una colección, y ojito con esto que no tenemos `ctrl + z`, debemos usar:

```
> db.infancia.remove({});
```

Y ya está. Así de sencillo es trabajar con MongoDB. Obviamente esto es el `a-b-c` y que la cosa va más allá pero a mí me resultó muy sencilla la curva de aprendizaje en comparación con otros gestores de bases de datos.

--

Ojalá este artículo ayude a alguien a iniciarse en esta maravillosa base de datos. Teniendo cierta experiencia con JavaScript nos será muy sencillo adoptar la filosofía y los conceptos de funcionalidad de MongoDB.

Nos vemos pronto.
