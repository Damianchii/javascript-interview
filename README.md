
# 🚀 JavaScript Interview Questions 
<p align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=js" />
  </a>
</p>

## ➡️ Explain event delegation 

> Event delegation in JavaScript is a programming technique that assigns event handlers to parent elements rather than to specific child elements. When an event occurs on a child element, the browser checks whether an event handler has been defined for that element. If not, the browser checks all parents one by one to find the event handler.

> Suppose we have a list of tasks to be performed (todo list) and new tasks are added dynamically by the user. We want to allow the user to mark a task as completed by clicking on it. Instead of assigning event handlers to each new element, we can use event delegation.

``` bash
<ul id="taskList">
  <li>Dish washes</li>
  <li>Buy milk</li>
  <li>Tidy room</li>
</ul>

```

> You can then use JavaScript to assign the click event handler to the `taskList` container and then delegate the event:

``` bash
const taskList = document.getElementById('taskList');

taskList.addEventListener('click', function(event) {
  // Verify that the item you clicked is a task list item
  if (event.target.tagName === 'LI') {
    // Add or remove the 'completed' class for the clicked task
    event.target.classList.toggle('completed');
  }
});

```


> In this example, instead of adding a click event handler to each list item, we assign it to the taskList container. When the user clicks on a list item, the event will be captured by the container, and then using event.target we check which item exactly was clicked. We can then respond appropriately by adding or removing the completed class to mark the task as completed. This makes the code more efficient and easier to maintain, especially for dynamically generated elements.

### Wyjaśnij delegacje zdarzeń w JavaScript

> Delegacja zdarzeń w JavaScript to technika programistyczna, która polega na przypisywaniu obsługi zdarzeń do elementów nadrzędnych, zamiast do konkretnych elementów podrzędnych. Gdy zdarzenie występuje na elemencie podrzędnym, przeglądarka sprawdza, czy została zdefiniowana obsługa zdarzenia dla tego elementu. Jeśli nie, przeglądarka sprawdza kolejno wszystkie elementy nadrzędne, aby znaleźć obsługę zdarzenia.

> Załóżmy, że mamy listę zadań do wykonania (todo list) i nowe zadania są dodawane dynamicznie przez użytkownika. Chcemy umożliwić użytkownikowi oznaczenie zadania jako wykonane przez kliknięcie na nie. Zamiast przypisywać obsługę zdarzeń do każdego nowego elementu, możemy użyć delegacji zdarzeń.

``` bash
<ul id="taskList">
  <li>Umyć naczynia</li>
  <li>Kupić mleko</li>
  <li>Posprzątać pokój</li>
</ul>

```
> A następnie możemy użyć JavaScript do przypisania obsługi zdarzenia kliknięcia do kontenera `taskList`, a następnie wykorzystać delegację zdarzeń:

``` bash
const taskList = document.getElementById('taskList');

taskList.addEventListener('click', function(event) {
  // Sprawdź, czy kliknięty element jest elementem listy zadań
  if (event.target.tagName === 'LI') {
    // Dodaj lub usuń klasę 'completed' dla klikniętego zadania
    event.target.classList.toggle('completed');
  }
});

```

> W tym przykładzie, zamiast dodawać obsługę zdarzenia kliknięcia do każdego elementu listy, przypisujemy ją do kontenera taskList. Gdy użytkownik kliknie na element listy, zdarzenie zostanie przechwycone przez kontener, a następnie używając event.target sprawdzamy, który dokładnie element został kliknięty. Następnie możemy odpowiednio zareagować, dodając lub usuwając klasę completed, aby oznaczyć zadanie jako wykonane. Dzięki temu kod jest bardziej wydajny i łatwiejszy w utrzymaniu, zwłaszcza w przypadku dynamicznie generowanych elementów.

## ➡️ Explain how `this` works in JavaScript.


> In JavaScript, the value of this depends on the context of the function invocation:
> <b>Global Context</b>

> * In the global context, outside of any function, this refers to the global object, which is window in web browsers and global in Node.js.
> <b>Function Context</b>

> * Inside a function, the value of this depends on how the function is called. If the function is called as a standalone function (i.e., not as a method of an object), this refers to the global object window in non-strict mode. In strict mode, this is undefined. If the function is called as a method of an object, this refers to that object.
> <b>Arrow Functions</b>

> * Arrow functions do not have their own this context. Instead, they inherit this from the enclosing lexical scope (i.e., the scope where they are defined).
> <b>Event Handlers</b>

> * In event handler functions, such as those assigned to DOM elements, this refers to the element that triggered the event.
> <b>Function Constructors</b>

> * Inside a function constructor (a function invoked with the new keyword), this refers to the newly created object.

### Wyjaśnij jak działa `this` w JavaScript 

> W JavaScript wartość `this` zależy od kontekstu wywołania funkcji:
> <b>Kontekst Globalny</b>

> * W kontekście globalnym, poza jakąkolwiek funkcją, `this` odnosi się do obiektu globalnego, którym jest `window` w przeglądarkach internetowych oraz `global` w Node.js.

> <b>Kontekst Funkcji</b>

> * Wewnątrz funkcji, wartość `this` zależy od sposobu wywołania funkcji.
Jeśli funkcja jest wywoływana jako samodzielna funkcja (czyli nie jako metoda obiektu), this odnosi się do obiektu globalnego `window` w trybie nieścisłym (non-strict mode). W trybie ścisłym (strict mode), `this` jest `undefined`.
Jeśli funkcja jest wywoływana jako metoda obiektu, `this` odnosi się do tego obiektu.

> <b>Funkcje Strzałkowe</b>

> * Funkcje strzałkowe nie mają własnego kontekstu `this`. Zamiast tego dziedziczą `this` z otaczającego zakresu leksykalnego (czyli z zakresu, w którym są zdefiniowane).

> <b>Obsługa Zdarzeń</b>

> * W funkcjach obsługi zdarzeń, takich jak te przypisane do elementów DOM, `this` odnosi się do elementu, który wywołał zdarzenie.

> <b>Konstruktory Funkcji</b>

> * Wewnątrz funkcji konstruktora (funkcji wywoływanej z użyciem słowa kluczowego `new`), `this` odnosi się do nowo utworzonego obiektu.

``` bash
// Kontekst globalny
console.log(this); // loguje obiekt globalny (window w przeglądarkach, global w Node.js)

// Kontekst funkcji
function foo() {
  console.log(this);
}
foo(); // loguje obiekt globalny (window w przeglądarkach, global w Node.js)

// Kontekst metody
const obj = {
  name: 'John',
  greet: function() {
    console.log(this.name);
  }
};
obj.greet(); // loguje 'John', ponieważ 'this' odnosi się do 'obj'

// Funkcje strzałkowe
const bar = () => {
  console.log(this);
};
bar(); // loguje ten sam obiekt 'this' co poza funkcją strzałkową

// Obsługa zdarzeń
const button = document.querySelector('button');
button.addEventListener('click', function() {
  console.log(this); // loguje element przycisku, który wywołał zdarzenie
});

// Konstruktory
function Osoba(imie) {
  this.imie = imie;
}
const jan = new Osoba('Jan');
console.log(jan.imie); // loguje 'Jan', ponieważ 'this' odnosi się do nowo utworzonego obiektu 'jan'

// Jawne wiązanie
function powitanie() {
  console.log(this.imie);
}
const obj2 = { imie: 'Alicja' };
powitanie.call(obj2); // loguje 'Alicja', ponieważ 'this' jest wyraźnie ustawione na 'obj2' za pomocą 'call'
```


## ➡️ Explain how prototypal inheritance works.

> By leveraging prototypal inheritance, JavaScript enables code reuse and object composition, facilitating the creation of more modular and maintainable codebases. Developers can extend and customize objects by adding properties and methods to their prototypes, allowing for flexible and powerful object-oriented programming in JavaScript.

### Wyjaśnij, jak działa dziedziczenie prototypowe.


> Dzięki dziedziczeniu prototypowemu JavaScript umożliwia ponowne wykorzystanie kodu i kompozycję obiektów, co ułatwia tworzenie bardziej modułowych i łatwych w utrzymaniu kodów źródłowych. Programiści mogą rozszerzać i dostosowywać obiekty, dodając właściwości i metody do ich prototypów, co pozwala na elastyczne i potężne programowanie zorientowane obiektowo w JavaScript.
``` bash
// Definiowanie konstruktora dla klasy Person
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// Dodanie metody do prototypu klasy Person
Person.prototype.greet = function() {
  console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
};

// Utworzenie nowego obiektu za pomocą konstruktora Person
const john = new Person('John', 30);

// Wywołanie metody z prototypu obiektu
john.greet(); // Wyświetli: "Hello, my name is John and I am 30 years old."
```
> W tym przykładzie

> * `Person` jest konstruktorem dla klasy `Person`, który przyjmuje dwa argumenty: `name` i `age`.

> * Metoda `greet()` jest dodawana do prototypu klasy `Person`, co oznacza, że wszystkie obiekty utworzone za pomocą konstruktora Person będą miały dostęp do tej metody.

> * Obiekt `john` jest utworzony za pomocą konstruktora Person.

> * Wywołanie metody `greet()` na obiekcie `john` wyświetli przywitanie zawierające jego imię i wiek.

## ➡️ What is the difference between a variable that is: `null`, `undefined` or `undeclared`?

> * `null` is a JavaScript primitive value that represents the intentional absence of any object value. It is explicitly assigned by developers to indicate that a variable has no value or that an object reference is intentionally empty.

```bash
let myNull = null;
```

> * `undefined` is a JavaScript primitive value automatically assigned to variables that have been declared but not initialized or assigned any value. It also represents the value returned by functions that do not explicitly return anything.

> * It indicates that a variable has been declared but not yet assigned any value.

```bash
let myVar;
console.log(myVar); // Output: undefined
```

> * An undeclared variable is a variable that has been used without being declared with the `var`, `let`, or `const` keyword. Accessing an undeclared variable will result in a reference error in strict mode or create a global variable implicitly in non-strict mode.

```bash
console.log(undeclaredVar); // ReferenceError: undeclaredVar is not defined
```

> In summary, `null` is a value that indicates intentional absence or emptiness, `undefined` is a value assigned to variables that have not been initialized, and undeclared variables are those that have been used without being declared.


### Jaka jest różnica między zmienną: `null`, `undefined` lub `undeclared`?

> * `null` to wartość pierwotna w języku JavaScript, która reprezentuje celowe brakowanie jakiejkolwiek wartości obiektu. Jest ona jawnie przypisywana przez programistów, aby wskazać, że zmienna nie ma żadnej wartości lub że odnośnik do obiektu jest celowo pusty.

```bash
let mojaZmienna = null;
```

> * `undefined` to wartość pierwotna w języku JavaScript, automatycznie przypisywana do zmiennych, które zostały zadeklarowane, ale nie zostały zainicjalizowane lub nie otrzymały żadnej wartości. Reprezentuje również wartość zwracaną przez funkcje, które nie zwracają jawnie żadnej wartości.

> * Oznacza to, że zmienna została zadeklarowana, ale jeszcze nie otrzymała żadnej wartości.

```bash
let mojaZmienna;
console.log(mojaZmienna); // Wynik: undefined
```

> * Zmienna niezadeklarowana to zmienna, która została użyta bez zadeklarowania za pomocą słowa kluczowego `var`, `let` lub `const`. Uzyskanie dostępu do zmiennej niezadeklarowanej spowoduje błąd odwołania w trybie ścisłym lub utworzy zmienną globalną domyślnie w trybie nieścisłym.

```bash
console.log(niezadeklarowanaZmienna); // ReferenceError: niezadeklarowanaZmienna nie jest zdefiniowana
```

> Podsumowując, `null` to wartość wskazująca na celowy brak lub pustość, `undefined` to wartość przypisana zmiennym, które nie zostały zainicjalizowane, a niezadeklarowane zmienne to takie, które zostały użyte bez wcześniejszego zadeklarowania.


## ➡️ What is a closure, and how/why would you use one?

> Closure occurs when a function remembers and then uses its lexical scope, even when it is called outside of it.

>  A function defined inside of another function, the inner function has access to the variables and scope of the outer function. Allow for private variables and state maintenance Used frequently in JS frameworks: React, Vue, Angular


### Czym są domknięcia i jak sie ich uzywa ?

> Domknięcie występuje wtedy, gdy funkcja zapamiętuje i następnie wykorzystuje swój leksykalny zakres, nawet wtedy gdy jest wywoływana poza nim.

``` bash
function outer(){
  const name = "Damian" 

  function inner(){
    return name
  }

  return inner()
}

const closure = outer()

console.log(closure // Damian
```
## ➡️ What language constructions do you use for iterating over object properties and array items?

> for loop, for..in, for each..in, map, reduce etc.

> <b>For Each</b>

``` bash
const arr = [1, 2, 3];

arr.forEach(value => {
  console.log(value);
});

```

> <b>For in</b>

```bash
const obj = { a: 1, b: 2, c: 3 };

for (let key in obj) {
  console.log(key, obj[key]);
}

```

### Jakich konstrukcji językowych używasz do iteracji po właściwościach obiektów i elementach tablicy?

> <b>For Each</b>

``` bash
const arr = [1, 2, 3];

arr.forEach(value => {
  console.log(value);
});

```

> <b>For in</b>

```bash
const obj = { a: 1, b: 2, c: 3 };

for (let key in obj) {
  console.log(key, obj[key]);
}

```
## ➡️ Can you describe the main difference between the `Array.forEach()` loop and `Array.map()` methods and why you would pick one versus the other?

> `Array.forEach()`

> The `forEach()` method executes a provided function once for each array element. It does not return a new array.

```bash
const arr = [1, 2, 3];
arr.forEach((value, index) => {
  console.log(`Element at index ${index}: ${value}`);
});
```

> `Array.map()`

> The `map()` method creates a new array by calling a provided function on every element in the calling array. It returns a new array with the results of the function calls.

``` bash
const arr = [1, 2, 3];
const doubledArr = arr.map(value => value * 2);
console.log(doubledArr); // Output: [2, 4, 6]
```
>In summary, you would pick `forEach()` when you need to perform an operation on each element of the array without creating a new array, and you would pick `map()` when you need to transform each element of the array and generate a new array with the transformed values.

### Czy możesz opisać główną różnicę między pętlą `Array.forEach()` a metodami `Array.map()` i dlaczego miałbyś wybrać jedną, a nie drugą?

> `Array.forEach()`
> Metoda `forEach()` wykonuje podaną funkcję raz dla każdego elementu tablicy. Nie zwraca nowej tablicy.

``` bash
const arr = [1, 2, 3];
arr.forEach((wartość, indeks) => {
  console.log(`Element na indeksie ${indeks}: ${wartość}`);
});
```

> `Array.map()`
> Metoda `map()` tworzy nową tablicę, wywołując podaną funkcję dla każdego elementu w wywołującej tablicy. Zwraca nową tablicę z wynikami wywołań funkcji

```bash
const arr = [1, 2, 3];
const podwojonaTablica = arr.map(wartość => wartość * 2);
console.log(podwojonaTablica); // Wynik: [2, 4, 6]

```
> Podsumowując, wybierasz `forEach()` gdy potrzebujesz wykonać operację na każdym elemencie tablicy bez tworzenia nowej tablicy, a `map()` gdy potrzebujesz przekształcić każdy element tablicy i utworzyć nową tablicę z przekształconymi wartościami.

## ➡️ What is a typical use case for anonymous functions?

> An anonymous function in JavaScript is a function that does not have a name.

``` bash
const myFunction = function() {
   console.log('This is an anonymous function');
};

```
> <b>Event Handling</b> Anonymous functions can be used as event handlers in the user interface. They are assigned to events such as clicks, text box value changes, page scrolling, etc.

``` bash
document.getElementById('myButton').addEventListener('click', function() {
   console.log('Button clicked');
});

```
> <b>Closures</b> Anonymous functions can create closures, which means they can access variables in their surrounding scope even after they leave that scope

### Jaki jest typowy przypadek użycia funkcji anonimowych?

> Funkcja anonimowa w JavaScript to funkcja, która nie ma nazwy.

``` bash
const myFunction = function() {
  console.log('This is an anonymous function');
};

```
> <b>Obsługa zdarzeń</b> Funkcje anonimowe mogą być używane jako obsługa zdarzeń w interfejsie użytkownika. Są one przypisywane do zdarzeń takich jak kliknięcia, zmiany wartości pola tekstowego, przewijanie strony itp.

``` bash
document.getElementById('myButton').addEventListener('click', function() {
  console.log('Button clicked');
});

```
> <b>Domknięcia (closures)</b> Funkcje anonimowe mogą tworzyć zamknięcia, co oznacza, że ​​mogą uzyskiwać dostęp do zmiennych ze swojego otaczającego zakresu, nawet po opuszczeniu tego zakresu

## ➡️ What is the difference between host objects and native objects?

> <b>Native objects</b> are objects that are part of the JavaScript language defined by the ECMAScript specification, such as `String`, `Math`, `RegExp`, `Object`, `Function`, etc.

> <b>Host objects</b> are provided by the runtime environment (browser or Node), such as `window`, `XMLHTTPRequest`, `document`, `setTimeout` etc.

### Jaka jest różnica między obiektami hosta a obiektami natywnymi?

> <b>Obiekty natywne</b> to obiekty będące częścią języka JavaScript zdefiniowanego w specyfikacji ECMAScript, takie jak `String`, `Math`, `RegExp`, `Object`, `Function` itp.

> <b>Obiekty hosta</b> są dostarczane przez środowisko wykonawcze (przeglądarkę lub węzeł), takie jak `window`, `XMLHTTPRequest`, `document`, `setTimeout` itp.

## ➡️ Explain the difference between: `function Person(){}`, `var person = Person()`, and `var person = new Person()`?

> `function Person(){}` - definition of the constructor of a function called Person
```bash
//Constructor function definition
function Person(name, age) {
    this.name = name;
    this.age = age;
}

// Use the constructor function to remnant the object
var person1 = new person('John', 30);
var person2 = new person('Alice', 25);

// Display runtime properties
console.log(person1.name); // Jan
console.log(person1.age); // thirty

console.log(person2.name); // Alice
console.log(person2.age); // 25
```

> `var person = Person()` - calling the Person constructor function and assigning it to the `person` connector

> `var person = new Person()` - creates an instance of the Person object and assigns it to the person variable

### wyjaśnij róznice miedzy `function Person(){}`, `var person = Person()`, i `var person = new Person()`?

> `function Person(){}` - definicja funkcji konstruktora o nazwie Person

```bash
// Definicja funkcji konstruktora
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// Użycie funkcji konstruktora do utworzenia instancji obiektu
var person1 = new Person('John', 30);
var person2 = new Person('Alice', 25);

// Wyświetlenie właściwości utworzonych obiektów
console.log(person1.name); // John
console.log(person1.age);  // 30

console.log(person2.name); // Alice
console.log(person2.age);  // 25
```

> `var person = Person()` - wywołanie funkcji konstruktora Person i przypisanie go do zmienniej `person`

>`var person = new Person()` - tworzy instancje obiektu Person i przypisuje go do zmiennej person

## ➡️ Explain the differences on the usage of foo between function foo() {} and var foo = function() {}

> `function foo() {}` - Function declarations are raised on your device as they are used, which means we will be able to use them before their actual function, see:
```bash
foo(); // work!

function foo() {
  console.log('function');
}

```

> `var foo = function() {}` - Function expressions are not constructed like function declarations. The variable `foo` is raised, but its value (function) is not assigned until the line of code is executed.

```bash
foo(); // error TypeError: foo is not a function

var foo = function() {
  console.log('function');
};

```

### Wyjaśnij różnice w użyciu `foo` pomiędzy `function foo() {}` i `var foo = function() {}`

> `function foo() {}` Deklaracje funkcji są wznoszone (hoisted) na górę swojego zasięgu podczas fazy kompilacji, co oznacza ze bedziemy mogii ich uzywac przed ich faktyczna deklaracji , orzeykład:
```bash
foo(); // To działa

function foo() {
  console.log('Deklaracja funkcji');
}

```
> `var foo = function() {}` - Wyrażenia funkcji nie są wznoszone tak jak deklaracje funkcji. Zmienna `foo` jest wznoszona, ale jej wartość (funkcja) nie jest przypisywana do momentu wykonania linii kodu.

```bash
foo(); // To spowoduje błąd: TypeError: foo is not a function

var foo = function() {
  console.log('Wyrażenie funkcji');
};

```

## ➡️ Can you explain what `Function.call()` and `Function.apply()` do? What is the notable difference between the two?



### Czy możesz wyjaśnić, do czego służą `Function.call()` i `Function.apply()`? Jaka jest zauważalna różnica między nimi?

> `Function.call()` - Metoda `call()` wywołuje funkcję z określonym kontekstem (`this`) oraz argumentami przekazanymi jako oddzielone argumenty do metody `call()`.

```bash
function greet() {
  console.log(`Hello, ${this.name}!`);
}

const person1 = { name: 'John' };
const person2 = { name: 'Alice' };

greet.call(person1); // Output: Hello, John!
greet.call(person2); // Output: Hello, Alice!

```
```bash
function greet(name) {
  console.log(`Hello, ${name}! My name is ${this.name}.`);
}

const person = {
  name: 'John'
};

greet.call(person, 'Alice'); // Output: Hello, Alice! My name is John.

```

> `Function.apply()` - Metoda `apply()` działa podobnie do `call()`, z tą różnicą, że argumenty są przekazywane jako tablica.

```bash
function greet(name, message) {
  console.log(`${message}, ${name}! My name is ${this.name}.`);
}

const person = { name: 'John' };

const args = ['Alice', 'Hello'];
greet.apply(person, args); // Output: Hello, Alice! My name is John.

```

## ➡️ Explain Function.prototype.bind()
> `Function.prototype.bind()` is a built-in method in JavaScript that creates a new function that is assigned a specific context and optional constant arguments.

> The `bind()` method allows you to establish a constant context (`this` value) for the function. This allows the specified context to be preserved even when the function is called in a different context.

```bash
const person = {
   name: 'John',
   greet: function() {
     console.log(`Hello, ${this.name}!`);
   }
};

const boundGreet = person.greet.bind(person);
boundGreet(); // Output: Hello, John!

```

> In this example, `bind()` is used to create a new boundGreet function that will always be called in the context of the person object, even when called in a different context. Thanks to this, the boundGreet function will retain access to the name property of the person object.

### Wyjasnij Function.prototype.bind()

> `Function.prototype.bind()` jest metodą wbudowaną w języku JavaScript, która tworzy nową funkcję, która ma przypisany określony kontekst oraz opcjonalnie stałe argumenty.

> Metoda `bind()` umożliwia ustalenie stałego kontekstu (wartości `this`) dla funkcji. Pozwala to na zachowanie określonego kontekstu nawet wtedy, gdy funkcja zostanie wywołana w innym kontekście.

```bash
const person = {
  name: 'John',
  greet: function() {
    console.log(`Hello, ${this.name}!`);
  }
};

const boundGreet = person.greet.bind(person);
boundGreet(); // Output: Hello, John!

```

> W tym przykładzie `bind()` jest używane do utworzenia nowej funkcji boundGreet, która zawsze będzie wywoływana w kontekście obiektu person, nawet gdy zostanie wywołana w innym kontekście. Dzięki temu, funkcja boundGreet zachowa dostęp do właściwości name obiektu person.

## ➡️ What is the difference between feature detection, feature inference, and using the UA string?

> <b>Feature detection</b> - checks whether a given browser or device supports a specific feature or API before using it in the code.

```bash
if (typeof localStorage !== 'undefined') {
   // The browser supports localStorage
   // We can safely use localStorage in our code
   localStorage.setItem('exampleKey', 'exampleValue');
   console.log(localStorage.getItem('exampleKey')); // Output: exampleValue
} else {
   // The browser does not support localStorage
   // Some workaround must be taken or the user must be notified that this functionality is missing
   console.log('Your browser does not support localStorage.');
}
```
> <b>Feature inference</b> - this is an approach that is based on the assumption that if certain features or properties are available, other features related to them should also be available. Here is an example where we use function inference in JavaScript:

```bash
if (document.querySelector && window.addEventListener) {
   // The browser supports both querySelector and addEventListener
   // We can safely use these functions in our code
   const element = document.querySelector('.example');
   element.addEventListener('click', function() {
     console.log('The .example element was clicked');
   });
} else {
   // The browser does not support one or both of these features
   // You need to take some substitute action or notify the user about the lack of these functionalities
   console.log('Your browser does not support some features.');
}

```
> In this example, we check whether the document object has a querySelector method (for selecting elements using CSS selectors) and whether the window object has an addEventListener method (for adding event listeners). If both methods are available, we assume that the browser also supports other DOM manipulation and event handling features, so we can safely use them in our code.

> <b>UA string</b> - Using the User-Agent (UA) string involves parsing a string identifying the user's browser and device sent in HTTP requests.

```bash
const userAgent = navigator.userAgent;

if (userAgent.includes('Chrome')) {
   console.log('The user is using Google Chrome.');
} else if (userAgent.includes('Firefox')) {
   console.log('The user is using Mozilla Firefox.');
} else if (userAgent.includes('Edge')) {
   console.log('The user is using Microsoft Edge.');
} else {
   console.log('The user's browser could not be identified.');
}

```

> In this example, we use the navigator.userAgent property, which contains the User-Agent string of the current browser. We then check the contents of this string to determine what browser the user is dealing with. Depending on what strings are included in userAgent, we can determine what browser the user is using and adjust the page's behavior accordingly.

### Jaka jest roznica miedzy feature dettaction, feature inference, i UA string ?

> <b>Feature detection</b> - polega na sprawdzaniu, czy dana przeglądarka lub urządzenie obsługuje określoną funkcję lub interfejs API przed użyciem jej w kodzie.

```bash
if (typeof localStorage !== 'undefined') {
  // Przeglądarka obsługuje localStorage
  // Możemy bezpiecznie korzystać z localStorage w naszym kodzie
  localStorage.setItem('exampleKey', 'exampleValue');
  console.log(localStorage.getItem('exampleKey')); // Output: exampleValue
} else {
  // Przeglądarka nie obsługuje localStorage
  // Trzeba podjąć jakieś działania zastępcze lub powiadomić użytkownika o braku tej funkcjonalności
  console.log('Twoja przeglądarka nie obsługuje funkcji localStorage.');
}
```
> <b>Feature inference</b> -  to podejście, które opiera się na założeniu, że jeśli pewne funkcje lub właściwości są dostępne, to inne powiązane z nimi także powinny być dostępne. Oto przykład, w którym korzystamy z wnioskowania funkcji w JavaScript:

```bash
if (document.querySelector && window.addEventListener) {
  // Przeglądarka obsługuje zarówno querySelector, jak i addEventListener
  // Możemy bezpiecznie korzystać z tych funkcji w naszym kodzie
  const element = document.querySelector('.example');
  element.addEventListener('click', function() {
    console.log('Kliknięto element .example');
  });
} else {
  // Przeglądarka nie obsługuje jednej lub obu z tych funkcji
  // Trzeba podjąć jakieś działania zastępcze lub powiadomić użytkownika o braku tych funkcjonalności
  console.log('Twoja przeglądarka nie obsługuje niektórych funkcji.');
}

```
> W tym przykładzie sprawdzamy, czy obiekt document ma metodę querySelector (do wybierania elementów za pomocą selektorów CSS) oraz czy obiekt window ma metodę addEventListener (do dodawania nasłuchiwaczy zdarzeń). Jeśli obie metody są dostępne, zakładamy, że przeglądarka obsługuje także inne funkcje związane z manipulacją DOM i obsługą zdarzeń, więc możemy bezpiecznie korzystać z nich w naszym kodzie.

> <b>UA string</b> - Korzystanie z ciągu User-Agent (UA) polega na analizowaniu ciągu identyfikującego przeglądarkę i urządzenie użytkownika wysłanego w żądaniach HTTP.

```bash
const userAgent = navigator.userAgent;

if (userAgent.includes('Chrome')) {
  console.log('Użytkownik korzysta z przeglądarki Google Chrome.');
} else if (userAgent.includes('Firefox')) {
  console.log('Użytkownik korzysta z przeglądarki Mozilla Firefox.');
} else if (userAgent.includes('Edge')) {
  console.log('Użytkownik korzysta z przeglądarki Microsoft Edge.');
} else {
  console.log('Nie można zidentyfikować przeglądarki użytkownika.');
}

```

> W tym przykładzie korzystamy z właściwości navigator.userAgent, która zawiera ciąg User-Agent aktualnej przeglądarki. Następnie sprawdzamy zawartość tego ciągu, aby określić, z jaką przeglądarką ma do czynienia użytkownik. W zależności od tego, jakie ciągi są zawarte w userAgent, możemy określić, z jaką przeglądarką korzysta użytkownik i dostosować zachowanie strony odpowiednio.

## ➡️ Explain "hoisting".

> <b>Hoisting</b> -  variable declarations (but not initializations) and function declarations are moved to the top of their containing scope during the compilation phase. This means that regardless of where variables and functions are declared in the code, they are treated as if they were declared at the beginning of their scope. However, only declarations are hoisted, while initializations remain in place. This can sometimes lead to unexpected behavior if not understood properly.

> Initialization example: 
```bash
let x; // Variable declaration of x (without initialization)
x = 10; // Initializing variable x with the value 10
console.log(x); // Output: 10

```

### Wyjasnij co to jest "hoisting"


> <b>Hoisting</b> - deklaracje zmiennych (ale nie ich inicjalizacje) oraz deklaracje funkcji są przenoszone na górę swojego zakresu podczas fazy kompilacji. Oznacza to, że bez względu na to, gdzie zmienne i funkcje są zadeklarowane w kodzie, są traktowane tak, jakby były zadeklarowane na początku swojego zakresu. Jednak tylko deklaracje są hoistowane, podczas gdy inicjalizacje pozostają na swoim miejscu. Może to czasami prowadzić do nieoczekiwanego zachowania, jeśli nie jest to właściwie zrozumiane.

> Przykład inicjalizacji: 
```bash
let x; // Deklaracja zmiennej x (bez inicjalizacji)
x = 10; // Inicjalizacja zmiennej x wartością 10
console.log(x); // Output: 10

```
## ➡️ What is type coercion? What are common pitfalls of relying on type coercion in JavaScript code?

> Type coercion in JavaScript refers to automatically transforming values from one data type to another when evaluating expressions. This process occurs when operands of different types are used in operations.

> * Implicit Conversion - Type coercion may lead to unexpected behavior when values are implicitly converted to other types. For example, the addition operator (+) can concatenate strings if one of the operands is a string.

```bash
// Example 1
console.log(5 + "5"); // Output: "55" because the number 5 is converted to a string and concatenation occurs.

// Example 2
console.log("3" - 1); // Output: 2 because the string "3" is converted to a number to enable subtraction.

```

> * Loss of Precision - Type coercion may lead to loss of precision when converting between numeric and text values. For example, numbers written as strings may be treated as numbers in arithmetic operations, which may lead to unintended results.

```bash
// Example 3
console.log(0.1 + 0.2); // Output: 0.30000000000000004, due to numerical representation errors.

// Example 4
console.log("10" / 2); // Output: 5, even though "10" is a string, will be converted to a number to perform division.

```

> * Inconsistent Behavior - Type coercion rules may vary depending on the context and operator used. This can lead to inconsistencies and make the code harder to understand and debug.

```bash
// Example 5
console.log(5 == "5"); // Output: true because the equality operator is type-insensitive and an implicit conversion occurs.

// Example 6
console.log(false == 0); // Output: true, which may be surprising because the logical value false is converted to the number 0.

```

### Co to jest przymus typu? Jakie są typowe pułapki polegające na wymuszaniu typu w kodzie JavaScript?

> Type coercion w języku JavaScript odnosi się do automatycznego przekształcania wartości z jednego typu danych na inny podczas ewaluacji wyrażeń. Ten proces zachodzi, gdy operandy różnych typów są używane w operacjach.

> *  Konwersja Niejawna - Type coercion może prowadzić do nieoczekiwanego zachowania, gdy wartości są niejawnie konwertowane na inne typy. Na przykład operator dodawania (+) może łączyć ciągi znaków, jeśli jeden z operandów jest ciągiem.

```bash
// Przykład 1
console.log(5 + "5"); // Output: "55", ponieważ liczba 5 jest konwertowana na ciąg znaków i następuje konkatenacja.

// Przykład 2
console.log("3" - 1); // Output: 2, ponieważ ciąg znaków "3" jest konwertowany na liczbę, aby umożliwić odejmowanie.

```

> * Utrata Precyzji - Type coercion może prowadzić do utraty precyzji podczas konwersji między wartościami numerycznymi i tekstowymi. Na przykład, liczby zapisane jako ciągi znaków mogą być traktowane jako liczby w operacjach arytmetycznych, co może prowadzić do niezamierzonych wyników.

```bash
// Przykład 3
console.log(0.1 + 0.2); // Output: 0.30000000000000004, z powodu błędów reprezentacji numerycznej.

// Przykład 4
console.log("10" / 2); // Output: 5, mimo że "10" jest ciągiem znaków, zostanie przekonwertowany na liczbę w celu wykonania dzielenia.

```

> * Niekonsekwentne Zachowanie - Zasady type coercion mogą się różnić w zależności od kontekstu i użytego operatora. Może to prowadzić do niekonsekwencji i sprawiać, że kod staje się trudniejszy do zrozumienia i debugowania.

```bash
// Przykład 5
console.log(5 == "5"); // Output: true, ponieważ operator równości nie uwzględnia typów i następuje niejawna konwersja.

// Przykład 6
console.log(false == 0); // Output: true, co może być zaskakujące, ponieważ wartość logiczna false jest konwertowana na liczbę 0.

```

## ➡️ Describe event bubbling.

> > Event bubbling is a mechanism in the DOM (Document Object Model) in which an event fired on a nested element propagates up through its ancestors in the DOM hierarchy. When an event occurs on an element, such as a button click event, the event first fires on the target element. The event then propagates up through the target element's ancestors, triggering the same event on every ancestor element in the hierarchy

> Event bubbling provides a convenient way to handle events in a more general and centralized way. Instead of attaching event listeners to each individual element, you can attach event listeners to their common ancestor and let the events ascend to that ancestor

### Opisz zdarzenie bubblingu

> Event bubbling to mechanizm w DOM (Modelu Obiektowym Dokumentu), w którym zdarzenie wywołane na zagnieżdżonym elemencie propaguje się w górę poprzez jego przodków w hierarchii DOM.Kiedy zdarzenie występuje na elemencie, takim jak zdarzenie kliknięcia na przycisku, zdarzenie najpierw wywołuje się na docelowym elemencie. Następnie zdarzenie wznosi się w górę przez elementy nadrzędne docelowego elementu, wywołując to samo zdarzenie na każdym elemencie przodka w hierarchii

> Bąbelkowanie zdarzeń zapewnia wygodny sposób obsługi zdarzeń w bardziej ogólny i scentralizowany sposób. Zamiast dołączać nasłuchiwacze zdarzeń do każdego indywidualnego elementu, można dołączyć nasłuchiwacze zdarzeń do ich wspólnego przodka i pozwolić zdarzeniom wznosić się do tego przodka

```bash
<ul id="parentList">
  <li id="item1">Element 1</li>
  <li id="item2">Element 2</li>
  <li id="item3">Element 3</li>
</ul>

```

```bash
const parentList = document.getElementById('parentList');
const items = document.getElementsByTagName('li');

parentList.addEventListener('click', function(event) {
  console.log('Zdarzenie kliknięcia na rodzicu');
});

for (let i = 0; i < items.length; i++) {
  items[i].addEventListener('click', function(event) {
    console.log('Click element: ' + i);
  });
}

```

## ➡️ Describe event capturing.

> Unlike event bubbling, which starts from the target element and bubbles up through its ancestors, event capturing starts from the top of the DOM tree and descends down to the target element.

### Opisz zdarzenie capturing(przechwytywanie)

> W przeciwieństwie do bąbelkowania zdarzeń, które rozpoczyna się od elementu docelowego i wznosi się w górę przez jego przodków, przechwytywanie zdarzeń rozpoczyna się od samej góry drzewa DOM i schodzi w dół do elementu docelowego.

```bash
<div id="outer">
  <div id="inner">
    <button id="button">Kliknij mnie</button>
  </div>
</div>

```

```bash
const outer = document.getElementById('outer');
const inner = document.getElementById('inner');
const button = document.getElementById('button');

outer.addEventListener('click', function(event) {
  console.log('Zdarzenie przechwycone na elemencie o id "outer"');
}, true);

inner.addEventListener('click', function(event) {
  console.log('Zdarzenie przechwycone na elemencie o id "inner"');
});

button.addEventListener('click', function(event) {
  console.log('Zdarzenie przechwycone na elemencie o id "button"');
});

```
## ➡️

> * Attributes - are defined in HTML and provide initial values for elements

> * Properties - are JavaScript objects that represent the state of HTML elements. They can be accessed and modified dynamically using JavaScript. Properties can change while the program is running and reflect the current state of the element

> *  Atrybuty - są zdefiniowane w HTML i dostarczają początkowych wartości elementom

> * Właściwości - są obiektami JavaScript, które reprezentują stan elementów HTML. Mogą być one dostępne i modyfikowane dynamicznie za pomocą JavaScriptu. Właściwości mogą zmieniać się podczas działania programu i odzwierciedlają aktualny stan elementu

> * `getAttribute('value')` zwraca początkową wartość atrybutu "value" określoną w HTML, która wynosi "Hello".
> * `input.value` zwraca aktualną wartość właściwości "value" elementu, która również wynosi "Hello", ale może być zmieniona dynamicznie podczas działania skryptu lub interakcji użytkownika.

```bash
<input id="myInput" type="text" value="Hello">

```

```bash
const input = document.getElementById('myInput');

// Pobranie wartości atrybutu
const attributeValue = input.getAttribute('value');
console.log('Wartość atrybutu:', attributeValue); // Output: Hello

// Pobranie wartości właściwości
const propertyValue = input.value;
console.log('Wartość właściwości:', propertyValue); // Output: Hello

```
