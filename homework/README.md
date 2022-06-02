
# Homework JavaScript Avanzado I

## Scope & Hoisting

Determiná que será impreso en la consola, sin ejecutar el código.

> Investiga cuál es la diferencia entre declarar una variable con `var` y directamente asignarle un valor.

```javascript
x = 1;
var a = 5;
var b = 10;
var c = function(a, b, c) {
  var x = 10;
  console.log(x); // Devuelve 10
  console.log(a); // Devuelve 8 
  var f = function(a, b, c) {
    b = a; 
    console.log(b); //Devuelve 8 porque b = a 
    b = c;
    var x = 5;
  }
  f(a,b,c);
  console.log(b); // Devuelve 9 
}
c(8,9,10);
console.log(b); // Devuelve 10
console.log(x); // Devuelve 1 
```

```javascript
console.log(bar); // undefined por agarra la variable pero no el contenido
console.log(baz); // baz is not defined
foo();
function foo() { console.log('Hola!'); }
var bar = 1;
baz = 2;
```

```javascript
var instructor = "Tony";
if(true) {
    var instructor = "Franco";
}
console.log(instructor); // Devuelve "Franco" 
```

```javascript
var instructor = "Tony";
console.log(instructor); // Devuelve "Tony "
(function() {
   if(true) {
      var instructor = "Franco";
      console.log(instructor); // Devuelve "Franco "
   }
})();// Funcion autoconvocada
console.log(instructor);// Devuelve "Tony"
```

```javascript
var instructor = "Tony";
let pm = "Franco";
if (true) {
    var instructor = "The Flash";
    let pm = "Reverse Flash";
    console.log(instructor); // Devuelve "The Flash"
    console.log(pm);// Devuelve "Reverse Flash"
}
console.log(instructor); //Devuelve "The Falsh"
console.log(pm); //Devuelve "Franco"
```
### Coerción de Datos

¿Cuál crees que será el resultado de la ejecución de estas operaciones?:

```javascript
6 / "3" // Devuelve 2
"2" * "3"//Devuelve 6
4 + 5 + "px"//Devuelve "9px"
"$" + 4 + 5//Devuelve "$45"
"4" - 2//Devuelve 2 
"4px" - 2//Devuelve NaN
7 / 0//Devuelve Infinify
{}[0]//Devuelve [0]
parseInt("09")//Devuelve 9
5 && 2//Devuelve 2
2 && 5//Devuelve 5
5 || 0//Devuelve 5
0 || 5//Devuelve 5
[3]+[3]-[10]//Devuelve '23'
3>2>1//Devuelve false
[] == ![]//Devuelve true
```

> Si te quedó alguna duda repasá con [este artículo](http://javascript.info/tutorial/object-conversion).


### Hoisting

¿Cuál es el output o salida en consola luego de ejecutar este código? Explicar por qué:

```javascript
function test() {
   console.log(a); // Devuelve undefined
   console.log(foo());// Devuelve 2

   var a = 1;
   function foo() {
      return 2;
   }
}

test();
```

Y el de este código? :  

```javascript
var snack = 'Meow Mix'; //// No tiene hoisting

function getFood(food) {
    if (food) {
        var snack = 'Friskies';
        return snack;
    }
    return snack;
}

getFood(false);
```


### This

¿Cuál es el output o salida en consola luego de ejecutar esté código? Explicar por qué:

```javascript
var fullname = 'Juan Perez';
var obj = {
   fullname: 'Natalia Nerea',
   prop: {
      fullname: 'Aurelio De Rosa',
      getFullname: function() {
         return this.fullname;
      }
   }
};

console.log(obj.prop.getFullname()); //'Aurelio De Rosa'

var test = obj.prop.getFullname;

console.log(test()); //  undefined
```

### Event loop

Considerando el siguiente código, ¿Cuál sería el orden en el que se muestra por consola? ¿Por qué?

```javascript
// function printing() {
//    console.log(1);
//    setTimeout(function() { console.log(2); }, 1000);
//    setTimeout(function() { console.log(3); }, 0);
//    console.log(4);
// }

// printing();
//1 - 4 - 3 - 2 
```
