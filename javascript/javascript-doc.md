# Guía de uso de JavaScript 💕📓

## Tabla de contenido

1. [Attributes](#Attributes)
1. [Console](#Console)
1. [Loops](#Loops)
1. [Array](#Array)
1. [Object](#Object)
1. [Fetch](#Fetch)

## Attributes

### getAttribute()

Obtiene valores de un atributo de un elemento.

```HTML
<h1 class="title title-header" id="title">Hola mundo</h1>
```

```JS
const title = document.getElementById( 'title' )
console.log( title.getAttribute( 'class' ) )

log: title title-header
```

### setAttribute()

Agrega valores a un atributo de un elemento.

```HTML
<h1 class="title title-header" id="title">Hola mundo</h1>
```

```JS
const title = document.getElementById( 'title' )
console.log( title.setAttribute( 'class', 'new-style' ) )

log: title title-header new-style
```

### classList

#### add()

Método para agrega clases.

```HTML
<h1 class="title title-header" id="title">Hola mundo</h1>
```

```JS
const title = document.getElementById( 'title' )
console.log( title.classList.add( 'other-style', 'new-style' ) )

log: title title-header other-style new-style
```

#### remove()

Método para eliminar clases.

```HTML
<h1 class="title title-header" id="title">Hola mundo</h1>
```

```JS
const title = document.getElementById( 'title' )
console.log( title.classList.remove( 'title' ) )

log: title-header
```

#### toggle()

Método para intercambiar clases.

**[[⬆️ Regresar a la Tabla de Contenido]](#tabla-de-contenido)**

## Console

### Log

Muestra información en consola.

```js
console.log( 'Hola mundo' )
```

### Warn

Muestra información en consola en forma de advertencia.

```js
console.warn( 'Hola mundo' )
```

### Danger

Muestra información en consola en forma de error.

```js
console.danger( 'Hola mundo' )
```

**[[⬆️ Regresar a la Tabla de Contenido]](#tabla-de-contenido)**

## Loops

### For

Manera clásica de recorrer un Array.

``` JS
let array = [ 1, 2, 3, 4, 5 ]
for ( let i = 0; i < array.length; i++ ) {
  const element = array[i];
  console.log( element );
}

log: 1, 2, 3, 4, 5
```

### ForIn

Devuelve los nombres de las propiedades de un objeto. Pero devuelve también las propiedades en la cadena de prototipos.



### ForOf

Manera más práctica de hacer un For.

> No puede recorrer un objeto debido a que no es iterable. (No tiene índices)

``` JS
let array = [ a, b, c, d ]
for( element of arr ) {
  console.log( element )
}

log: a, b, c, d
```

### ForEach

Cuando deseemos aplicar una función a cada elemento.

``` JS
let array = [ a, b, c, d ]
array.forEach( (element, i) => {
  console.log( element );
  console.log( i );
});

log: a, 0,  b, 1, c, 2, d, 3
```

**[[⬆️ Regresar a la Tabla de Contenido]](#tabla-de-contenido)**

## Array

### .map(callback)

Transorma todos los elementos del array.

_Ejemplo: Arreglo que se multiplica por si mismo._

``` JS
let arrayNumbers = [ 2, 4, 6, 7 ]
let arrayResult = arrayNumbers.map( el => el * el )

console.log( arrayResult )
[ 4, 16, 36, 49 ]
```

### .filter(callback)

Filtra los elementos que cumplan con la condición.

_Ejemplo: Arreglo que busque números mayor a 5._

``` JS
let arrayNumbers = [ 2, 4, 6, 7 ]
let arrayResult = arrayNumbers.filter( el => el > 5 )

console.log( arrayResult )
[ 6, 7 ]
```

### .reduce(callback)

Reduce todos los elementos a un solo valor.
El callback necesita de 2 valores.

_Ejemplo: Suma de todo los números del arreglo._

``` JS
let arrayNumbers = [ 2, 4, 6, 7 ]
let arraySum = arrayNumbers.reduce( ( a, b ) => a + b )

console.log( arrayResult )
19
```

## Eliminar valores duplicados

Los objetos **Set**, es una colección de valores. Únicamente un valor puede estar una vez

⚠️ Cuando se utiliza Set, se van a convertir en un objeto. Para eliminar el duplicado y siga en Array, agregarle el **Spread Operator**.

``` JS
const numbers = [ 2, 4, 6, 7, 5, 2 ]
new Set( numbers )

console.log( arrayResult )
{ 2, 4, 5, 6, 7 }
```

## Spread Operator

Agregando el operador **...**

``` JS
const numbers = [ 2, 4, 6, 7, 5, 2 ]
[..new Set( numbers )]

console.log( arrayResult )
[ 2, 4, 5, 6, 7 ]
```

**[[⬆️ Regresar a la Tabla de Contenido]](#tabla-de-contenido)**

## Object

_Ejemplo de un object._

``` JS
let perro = {
  nombre: 'Chilaquila',
  edad: 1,
  color: 'black',
  sexo: 'female',
  vacunas: true,
  correr() {
    console.log( `${ this.nombre } corre` )
  }
}

console.log( perro.nombre );
Chilaquila

console.log( perro.correr() );
Chilaquila corre
```

_Las propiedades de los objetos deben ser sin espacios o números, en caso de que tengan se deben encomillar y se imprime de la siguiente manera_

``` JS
let user = {
  nombre: 'Andrei',
  'ed-ad': 24,
}

console.log( user[ 'ed-ad' ] )
24 // Imprime la edad con notación de corchete.
```

### Agregar o quitar elementos a un objeto

_Para eliminar contenido de la siguiente_

``` JS
let user = {
  nombre: 'Andrei',
  edad: 24,
}

delete user.nombre

console.log( user )

let user = {
  edad: 24,
}
```

_Para agregar contenido_

``` JS
let user = {
  edad: 24,
}

user.nombre = 'Andrei'
user[ 'titulo' ] = 'Lic.'

console.log( user )

let user = {
  nombre: 'Andrei'
  edad: 24,
  titulo: 'Lic.'
}
```

### Operador __in__

_Nos sirve si hay una propiedad en el Objeto_

``` JS
let user = {
  edad: 24,
}

console.log( 'edad' in user )
true
```

_Para encontrar todas las propiedades de un Objeto exceptuando las que se puedan heradad es con __hasOwnProperty___

``` JS
let user = {
  name: 'Alex Andrei',
  age: 24,
  country: 'México'
}

for ( let prototype in user ) {
  if( user.hasOwnProperty( prototype ) ) console.log( prototype )
}
```

### Object.entries()

Devuelve como arrays cada una de las entradas del objeto (propiedad, valor).

### Object.keys()

Devuelve un object (array like) con todas las propiedades.

### Object.values()

Devuelve los valores del objeto.

**[[⬆️ Regresar a la Tabla de Contenido]](#tabla-de-contenido)**

## Fetch

Manipulación de peticiones y respuestas, también proporciona una manera práctica y lógica de obtener recursos de forma asíncrona.

_Necesita obligatoriamente de un argumento, la URL y devuelve un objeto Promise conteniendo la respuesta en "response" y para extraer la contenido se utiliza el método **json()**._

_Para saber si la petición no fue encontrada, se utiliza el catch(). En caso que no encontrará un 404, la condicional lanzará el error con el estatus._

``` JS
fetch('https://jsonplaceholder.typicode.com/usedasadrs')
  .then( response => {
    if ( !response.ok) {
      throw Error( response.status )
    }
    return response.json()
  })
  .then(json => console.log(json))
  .catch(error => console.log(`Hubo un error con la petición Fetch: ${error.message}`))
```

**[[⬆️ Regresar a la Tabla de Contenido]](#tabla-de-contenido)**