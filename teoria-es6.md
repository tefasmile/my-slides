# ECMAScript 6
# aka ES6 o ES2015

![ECMAScript 6](http://bextlan.com/img/para-cursos/es6-logo.jpg)

## Índice
1. [ECMAScript](#ecmascript)
1. [Características ECMAScript 6](#características-ecmascript-6)
	1. [Variables de bloque y constantes](#variables-de-bloque-y-constantes)
	1. [Plantillas de cadenas de texto](#plantillas-de-cadenas-de-texto)
	1. [Funciones flecha](#funciones-flecha)
	1. [Objetos literales](#objetos-literales)
	1. [Destructuración](#destructuración)
	1. [Parámetros por defecto](#parámetros-por-defecto)
	1. [Parámetros rest](#parámetros-rest)
	1. [Operador de propagación](#operador-de-propagación)
	1. [Clases](#clases)
	1. [Promesas](#promesas)
	1. [Métodos clase String](#métodos-clase-string)
	1. [Números octales y binarios](#números-octales-y-binarios)
	1. [Métodos clase Math](#métodos-clase-math)
	1. [](#)
	1. Replacing IIFEs with Blocks
	1. Parametros rest
	1. Módulos
	1. 
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
1. Más Info
	https://kangax.github.io/compat-table/es6/
	http://es6-features.org/


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
### aka let y const

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


## Plantillas de cadenas de texto
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


## Funciones flecha

### aka Arrow Functions

Es una nueva forma de definir funciones, hay distintas variantes en la sintaxis:

### Función de un solo parámetro

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

### Función de varios parámetros

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

### Función sin parámetros

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

### Función con cuerpo

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

	console.log( saludo(hora) ); //Imprime el saludo dependiendo la hora del día

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

	console.log( saludo(hora) ); //Imprime el saludo dependiendo la hora del día

	//Antes
	var numeros = [1, 2, 3, 4];
	
	numeros.forEach(function (num) {
		console.log(num); //Imprime el número en turno
		console.log(num * 10); //Imprime el número en turno por 10
	});

	//Ahora
	let numeros = [1, 2, 3, 4];
	
	numeros.forEach((num) => {
		console.log(num); //Imprime el número en turno
		console.log(num * 10); //Imprime el número en turno por 10
	});
})();
```

### Contexto Léxico de `this`

Las arrow function tienen la capacidad de capturar el objeto `this` del contexto donde la `arrow` se ejecuta y así utilizarlo dentro de su bloque de sentencias

```JavaScript
(function() {
	'use strict';

	//El problema de `this` Antes
	function Persona(nombre) {
		//El constructor Persona() define `this` como una instancia de él mismo
		this.nombre = nombre;
		this.edad = 0;

		setInterval(function () {
			//La función anónima define `this` como una instancia de ella misma
			this.edad++;
		}, 1000);
	}

	var jon = new Persona('Jonathan');
	console.log(jon); //Imprime la edad en 0 por cada segundo que pasa


	//La solución al problema de `this` Antes
	function Persona(nombre) {
		//Se declara una variable self (algunos prefieren that) para guardar el `this` del constructor Persona()
		var self = this;

		self.nombre = nombre;
		self.edad = 0;

		setInterval(function () {
			//La función anónima define su propio `this` pero el valor que aumenta es edad del `this` de Persona()
			self.edad++;
		}, 1000);
	}

	var jon = new Persona('Jonathan');
	console.log(jon); //Imprime el valor de edad más uno por cada segundo que pasa


	//La solución al problema de `this` Ahora
	function Persona(nombre) {
		//El constructor Persona() define `this` como una instancia de él mismo
		this.nombre = nombre;
		this.edad = 0;

		setInterval(() => {
			//`this` hace referencia al objeto Persona()
			this.edad++;
		}, 1000);
	}

	var jon = new Persona('Jonathan');
	console.log(jon); //Imprime el valor de edad más uno por cada segundo que pasa
})();
```

**[⬆ regresar al índice](#Índice)**


## Objetos literales

### Atajos en la escritura de atributos y métodos

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

### Nombres de atributos y métodos calculados (o computados)

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


## Destructuración

### aka Destructuring o Descomposición

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


## Parámetros por defecto

### aka Default Parameters

Ahora es completamente posible definir un valor por defecto a los parámetros de nuestras funciones al igual que en otros lenguajes de programación.

```JavaScript
(function() {
	'use strict';

	//Antes
	function pais(nombre) {
		nombre = nombre || 'Terrestre';
		console.log(nombre);
	}

	pais(); //Imprime Terrestre
	pais('México'); //Imprime México

	//Ahora
	function pais(nombre = 'Terrestre') {
		console.log(nombre);
	}

	pais(); //Imprime Terrestre
	pais('México'); //Imprime México
})();
```

**[⬆ regresar al índice](#Índice)**


## Parámetros rest

### aka Rest Parameters

Los parámetros rest son una forma de utilizar parámetros virtualmente infinitos, se definen agregando **`...`** adelante del nombre del parámetro rest, éste tiene que ser siempre el último parámetro de la función.

```JavaScript
(function() {
	'use strict';

	function sumar(a, b, ...c) {
		
		let resultado = a + b;

		c.forEach(n => {
			resultado += n;
		});

		return console.log(resultado);
	}

	sumar(1,2); //Imprime 3
	sumar(1,2,3); //Imprime 6
	sumar(1,2,3,4); //Imprime 10
	sumar(1,2,3,4,5); //Imprime 15
})();
```

**[⬆ regresar al índice](#Índice)**


## Operador de propagación

### aka Spread Operator

Permite que una expresión sea expandida en situaciones donde se esperan múltiples argumentos o elementos.

```JavaScript
(function() {
	'use strict';

	let arr1 = [1, 2, 3, 4],
		arr2 = [5, 6, 7, 8];

	console.log(arr1); //Imprime [1, 2, 3, 4]
	console.log(...arr1); //Imprime 1 2 3 4

	arr1.push(...arr2);
	console.log(arr1); //Imprime [1, 2, 3, 4, 5, 6, 7, 8]

	let superiores = ['hombros', 'brazos', 'tronco'],
		inferiores = ['pelvis', 'piernas', 'rodillas'],
		cuerpo = ['cabeza', ...superiores, ...inferiores, 'pies'];

	console.log(cuerpo); //Imprime ["cabeza", "hombros", "brazos", "tronco", "pelvis", "piernas", "rodillas", "pies"]
})();
```

**[⬆ regresar al índice](#Índice)**


## Clases

### aka Classes

En ES6 se incorporan al lenguaje clases para poder hacer Programación Orientada a Objetos más facilmente (sin prototipos), soportan herencia, polimorfismo, superclases, instancias, métodos estáticos, constructores, setters y getters.

### Definición de clase, constructor e instancia de objetos

```JavaScript
(function() {
	'use strict';

	class Animal {
		//el constructor es un método especial que se ejecuta en el momento de instanciar la clase
		constructor(nombre, edad, genero) {
			this.nombre = nombre;
			this.edad = edad;
			this.genero = genero;
		}

		//métodos públicos de la clase
		comunicar() {
			console.log('Me comunico con sonidos');
		}

		comer() {
			console.log('Ingiero alimentos');
		}

		respirar() {
			console.log('Respiro oxígeno');
		}

		reproducir() {
			console.log('Me reproduzco sexualmente');
		}
	}

	let lucy = new Animal('Lucy', 20, 'Hembra');
	console.log(lucy); //Imprime Animal {nombre: "Lucy", edad: 20, genero: "Hembra"} 
	lucy.comunicar(); //Imprime Me comunico con sonidos
	lucy.comer(); //Imprime Ingiero alimentos
	lucy.respirar(); //Imprime Respiro oxígeno
	lucy.reproducir(); //Imprime Me reproduzco sexualmente
})();
```

### Herencia, polimorfismo, métodos estáticos, setters y getters

```JavaScript
(function() {
	'use strict';

	//con la palabra extends la clase Humano hereda de Animal
	class Humano extends Animal {
		//el constructor es un método especial que se ejecuta en el momento de instanciar la clase
		constructor(nombre, edad, genero) {
			//con el método super() se manda a llamar el constructor de la clase padre
			super(nombre, edad, genero);
			this.razonar = true;
			this._nacionalidad = 'Terrestre';
		}

		//un método estático se pueden ejecutar sin necesidad de instanciar la clase
		static saludar() {
			console.log('Hola soy un Humano');
		}

		//Los setters y getters son métodos especiales que nos permiten establecer y obtener los valores de atributos de nuestra clase
		set nacionalidad(pais) {
			this._nacionalidad = pais;
		}

		get nacionalidad() {
			return this._nacionalidad;
		}

		//métodos públicos de la clase redefinidos gracias al polimorfismo
		comunicar() {
			console.log('Me comunico hablando');
		}

		comer() {
			console.log('Como de todo, soy omnívoro');
		}

		respirar() {
			console.log('Respiro oxígeno con ayuda de mis pulmones');
		}

		reproducir() {
			console.log('Me reproduzco sexualmente, soy mamífero y vivíparo');
		}

		pensar() {
			console.log('Pienso por que tengo intelecto');
		}
	}

	Humano.saludar(); //Imprime Hola soy un Humano
	let jon = new Humano('Jonathan', 32, 'Macho');
	console.log(jon); //Imprime Humano {nombre: "Jonathan", edad: 32, genero: "Macho", razonar: true, _nacionalidad: "Terrestre"}
	jon.comunicar(); //Imprime Me comunico hablando
	jon.comer(); //Imprime Como de todo, soy omnívoro
	jon.respirar(); //Imprime Respiro oxígeno con ayuda de mis pulmones
	jon.reproducir(); //Imprime Me reproduzco sexualmente, soy mamífero y vivíparo
	jon.pensar(); //Imprime Pienso por que tengo intelecto
	jon.nacionalidad = 'México';
	console.log(jon.nacionalidad); //Imprime México
	console.log(jon); //Imprime Humano {nombre: "Jonathan", edad: 32, genero: "Macho", razonar: true, _nacionalidad: "México"}
})();
```

**[⬆ regresar al índice](#Índice)**


## Promesas

### aka Promises

Es una manera alternativa a las `callbacks` para modelar asincronía

* Construcción explícita del flujo de ejecución
* Separación en bloques consecutivos
* Manejo de errores más controlado
* Combinación de diferentes flujos asíncronos
* [Más info](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)

### Callbacks VS Promesas
![Callbacks VS Promesas](http://bextlan.com/img/para-cursos/callbacks-vs-promise.png)

### Promesas en el navegador

```JavaScript
(function() {
	'use strict';

	function adivinarNumero() {
		return new Promise((resolve, reject) => {
			setTimeout(() => {
				let n = Math.floor(Math.random() * 10);
				
				return (n >= 1 && n <= 5)
					? resolve(`Adivinaste el número: ${n}`)
					: reject(new Error(`No adivinaste el número: ${n}`));
			}, 1000);
		});
	}

	adivinarNumero()
		.then( num => console.log(num) )
		.catch(error => console.log(error) );
})();
```

### Promesas en el servidor

```JavaScript
'use strict';

const fs = require('fs'),
	file = './nombres.txt',
	newFile = './nombres-promises-es6.txt';

let promise = new Promise((resolve, reject) => {
	fs.access(file, fs.F_OK, (err) => {
		return (err) 
			? reject( new Error('El archivo no existe') ) 
			: resolve(true);
	});
});

promise
	.then((dataPromise) => {
		console.log('El archivo existe');
		
		return new Promise((resolve, reject) => {
			fs.readFile(file, (err, data) => {
				return (err) 
				? reject( new Error('El archivo no se pudo leer') ) 
				: resolve(data);
			});
		});
	})
	.then((dataPromise) => {
		console.log('El archivo se ha leído exitosamente');

		return new Promise((resolve, reject) => {
			fs.writeFile(newFile, dataPromise, (err) => {
				return (err)
					? reject( new Error('El archivo no se pudo copiar') ) 
					: resolve('El archivo se ha copiado con éxito');
			});
		});
	})
	.then((dataPromise) => { console.log(dataPromise); })
	.catch((err) => { console.log(err.message); });
```

**[⬆ regresar al índice](#Índice)**


## Tema

### aka Tema

Explicacion

```JavaScript
(function() {
	'use strict';

	
})();
```

**[⬆ regresar al índice](#Índice)**


## Métodos clase String

Nuevos métodos para Cadenas de Texto

* [**`.fromCodePoint()`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/fromCodePoint)
* [**`.codePointAt()`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/codePointAt)
* [**`.startsWith()`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/startsWith)
* [**`.endsWith()`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/endsWith)
* [**`.includes()`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/includes)
* [**`.repeat()`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/repeat)
* [**`.normalize()`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/normalize)
* [**`.raw()`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/raw)

```JavaScript
(function() {
	'use strict';
	
	let nombre = 'Jonathan';

	console.log( nombre.startsWith('jo') ); //Imprime false
	console.log( nombre.endsWith('an')) ; //Imprime true
	console.log( nombre.includes('th')) ; //Imprime true
	nombre.repeat(3); //Imprime JonathanJonathanJonathan
})();
```

**[⬆ regresar al índice](#Índice)**


## Números octales y binarios

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


## Métodos clase Math

Nuevos métodos de la Clase Matemáticas, apto sólo para ñoños XP

* [**`.acosh()`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/acosh)
* [**`.asinh()`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/asinh)
* [**`.atanh()`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/atanh)
* [**`.cbrt()`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/cbrt)
* [**`.clz32()`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/clz32)
* [**`.cosh()`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/cosh)
* [**`.expm1()`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/expm1)
* [**`.fround()`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/fround)
* [**`.hypot()`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/hypot)
* [**`.imul()`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/imul)
* [**`.log10()`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/log10)
* [**`.log1p()`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/log1p)
* [**`.log2()`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/log2)
* [**`.sign()`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/sign)
* [**`.sinh()`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/sinh)
* [**`.tanh()`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/tanh)
* [**`.trunc()`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/trunc)

**[⬆ regresar al índice](#Índice)**