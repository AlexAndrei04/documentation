# Guía de uso de JavaScript 💕📓

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

_No sirve si hay una propiedad en el Objeto_

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