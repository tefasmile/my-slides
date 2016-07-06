# Herramientas Frontend

![Herramientas Frontend](http://bextlan.com/img/para-cursos/es6-logo.jpg)

## Índice
1. [Introducción](link a las slides)
1. [Node.js](#nodejs)
1. [NPM](#npm)
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

### NPM CLI

Inicializar un proyecto npm

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
				
* []()
* []()
* []()

**[⬆ regresar al índice](#Índice)**