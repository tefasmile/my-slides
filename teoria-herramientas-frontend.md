# Herramientas Frontend

![Herramientas Frontend](http://bextlan.com/img/para-cursos/es6-logo.jpg)

## Índice
1. [Introducción](link a las slides)
1. [Node.js](#nodejs)
1. [NPM](#npm)
1. [Paquetes NPM](#paquetes-npm)
Sistemas de Automatización
Web Performance Optimization
Preprocesadores
Git & GitHub, MarkDown

## Node.js
![Node.js](http://bextlan.com/img/para-cursos/nodejs-new-pantone-black.png)

* [nodejs.org](https://nodejs.org/)
* [¿Qué es Node.js?](http://jonmircha.github.io/slides-nodejs/#/7)
* [Modelo Asíncrono y No Bloqueante](http://jonmircha.github.io/slides-nodejs/#/20)
* [Características y Ventajas](http://jonmircha.github.io/slides-nodejs/#/35)
* [io.js y el presente futuro de Node.js](http://jonmircha.github.io/slides-nodejs/#/44)
* [Instalación](http://jonmircha.github.io/slides-nodejs/#/57)
* [Más Info](https://www.youtube.com/playlist?list=PLvq-jIkSeTUY3gY-ptuqkNEXZHsNwlkND)

**[⬆ regresar al índice](#Índice)**


## NPM
![NPM](http://bextlan.com/img/para-cursos/npm-logo.png)

### Node Package Manager
[npmjs.com](https://www.npmjs.com/) es el gestor de paquetes de Node.js... y de todo JavaScript

### Iniciar un proyecto npm

```
$ > npm init //Con asistente
$ > npm init -y // Sin asistente
```

### package.json

* Es el archivo de configuración de un proyecto de node.js
* [Configuración del package.json](http://browsenpm.org/package.json)
* [Semantic Versioning](http://semver.org/)

```json
{
	"name": "module-name",
	"version": "10.3.1",
	"description": "An example module to illustrate the usage of a package.json",
	"author": "Your Name <you.name@example.org>",
	"contributors": [{
		"name": "Foo Bar",
		"email": "foo.bar@example.com"
	}],
	"bin": {
		"module-name": "./bin/module-name"
	},
	"scripts": {
		"test": "vows --spec --isolate",
		"start": "node index.js",
		"predeploy": "echo im about to deploy",
		"postdeploy": "echo ive deployed",
		"prepublish": "coffee --bare --compile --output lib/foo src/foo/*.coffee"
	},
	"main": "lib/foo.js",
	"repository": {
		"type": "git",
		"url": "https://github.com/nodejitsu/browsenpm.org"
	},
	"bugs": {
		"url": "https://github.com/nodejitsu/browsenpm.org/issues"
	},
	"keywords": [
		"nodejitsu",
		"example",
		"browsenpm"
	],
	"dependencies": {
		"primus": "*",
		"async": "~0.8.0",
		"express": "4.2.x",
		"winston": "git://github.com/flatiron/winston#master",
		"bigpipe": "bigpipe/pagelet",
		"plates": "https://github.com/flatiron/plates/tarball/master"
	},
	"devDependencies": {
		"vows": "^0.7.0",
		"assume": "<1.0.0 || >=2.3.1 <2.4.5 || >=2.5.2 <3.0.0",
		"pre-commit": "*"
	},
	"preferGlobal": true,
	"private": true,
	"publishConfig": {
		"registry": "https://your-private-hosted-npm.registry.nodejitsu.com"
	},
	"subdomain": "foobar",
	"analyze": true,
	"license": "MIT"
}
```

**[⬆ regresar al índice](#Índice)**


## Paquetes NPM

### Instalación Única

Se instalan en la carpeta donde se encuentre la terminal de comandos, **NO** se registran en el archivo **`package.json`**

```
$ > npm install [nombre del package]
$ > npm install [nombre del package]@3.4.12 // Versión específica
$ > npm i [nombre del package] // shortcut
```

### Instalación como Dependencia del proyecto

Se instalan en la carpeta donde se encuentre la terminal de comandos, **SI** se registran en el archivo **`package.json`** como dependencias del proyecto, esto significa que el proyecto requiere de éstos paquetes para funcionar

```
$ > npm install [nombre del package] --save
$ > npm install [nombre del package] -S // shortcut
```

### Instalación como Dependencia de Desarrollo del proyecto

Se instalan en la carpeta donde se encuentre la terminal de comandos, **SI** se registran en el archivo **`package.json`** como dependencias de desarrollo del proyecto, esto significa que facilitan y optimizan las tareas comunes de desarrollo y publicación del proyecto

```
$ > npm install [nombre del package] --save-dev
$ > npm install [nombre del package] -D // shortcut
```

### Instalación Global

Se instalan localmente en el ordenador independientemente de donde se encuentre la terminal de comandos, esto significa que estarán disponibles en todas las carpetas del ordenador, **NO** se registran en el archivo **`package.json`**

```
$ > npm install [nombre del package] --global
$ > npm install [nombre del package] -g // shortcut
```

### Instalación Múltiple de paquetes

Se pueden instalar múltiples paquetes, separando sus nombres con un espacio en blanco y al final especificar el flag del tipo de instalación

```
$ > npm install [package1] [package2] [package3] --flag
```

### Actualización de paquetes

```
$ > npm update [package]
```

### Desinstalación de paquetes

Si se utiliza el flag **`--save`** o **`--save-dev`** se elimina el registro del archivo **`package.json`**, si se usa **`--global`** se elimina del ordenador

```
$ > npm uninstall [package] // se borra de la carpeta node_modules
$ > npm uninstall [package] --save
$ > npm uninstall [package] --save-dev
$ > npm uninstall [package] --global
$ > npm un [package] // shortcut
```

### Publicación de paquetes
Un paquete no puede volver a re-publicarse con la misma versión. Si despublicas un paquete puedes romper Internet :grimacing:

```
$ > npm publish
```

### Mostrar información de paquetes
Lee metadatos del archivo **`package.json`** del paquete en su repositorio oficial

```
$ > npm view [package]
$ > npm view [package] versions
```

### [Documentación de NPM](https://docs.npmjs.com/)

**[⬆ regresar al índice](#Índice)**