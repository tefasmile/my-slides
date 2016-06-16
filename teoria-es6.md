# ECMAScript 6
# aka ES6 o ES2015

![ECMAScript 6](http://bextlan.com/img/para-cursos/es6-logo.jpg)

## Índice
1. [ECMAScript](#ecmascript)
1. [Características ECMAScript 6](#características-ecmascript-6)
	1. [Variables de bloque y constantes](#variables-de-bloque-y-constantes)
	1. [Plantillas de cadenas de texto](#plantillas-de-cadenas-de-texto)
	1. [Funciones Flecha](#funciones-flecha)
	1. [Objetos literales](#objetos-literales)
	1. [Destructuración](#destructuración)
	1. [Números octales y binarios](#números-octales-y-binarios)
	1. [](#)
	1. Promises
	1. Classes
		1. Herencia
		1. Métodos estáticos
		1. Getters y setters
	1. Strings Methods
	1. Replacing IIFEs with Blocks
	1. Destructuring
	1. Parametros por defecto
	1. Parametros rest
	1. Operador de Propagación
	1. Módulos
	1. 
	1. Objeto Math
	1. Métodos de Arrays
	1. Métodos de Object
	1. Símbolos
	1. Iteradores
	1. Generadores
	1. Colecciones
	1. Proxies
	1. Reflection
	1. Decoradores
	1. Funciones async
	1. Map, Weakmap, Set, Weakset
1. Babel 


# ECMAScript

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


# Características ECMAScript 6

## Variables de bloque y constantes
## aka let y const

### Variables de bloque

En ES6 se agrega una nueva forma de definir variables usando la palabra `let`, se diferencia de `var` en que el scope de una variable definida con `let` es, el bloque en el cual se encuentra la variable y no la función.

```JavaScript
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
```

### Constantes

Una constantes es un tipo **INMUTABLE**, NO puede cambiar una vez definida, se usa la palabra `const` en lugar de `var`, al igual que `let` su scope es de bloque, son tipos de sólo lectura y se le debe asignar un valor en el momento de su declaración. Son referencias inmutables, pero sus valores no necesariamente.

```JavaScript
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
	console.log(D.documentElement); //Imprime el elemento <html>
})();
```

**[⬆ regresar al índice](#Índice)**


### Plantillas de cadenas de texto
### aka Template Strings

Los template string son una forma más fácil de crear cadenas con variables dentro (interpolación), generar cadenas multilínea, ejecutar expresiones, funciones y etiquetados.

```JavaScript
(function() {
	'use strict';

	let saludo = `Hola soy un Template String`;
	console.log(saludo); //Imprime Hola soy un Template String

	//strings multilínea
	let mensaje = `No es quien seas en el interior,
	tus actos son los que te definen...
	Batman`;
	console.log(mensaje); 
	//Imprime 
	No es quien seas en el interior,
	tus actos son los que te definen...
	Batman

	//variables en strings (interpolación)
	let nombre = 'Jonathan';
	console.log(`Hola ${nombre}`); //Imprime Hola Jonathan

	//ejecutar expresiones
	console.log(`Hola ${nombre}, tienes ${30 + 2} años`); //Imprime Hola Jonathan, tienes 32 años

	//ejecutar funciones
	let estaciones = ['Primavera', 'Verano', 'Otoño', 'Invierno'],
		ol = `<ol>
			${
				estaciones.map(function (estacion) {
					return `<li>${estacion}</li>`;
				}).join('')
			}
		</ol>`;
	
	console.log(ol); //Imprime <ol><li>Primavera</li><li>Verano</li><li>Otoño</li><li>Invierno</li></ol>

	//función de etiquetado
	const etiqueta = function (cadena, variable) {
		console.log(cadena);
		console.log(variable);
		console.log(cadena[0] + variable);
	};

	let nombre = 'Jon';

	etiqueta`Hola ${nombre}`;
})();
```

**[⬆ regresar al índice](#Índice)**


### Funciones Flecha

### aka Arrow Functions

Es una nueva forma de definir funciones, hay distintas variantes en la sintaxis:

#### Función de un solo parámetro

Al crear una arrow function de un solo parámetro no es necesario escribír los paréntesis, tampoco es necesario escribír las llaves, esto se puede cuando la función es de una sola línea y devuelve un valor.

```JavaScript
(function() {
	'use strict';
	
	//Antes
	var saludo = function (nombre) {
		return 'Hola ' + nombre;
	};
	console.log( saludo('Jonathan') ); //Imprime Hola Jonathan

	//Ahora
	let saludo = nombre => `Hola ${nombre}`;
	console.log( saludo('Jonathan') ); //Imprime Hola Jonathan
})();
```

#### Función de varios parámetros

Cuando la función tenga más de un parámetro es necesario envolver el nombre de estos entre paréntesis.

```JavaScript
(function() {
	'use strict';
	
	//Antes
	var sumar = function (a, b) {
		return a + b;
	};
	console.log( sumar(10, 9) ); //Imprime 19

	//Ahora
	let sumar = (a, b) => a + b;
	console.log( sumar(10, 9) ); //Imprime 19
})();
```

#### Función sin parámetros

Cuando la función no reciba parámetros también son necesarios los paréntesis.

```JavaScript
(function() {
	'use strict';
	
	//Antes
	var saludo = function () {
		return 'Hola a tod@s';
	};
	console.log( saludo() ); //Imprime Hola a tod@s

	//Ahora
	let saludo = () => `Hola a tod@s`;
	console.log( saludo() ); //Imprime Hola a tod@s
})();
```

#### Función con cuerpo

Cuando la función tiene más de una línea (o no devuelve ningún valor) es necesario utilizar las llaves.

```JavaScript
(function() {
	'use strict';

	//Antes
	var fecha = new Date(),
		hora = fecha.getHours();

	var saludo = function (hr) {
		if (hr <= 5) {
			return 'No me jodas!!!';
		} else if(hr >= 6 && hr <= 11) {
			return 'Buenos días!!!';
		} else if(hr >= 12 && hr <= 18) {
			return 'Buenas tardes!!!';
		} else {
			return 'Buenas noches!!!';
		}
	};

	console.log( saludo(hora) );

	//Ahora
	let fecha = new Date(),
		hora = fecha.getHours();

	let saludo = (hr) => {
		if (hr <= 5) {
			return 'No me jodas!!!';
		} else if(hr >= 6 && hr <= 11) {
			return 'Buenos días!!!';
		} else if(hr >= 12 && hr <= 18) {
			return 'Buenas tardes!!!';
		} else {
			return 'Buenas noches!!!';
		}
	};

	console.log( saludo(hora) );
})();
```

**[⬆ regresar al índice](#Índice)**


### Objetos literales

#### Atajos en la escritura de atributos y métodos

```JavaScript	
(function() {
	'use strict';
	
	//Antes
	var nombre = 'kEnAi',
		edad = 3;

	var perro = {
		nombre : nombre,
		edad : edad,
		ladrar : function () {
			alert('guau guau!!!');
		}
	};

	console.log(perro); //Imprime Object {nombre: "kEnAi", edad: 3}
	perro.ladrar(); //Manda alerta

	//Ahora
	let nombre = 'kEnAi',
		edad = 3;

	const perro = {
		nombre,
		edad,
		ladrar() {
			alert('guau guau!!!');
		}
	};

	console.log(perro); //Imprime Object {nombre: "kEnAi", edad: 3}
	perro.ladrar(); //Manda alerta
})();
```

#### Nombres de atributos y métodos calculados (o computados)
```JavaScript
(function() {
	'use strict';
	
	let nombreAtributo = 'nombre',
		nombreOtroAtributo = 'ad',
		nombreMetodo = 'ladrar';

	const perro = {
		[nombreAtributo] : 'kEnAi',
		[`ed${nombreOtroAtributo}`] : 3,
		[nombreMetodo]() {
			alert('guau guau!!!');
		}
	};

	console.log(perro); //Imprime Object {nombre: "kEnAi", edad: 3}
	perro.ladrar(); //Manda alerta
})();
```

**[⬆ regresar al índice](#Índice)**


### Destructuración

### aka Destructuring

Nuevas formas de asignar valores a Arrays y Objetos. 

```JavaScript
(function() {
	'use strict';

	//Destructuración de Arreglos
	let numeros = [1, 2, 3];

	//sin destructuración
	let uno = numeros[0],
		dos = numeros[1],
		tres = numeros[2];

	console.log(numeros, uno, dos, tres); //Imprime [1, 2, 3] 1 2 3

	//con destructuración
	let [one, two, three] = numeros;

	console.log(numeros, one, two, three); //Imprime [1, 2, 3] 1 2 3

	//Destructuración de Objetos
	let persona = { nombre: 'Jonathan', apellido: 'MirCha' };
	let { nombre, apellido } = persona;

	console.log(persona); //Imprime Object {nombre: "Jonathan", apellido: "MirCha"}
	console.log(nombre); //Imprime Jonathan
	console.log(apellido); //Imprime MirCha

	let datos = { correo: 'jonmircha@gmail.com', telefono: 5566778899 };

	let { correo: email, telefono: phone } = datos;
	
	console.log(datos); //Imprime Object {correo: "jonmircha@gmail.com", telefono: 5566778899}
	console.log(email); //Imprime jonmircha@gmail.com
	console.log(phone); //Imprime 5566778899
})();
```

**[⬆ regresar al índice](#Índice)**


### Tema

### aka Tema

Explicacion

```JavaScript
(function() {
	'use strict';

	
})();
```

**[⬆ regresar al índice](#Índice)**


### Tema

### aka Tema

Explicacion

```JavaScript
(function() {
	'use strict';

	
})();
```

**[⬆ regresar al índice](#Índice)**


### Números octales y binarios

```JavaScript
(function() {
	'use strict';

	//octales
	console.log(0o17); //Imprime 15

	//binarios
	console.log(0b100); //Imprime 4
})();
```

**[⬆ regresar al índice](#Índice)**