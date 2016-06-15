# ECMAScript 6
# aka ES6 o ES2015

![ECMAScript 6](http://bextlan.com/img/para-cursos/es6-logo.jpg)

## Índice
1. [ECMAScript](#ecmascript)
1. [Características ECMAScript 6](#características-ecmascript-6)
	1. [Variables de bloque y constantes](#variables-de-bloque-y-constantes)
	1. [Plantillas de cadenas de texto](#plantillas-de-cadenas-de-texto)
	1. [Números octales y binarios](#números-octales-y-binarios)
	1. [](#)
	1. [](#)
	1. [](#)


## ECMAScript

* ECMAScript es el nombre del estándar internacional que define JavaScript
* Definido por un comité técnico (TC-39) de ecma international.
* Identificado como Ecma-262 y ISO/IEC 16262
* No es parte del W3C
* La versión actual es la ES6 o [ECMAScript 2015](http://www.ecma-international.org/ecma-262/6.0/)

--------------------------------------------------
| Edición | Publicación | Cambios |
| ------- | ----------- | ------- |
| 1 | 1997 |  Primera edición |
| 2 | 1998 |  Cambios editorales para mentener la especificación completa alineada con el estándar internacional ISO/IEC 16262 |
| 3 | 1999 |  Se agregaron expresiones regulares, mejor manejo de strings, nuevo control de declaraciones, manejo de excepciones con try/catch, definición más estricta de errores, formato para la salida numérica y otras mejoras |
| 4 | Abandonado | La cuarta edición fue abandonada debido a diferencias políticas respecto a la complejidad del lenguaje. Muchas características propuestas para la cuarta edición fueron completamente abandonadas; algunas fueron propuestas para la edición ECMAScript Harmony |
| 5 | 2009 | Agrega el modo estricto `strict mode`, un subconjunto destinado a proporcionar una mejor comprobación de errores y evitar constructores propensos a errores. Aclara varias ambigüedades de la tercera edición, y afina el comportamiento de las implementaciones del "mundo real" que difieren consistentemente desde esa especificación. Agrega algunas nuevas características, como getters y setters, librería para el soporte de JSON, y una más completa reflexión sobre las propiedades de los objetos |
| 5.1 | 2011 | Está completamente alineada con la tercera edición del estándar internacional ISO/IEC 16262:2011 |
| 6 | 2015 | La sexta edición agrega cambios significativos en la sintaxis para escribir aplicaciones complejas, incluyendo clases y módulos, definiéndolos sémanticamente en los mismos términos del modo estricto de la edición ECMAScript 5. Otras nuevas características incluyen iteradores for/of loops, generadores y generador de expresiones estilo Python, funciones de dirección, datos binarios, colecciones (mapas, sets, mapas débiles), y proxies (metaprogramación para objetos virtuales y wrappers). Al ser la primera especificación “ECMAScript Harmony”, es también conocida como “ES6 Harmony” |
| 7 |  En progreso | La séptima edición está en una etapa muy temprana de desarrollo, pero está orientada a continuar con la reforma del lenguaje, aislamiento de códigos, control de efectos y librerías/herramientas habilitadas desde ES6. Nuevas características propuestas incluyen promesas/concurrencia, matemáticas y datos numéricos mejorados, guards y trademarks (una alternativa al tipado estático), sobrecarga de operadores, value types (first-class number-like objects), nuevas estructuras de registro (registros, tuplas y vectores tipados), pattern matching, y traits |
--------------------------------------------------

**[⬆ regresar al índice](#Índice)**


## Características ECMAScript 6

### Variables de bloque y constantes
### aka let y const

#### Variables de bloque

En ES6 se agrega una nueva forma de definir variables usando la palabra `let`, se diferencia de `var` en que el scope de una variable definida con `let` es, el bloque en el cual se encuentra la variable y no la función.

	(function() {
		'use strict';

		let x = 'Hola kEnAi';
	    
		if(true) {
			let x = 'Hola Jon';
			console.log(x);  // Imprime en consola Hola Jon
		}

		console.log(x);  // Imprime en consola Hola kEnAi

		for (let i = 0; i < 5; i++) {
			console.log(i); // Imprime del 0 al 4
		};
		
		console.log(i); // Imprime Uncaught ReferenceError: i is not defined
	})();

#### Constantes

Una constantes es un tipo **INMUTABLE**, NO puede cambiar una vez definida, se usa la palabra `const` en lugar de `var`, al igual que `let` su scope es de bloque, son tipos de sólo lectura y se le debe asignar un valor en el momento de su declaración. Son referencias inmutables, pero sus valores no necesariamente.

	(function() {
		'use strict';
		
		const DIEZ = 10;
		DIEZ = 5;
		console.log(DIEZ); // Imprime Uncaught TypeError: Assignment to constant variable

		const hola = 'hola mundo';
		hola = 'hola mundo'; // Imprime Uncaught TypeError: Assignment to constant variable

		const PI;
		PI = 3.15; //Imprime Missing initializer in const declaration

		const obj = {};
		obj.prop = 'x';
		console.log(obj); //Imprime { prop: 'x' }
		obj.prop = 'y';
		console.log(obj); //Imprime { prop: 'y' }

		const D = document;
		console.log(D); //Imprime el objeto document
		console.log(D.documentElement); //Imprime el tag <html>
	})();

**[⬆ regresar al índice](#Índice)**


### Plantillas de cadenas de texto
### aka Template Strings

Los template string son una forma más fácil de crear strings con variables en medio o strings multilínea.

	(function() {
		'use strict';

		let saludo = `Hola soy un Template String`;
		console.log(saludo); //Imprime Hola soy un Template String

		//variables en strings
		let nombre = 'Jonathan';
		console.log(`Hola ${nombre}`); //Imprime Hola Jonathan

		//incluso pueden ejecutar funciones o colocar expresiones
		console.log(`Hola ${nombre}, tienes ${30 + 2} años`); //Imprime Hola Jonathan, tienes 32 años

		//strings multilínea
		let mensaje = `No es quien seas en el interior,
		tus actos son los que te definen...
		Batman`;
		console.log(mensaje); 
		//Imprime 
		No es quien seas en el interior,
		tus actos son los que te definen...
		Batman
	})();

**[⬆ regresar al índice](#Índice)**


### Números octales y binarios

	(function() {
		'use strict';

		//octales
		console.log(0o17); //Imprime 15

		//binarios
		console.log(0b100); //Imprime 4
	})();

**[⬆ regresar al índice](#Índice)**