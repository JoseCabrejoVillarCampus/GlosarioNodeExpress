
<img src="img/nodejs-1-logo.svg" alt="MySQL Logo" width="100">

Node es un entorno de ejecución de código Javascript de lado del servidor.
Node utiliza un modelo de E/S sin bloqueo y basado en eventos. Esto significa que puede manejar muchas solicitudes simultáneamente sin bloquear el flujo de ejecución.

## Caracteristicas

Permite ejecutar a Javascript desde el servidor
Tiene su modelo E/S sin bloqueo basado en eventos
Arquitectura orientada a módulos
Tiene una amplica comunidad y ecosistema
Es un lenguaje escalable por lo que puede manejar proyectos grandes


### CONFIGURACIÓN DE NODE:

NVM: o Node Version Manager es una herramienta que permite gestar las diferentes versiones de node. Con NVM se pueden cambiar, instalar o actualizar la versiones de Node.

Es importante entender que con NVM podemos trabajar con las versiones LTS, que son las versiones con soporte a largo plazo de node.
-> Para instalar NVM en linux tenemos que instalar el CURL con:

```
sudo apt install curl
```

-> Descarga el script de instalación de NVM utilizando el siguiente comandos:

```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh
```

->Luego lo ejecutamos:

```
source ~/.bashrc

```

### INSTALACIÓN DE NODE

```
nvm list-remote
nvm install v18.16.0
```
---



<img src="img/2560px-Npm-logo.svg.png" alt="MySQL Logo" width="100">

NPM significa Node Package Manager, es el administrador de paquetes predeterminado para node.js.

Node permite:
Instalar paquetes: librerias, frameworks, o cualquier tipo de código.
Gestionar dependencias: En el archivo "package.json" se encuentra información sobre las dependencias requeridas para el proyecto, el nombre del paquete y su versión
Actualizar paquetes: Actualiza los paquetes a sus versiones más recientes
Publicar tus propios paquetes.
Npm se instala automáticamente junto con NODE.JS

Para instalar el archivo packege.json usamos:

```    
npm init -y
```


## ES modules

Conocido también como ECMAscript Modules o ES6 Modules, son una forma estandar de organizar y compartir código js. Sirven tanto en navegadores web como en entornos del servidor.

## Caracteristicas:

Asíncrono y basado en promesas: Su principal virtud es que es asíncrono y no es bloqueante
Sintaxis import/export: Los módulos ES utilizan una sintaxis para importar y exportar archivos.
    //Si mi archivo se exporta por default no hay necesidad de usar llaves {  } en el import
    import nombre_que_le_otorgo from "ruta_específica_al_archivo"
Para configurar ECMAscript en nuestro proyecto y no usar commonJS toca especificar en el package.json que el tipo será modular. type: "module"

Modulo readline de NODE.js
El módulo readline de Node.js es una utilidad que proporciona una interfaz para leer datos de una secuencia de entrada, como la entrada estándar (stdin). Permite leer datos de forma interactiva desde la consola y responder a ellos en tiempo real.

El módulo readline ofrece varias funcionalidades útiles, como:
Leer datos línea por línea: Puedes utilizar el método createInterface para crear una interfaz de lectura y escritura, y luego usar el método on('line') para leer cada línea de entrada a medida que se ingresa. Esto es útil para construir aplicaciones interactivas donde necesitas procesar datos de entrada de manera incremental.
Realizar preguntas y obtener respuestas: Puedes utilizar la función question de la interfaz de lectura y escritura para hacer una pregunta al usuario y recibir su respuesta. Esto es útil para construir interfaces de línea de comandos interactivas.
Autocompletar: El módulo readline también proporciona funcionalidad de autocompletado. Puedes usar el método setCompleter para establecer una función de autocompletado personalizada que se ejecutará cuando el usuario presione la tecla de tabulación. Esto es útil para ofrecer sugerencias o completar automáticamente ciertos comandos o entradas.
Cuando necesite esta herramienta el link de la documentación oficial de la libreria es: https://nodejs.org/docs/latest-v18.x/api/readline.html

---

<img src="img/nodemon.svg" alt="MySQL Logo" width="100">

es una herramienta de desarrollo para aplicaciones Node.js que facilita la tarea de reiniciar automáticamente la aplicación cuando se detectan cambios en los archivos del proyecto.

Nodemon cuenta con varios puntos a su favor así como:

Su reinicio automático
Soporte amplio y una comunidad amplia de desarrolladores
Detalles de reinicio controlados
Integración de scripts personalizados
configuración flexible
su modo silencioso
Su instalación en el proyecto es super sencilla: se busca la ruta donde está en package.json en la terminal y se escribe

```
npm i -E -D nodemon
```

Una vez instalado, nos dirigimos al packege.json y el atributo "scripts" le ponemos:
    
    "scripts": {
        "dev": "nodemon ./rutaArchivoAejecutar.js"
    }

Luego iniciamos en la consola
    
    ```
    npm run dev
    ```

nodemon todo el tiempo estará observando cuando realicemos cambios en nuestro archivo seleccionado.

Para activar el modo silencioso:
    
    ```
    "scripts": {
        "dev": "nodemon --quiet ./app.js"
    }
    ```

---

# REQUEST HTTP

Es un objeto proporcionado por el módulo http o https que representa la solicitud HTTP recibida por el servidor. Proporciona información sobre la solicitud realizada por el cliente, como la URL, los encabezados, los parámetros de consulta y el cuerpo de la solicitud.

El objeto request se pasa como argumento a la función de controlador de solicitud cuando se maneja una solicitud HTTP en el servidor. A través de este objeto, puedes acceder a los detalles de la solicitud y tomar decisiones basadas en ellos.

usualmente se envía como req y estos son sus propiedades más relevantes:

req.url -> da la url de la solicitud
req.method -> de información sobre el método usado en la solicitud
req.body -> Es el cuerpo de la solicitud, la data que se envía mediante un put y un post
req.headers
req.params -> los parámetros de la ruta, usualmente se usa para los id en los endpoints
usualmente se usa el res para enviar datos de respuesta que pueden ser interpretados como un mensaje cuando se completa un evento, si no se envía un res.end() o un ***res.send()***y se aliza una solicitud esta se quedará procesando hasta que se cumpla un tiempo en el servidor.

Si en un futuro esto interesado en consumir la api de asteroides de la nasa para realizar el programa que plantea la documentación esta seria la url para el fetch https://api.nasa.gov/neo/rest/v1/feed?start_date=2023-07-11&end_date=2023-07-13&api_key=VTgdKeFvhhGlRnL0W4NjgQ2qXuFXcDpPkbw4XFh5

---

### EXPRESS
Express es un framework de desarrollo de aplicaciones web para Node.js que simplifica la creación de servidores web y el manejo de rutas, solicitudes y respuestas HTTP. Proporciona una capa de abstracción sobre el servidor HTTP incorporado de Node.js, lo que hace que sea más fácil y rápido crear aplicaciones web.

Express permite:

Enrutamiento
Middleware: es donde se pueden agregar funciones intermedias, para crearle una capa de seguridad extra al código. Donde autentica, manipula solicitudes y respuestas antes de que llegue al controlador final.
Gestión de vistas
Integración con servicios y recursos externos
Para usar express solo hay que instalarlo al igual que nodemon:

    ```
    npm i -E express
    ```

Para usar express solo hay que importarlo en los archivos que lo necesiten y si se desea guardar el poder de la función importada solo se tiene que guardar en una constante

import express from 'express';

const express = express();
Express crea rutas de manera muy sencilla para fines visuales se creará un endpoint /api/conExpress

```
express.get('/api/conExpress', (req,res)=>{
    res.send("Api con express");
})
```

//en mi archivo de configuración:

```
let config = {
    hostname: "localhost",
    port: 5005
}
```

express.listen(config, ()=>{
    console.log(`servidor http://${config.hostname}:${config.port}/api/conExpress`);
})

---

## Middleware

los middleware pueden realizar diferentes tareas como:
Modificar los objetos de solicitud y respuesta
realizar validaciones
autenticar usuarios
administrarsesiones
registrar información de registro
comprimir o cifrar datos

---

## Router

un router es una forma de organizar y gestionar las rutas de una aplicación web de manera modular. Los routers permiten agrupar rutas relacionadas y sus respectivos controladores en un lugar específico.

Un router en Express es un objeto que proporciona métodos para definir rutas y gestionar las solicitudes HTTP asociadas a esas rutas. Puedes utilizar variosrouters en una aplicación Express para dividir y organizar las rutas en diferentes módulos o archivos.

Usar routers es una forma de hacer más ordena el código y más legible. Se crea una carpeta llamada routes y luego se agregan todos los archivos js necesarios para el enrutamiento de la api

---

## VARIABLES DE ENTORNO 'dotenv'

Son variables específicas del entorno en el que se ejecuta una aplicación. Son datos sensibles,configuraciones personalizadas u otros datos relevantes para la aplicación.


Instalamos la dependencia dotenv:

```
    npm i -E dotenv
```

Luego creamos nuestro archivo .env(q ira en gitignore)

```
MY_CONFIG={"hostname": "", "port":}
MY_CONNECT={"host":"localhost","user":"","database":"","password":"","port":}
```

Luego nuestro exampleenv(pra guiar a los desarrolladores)

```
MY_CONFIG={}
MY_CONNECT={}
```

---


# CONECCIÓN A MySQL

Esta conexión se puede hacer con diferentes dependencias.

## mysql2

Es un paquete de node que permite manejar mysql pero con algunas mejoras y optimizaciones.


Instalamos:

```
 npm i -E mysql2
```

Una vez finalizado ya podemos importarla en nuestro proyecto.

Ejemplo de como se utiliza la extención:

    import mysql from 'mysql2';

    //Primero en nuestro archivo de variables de entorno se debe ingresar un objeto con los datos de conexión a la base de datos, esos datos son sencibles, por lo que hacerlo directamente como lo estoy explicando no es correcto y puede generar vulnerabilidades.
    const conexion = mysql.createPool({
        host: 'localhost',
        user: 'root',
        password: '',
        database: 'nombre_baseDeDatos'
    })
    
    // Luego se usan estas credenciales con la librería importada
    conexion.query(
        /*sql*/ `SELECT * FROM nombre_baseDeDatos.nombretabla`,
        (err, res, file)=>{
            console.log(res);
        }
    )
Hay muchas posibilidades para realizar consultas, select, post, put, update usando esta librería.


## Tecnologias Implementadas

<div>
<img src="img/nodejs-1-logo.svg" alt="MySQL Logo" width="100">
<img src="img/Unofficial_JavaScript_logo_2.svg.png" alt="MySQL Logo" width="100">
<img src="img/mysql-logo.svg" alt="MySQL Logo" width="100">
<img src="img/nodemon.svg" alt="MySQL Logo" width="100">
<img src="img/Typescript_logo_2020.svg.png" alt="MySQL Logo" width="100">
<img src="img/2560px-Npm-logo.svg.png" alt="MySQL Logo" width="100">
</div>

# Dependencias Implementadas

Express
class-transformer
reflect-metadata
mysql2
dotenv
nodemon
typescript

# Instalacion Completa Para Proyectos

Inicializamos en consola
```
npm init -y
```
instalamos nodemon
```
npm i -E -D nodemon
```
instalamos express
```
npm i -E -D express
```
instalamos dotenv
```
npm i -E -D dotenv
```
instalamos mysql2
```
npm i -E -D mysql2
```
instalamos class-transformer
```
npm i -E -D class-transformer
```
instalamos reflect-metadata
```
npm i -E -D reflect-metadata
```
instalamos typescript
```
npm i -E -D typescript
```

## Configuracion del .env

```
MY_CONFIG={"hostname": "", "port":}
MY_CONNECT={"host":"localhost","user":"","database":"","password":"","port":}

```

## Configuracion del tsconfig

```
{
    "compilerOptions":{
        "target":"es6",
        "module":"ES6",
        "moduleResolution":"node",
        "outDir":"./dtocontroller",
        "esModuleInterop":true,
        "experimentalDecorators":true,
        "emitDecoratorMetadata": true
    }
}
```
