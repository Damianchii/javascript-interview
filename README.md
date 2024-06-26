
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
## ➡️ What is the difference between an "attribute" and a "property"?

> * Attributes - are defined in HTML and provide initial values for elements

> * Properties - are JavaScript objects that represent the state of HTML elements. They can be accessed and modified dynamically using JavaScript. Properties can change while the program is running and reflect the current state of the element

> * `getAttribute('value')` returns the initial value of the "value" attribute specified in the HTML, which is "Hello".
> * `input.value` returns the current value of the element's "value" property, which is also "Hello", but can be changed dynamically during script execution or user interaction.

### Jaka jest różnica między „atrybutem” a „właściwością”?

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

## ➡️ What are the pros and cons of extending built-in JavaScript objects?

#### <b>Advantages</b>

> * <b>Convenience</b> This can provide convenience by adding custom methods or properties directly to built-in objects, allowing for cleaner and more concise code.

#### <b>Cons</b>

> * <b>Global Scope Pollution</b> Adding methods or properties to built-in objects affects all instances of those objects throughout the application, which may lead to unintended consequences or conflicts with other libraries.

> * <b>Potential Conflicts</b> There is a risk of name conflicts with existing or future methods or properties of built-in objects, especially in larger code bases or when collaborating with other developers.

> * <b>Maintenance</b> Extended methods or properties may not be consistent across different environments or JavaScript engine implementations, leading to maintenance challenges and potential compatibility issues.

### Jakie są zalety i wady rozszerzania wbudowanych obiektów JavaScript?

#### <b>Zalety</b>

> * <b>Wygodne</b> Może to zapewnić wygodę poprzez dodawanie niestandardowych metod lub właściwości bezpośrednio do wbudowanych obiektów, co pozwala na czystszy i bardziej zwięzły kod.

#### <b>Wady</b>

> * <b>Zanieczyszczenie globalnego zakresu</b> Dodawanie metod lub właściwości do wbudowanych obiektów wpływa na wszystkie wystąpienia tych obiektów w całej aplikacji, co może prowadzić do niezamierzonych skutków lub konfliktów z innymi bibliotekami.

> * <b>Potencjalne konflikty</b> Istnieje ryzyko konfliktów nazw z istniejącymi lub przyszłymi metodami lub właściwościami wbudowanych obiektów, zwłaszcza w większych bazach kodu lub podczas współpracy z innymi programistami.

> * <b>Konserwacja</b> Rozszerzone metody lub właściwości mogą nie być spójne w różnych środowiskach lub implementacjach silników JavaScript, co prowadzi do wyzwań konserwacyjnych i potencjalnych problemów z kompatybilnością.

```bash
// Rozszerzenie wbudowanego obiektu Array o metodę do sumowania elementów
Array.prototype.sum = function() {
    let total = 0;
    for (let i = 0; i < this.length; i++) {
        total += this[i];
    }
    return total;
};

// Użycie nowej metody sum() na tablicy
const numbers = [1, 2, 3, 4, 5];
console.log(numbers.sum()); // Output: 15

```

## ➡️ What is the difference between `==` and `===`?

> `==` performs type coercion before comparison, while `===` does not perform type coercion and requires both value and type to be equal for true comparison.

### Jaka jest roznica miedzy `==` a `===` ?

> `==` wykonuje konwersję typów przed porównaniem, podczas gdy `===` nie wykonuje konwersji typów i wymaga, aby zarówno wartość, jak i typ były identyczne dla poprawnego porównania.

## ➡️ Explain the same-origin policy with regards to JavaScript.

> Same-Origin Policy in the context of JavaScript is a security policy used by web browsers that limits the interactions of JavaScript scripts with resources on websites to the same origins (same protocols, domains and ports). This means that a script on one web page has limited access to resources (e.g. data, DOM objects) on other web pages.

> For example, if a script is located on a page at https://example.com, it can use data located on the same page or on other pages at https://example.com/foo or https:/ /example.com/bar, but will not be able to access resources on sites with other addresses, such as https://example.org or http://example.com:8080.

### Wyjaśnij zasady tego samego pochodzenia w odniesieniu do JavaScript.

> Polityka tej samej domeny (Same-Origin Policy) w kontekście JavaScriptu to zasada bezpieczeństwa stosowana przez przeglądarki internetowe, która ogranicza interakcje skryptów JavaScript z zasobami na stronach internetowych do tych samych źródeł (takich samych protokołów, domen i portów). Oznacza to, że skrypt na jednej stronie internetowej ma ograniczony dostęp do zasobów (np. danych, obiektów DOM) na innych stronach internetowych.

> Na przykład, jeśli skrypt znajduje się na stronie o adresie https://example.com, może on korzystać z danych znajdujących się na tej samej stronie lub na innych stronach o adresach https://example.com/foo lub https://example.com/bar, ale nie będzie mógł uzyskać dostępu do zasobów na stronach o innych adresach, takich jak https://example.org czy http://example.com:8080.

## ➡️ Why is it called a Ternary operator, what does the word "Ternary" indicate?

> The Ternary operator in JavaScript is denoted by `? :`, and it is used as a shorthand for an if-else statement.

```bash
arr1 ? arr2 : arr3
```

### Dlaczego nazywa się to operatorem trójskładnikowym, co oznacza słowo „trójskładnikowy”?

> Operator trójskładnikowy w JavaScript jest oznaczony przez `? :` i jest używany jako skrót instrukcji if-else.

## ➡️ What is strict mode? What are some of the advantages/disadvantages of using it?

> Strict mode offers several advantages in terms of preventing errors, improving performance, strengthening security and code quality, but also comes with potential disadvantages in terms of backward compatibility, learning curve and stricter requirements. Developers should carefully consider the tradeoffs and use strict mode carefully, depending on design requirements and coding practices

#### Advantages

> * <b>Error Prevention</b> Strict mode helps catch common errors in your code and prevents potentially problematic code structures from being executed silently. This makes it easier to track errors in your code and makes debugging easier.

> * <b>Performance Improvements</b> In some cases, strict mode code may be more aggressively optimized by JavaScript engines, which may lead to potential performance improvements.

> * <b>Security Hardening</b> By preventing certain unsafe or risky coding practices, strict mode can improve the security of JavaScript applications and reduce the risk of vulnerabilities.

> * <b>Improving Development Practices</b> Strict mode encourages developers to follow best practices and write cleaner, more robust code by applying stricter rules and standards.

#### Cons
> * <b>Backward Compatibility</b> Strict mode may break existing code that relies on non-strict behavior. Enabling strict mode in older codes may require significant modifications to match.

> * <b>Learning Curve</b> Developers who are new to strict mode may initially have difficulty understanding its limitations and adapting their coding practices.

> * <b>Strict Requirements</b> Strict mode places more stringent requirements on your code, which may restrict certain programming techniques or patterns that were previously allowed.

### Co to jest tryb ścisły? Jakie są zalety/wady korzystania z niego?

> Tryb ścisły oferuje kilka zalet w zakresie zapobiegania błędom, poprawy wydajności, wzmocnienia bezpieczeństwa i jakości kodu, towarzyszą mu także potencjalne wady związane z zgodnością wsteczną, krzywą uczenia się i surowszymi wymaganiami. Programiści powinni dokładnie rozważyć kompromisy i używać trybu ścisłego z rozwagą, w zależności od wymagań projektowych i praktyk kodowania

#### Zalety

> * <b>Zapobieganie Błędom</b> Tryb ścisły pomaga wyłapywać powszechne błędy w kodzie i uniemożliwia wykonywanie potencjalnie problematycznych konstrukcji kodu w sposób cichy. Ułatwia to śledzenie błędów w kodzie i ułatwia debugowanie.

> * <b>Poprawa Wydajności</b> W niektórych przypadkach kod w trybie ścisłym może być bardziej agresywnie zoptymalizowany przez silniki JavaScript, co może prowadzić do potencjalnych ulepszeń wydajnościowych.

> * <b>Wzmocnienie Bezpieczeństwa</b> Poprzez uniemożliwianie pewnych niebezpiecznych lub ryzykownych praktyk kodowania, tryb ścisły może poprawić bezpieczeństwo aplikacji JavaScript i zmniejszyć ryzyko wystąpienia podatności.

> * <b>Poprawa Praktyk Programistycznych</b> Tryb ścisły zachęca programistów do stosowania najlepszych praktyk i pisania czystszych, bardziej solidnych kodów, stosując bardziej restrykcyjne reguły i standardy.

#### Wady
> * <b>Zgodność Wsteczna</b>  Tryb ścisły może naruszyć istniejący kod, który polega na nieścisłym zachowaniu. Włączenie trybu ścisłego w starszych kodach może wymagać znacznych modyfikacji, aby je dopasować.

> * <b>Krzywa Uczenia</b>  Programiści, którzy dopiero zaczynają korzystać z trybu ścisłego, mogą początkowo mieć trudności z zrozumieniem jego ograniczeń i dostosowaniem swoich praktyk kodowania.

> * <b>Surowe Wymagania</b>  Tryb ścisły nakłada bardziej restrykcyjne wymagania na kod, co może ograniczać pewne techniki programowania lub wzorce, które wcześniej były dozwolone.

```bash
// Kod bez trybu ścisłego
function add(a, b) {
    return a + b;
}

console.log(add(1, 2)); // Output: 3
console.log(add('1', '2')); // Output: '12' (konkatenacja stringów)

// Kod z trybem ścisłym
'use strict';

function addStrict(a, b) {
    return a + b;
}

console.log(addStrict(1, 2)); // Output: 3
console.log(addStrict('1', '2')); // Output: TypeError: Cannot convert string to number (błąd)

```

## ➡️ What are some of the advantages/disadvantages of writing JavaScript code in a language that compiles to JavaScript?

#### Advantages

> * <b>Extended Language Features</b> These languages often provide additional features and syntactic improvements not found in pure JavaScript, such as static typing, classes, interfaces, and modules. This can lead to more readable, organized code and reduce the risk of errors.

> * <b> Tool Support</b> Many of these languages are supported by robust tools, including compilers, linters, and IDE integrations, which can help improve code quality, enforce coding standards, and optimize the development process.

#### Defects

> * <b> Learning Curve</b> Developers must learn the syntax, features, and nuances of the language that compiles to JavaScript, which can initially increase the learning curve, especially for developers who already know JavaScript well.

> * <b> Build Effort</b> Adding a build step introduces additional complexity to the development process and can increase build times, especially in larger projects. This overhead may be negligible for smaller projects, but can become significant in larger, more complex applications.

### Jakie są zalety/wady pisania kodu JavaScript w języku kompilującym się do JavaScript?

#### Zalety

> * <b>Rozszerzone Funkcje Językowe</b> Te języki często dostarczają dodatkowych funkcji i ulepszeń składniowych, których nie ma w czystym JavaScript, takich jak statyczne typowanie, klasy, interfejsy i moduły. Może to prowadzić do bardziej czytelnego, zorganizowanego kodu i zmniejszać ryzyko wystąpienia błędów.

> * <b> Wsparcie Narzędziowe</b> Wiele z tych języków jest wspieranych przez solidne narzędzia, w tym kompilatory, lintery i integracje z IDE, co może pomóc poprawić jakość kodu, narzucić standardy kodowania i zoptymalizować proces deweloperski.

#### Wady

> * <b> Krzywa Uczenia</b> Deweloperzy muszą nauczyć się składni, funkcji i niuansów języka kompilującego się do JavaScript, co początkowo może zwiększyć krzywą uczenia się, szczególnie dla deweloperów, którzy już dobrze znają JavaScript.

> * <b> Nakład Kompilacji</b> Dodanie etapu kompilacji wprowadza dodatkową złożoność do procesu deweloperskiego i może zwiększyć czas kompilacji, szczególnie w większych projektach. Ten nakład może być pomijalny dla mniejszych projektów, ale może stać się istotny w większych, bardziej złożonych aplikacjach.

## ➡️ What tools and techniques do you use debugging JavaScript code?

> * <b>Browser Developer Tools</b> I make use of built-in developer tools available in web browsers, such as Chrome DevTools, Firefox Developer Tools, or Microsoft Edge Developer Tools. These tools offer features like DOM element inspection, JavaScript debugging, network monitoring, performance profiling, and many other useful tools for code analysis and debugging.

> * <b>`console.log()`</b> I often employ the technique of adding `console.log()` statements to the code to display variable values, check control flow, and track code execution. It's a quick way to diagnose errors and monitor code behavior.

> * <b>Isolation Testing</b> I frequently isolate the problematic code snippet and test it in isolation to identify whether the issue lies within that specific code snippet or stems from interactions with other parts of the application.

### Jakich narzędzi i technik używasz do debugowania kodu JavaScript?

> * <b>Przeglądarkowych Narzędzi Deweloperskich</b> Korzystam z wbudowanych narzędzi deweloperskich dostępnych w przeglądarkach internetowych, takich jak Chrome DevTools, Firefox Developer Tools czy Microsoft Edge Developer Tools. Te narzędzia oferują funkcje takie jak inspekcja elementów DOM, debugowanie JavaScriptu, monitorowanie sieci, profilowanie wydajności i wiele innych przydatnych narzędzi do analizy i debugowania kodu.

> * <b>`console.log()`</b> Często stosuję technikę dodawania instrukcji `console.log()` do kodu w celu wyświetlenia wartości zmiennych, sprawdzenia przepływu sterowania i śledzenia wykonania kodu. Jest to szybki sposób na diagnostykę błędów i monitorowanie zachowania kodu.

> * <b>Testowanie w Izolacji</b> Często izoluję problematyczny fragment kodu i testuję go w izolacji, aby zidentyfikować, czy problem występuje w danym fragmencie kodu czy może wynika z interakcji z innymi częściami aplikacji.

## ➡️ Explain the difference between mutable and immutable objects

> Mutable objects are those whose state can be modified after creation, while immutable objects are those whose state cannot be changed after creation.

> * Example of immutable object - numbers, strings and boolean

```bash
let num = 5; // immbutable number
num = 10;    // This creates a new number with value 10 and assigns it to num
```

> * Example of mutable object 

```bash
let arr = [1, 2, 3]; // Mutable array
arr.push(4);         // Modifies arrays by adding an element

```

### Wyjaśnij różnicę pomiędzy obiektami mutowalnymi i niemutowalnymi

> Obiekty mutowalne są tymi, których stan może być modyfikowany po ich utworzeniu, podczas gdy obiekty niemutowalne są tymi, których stan nie może być zmieniony po utworzeniu.

> * Przykład obiektów niemutowalnych :  liczby, ciągi znaków i wartości logiczne

```bash
let num = 5; // Niemutowalna liczba
num = 10;    // To tworzy nową liczbę o wartości 10 i przypisuje ją do num
```

> * Przykład obiektów mutowalnych - tablice, obiekty

```bash
let arr = [1, 2, 3]; // Mutowalna tablica
arr.push(4);         // Modyfikuje tablicę przez dodanie elementu

```
## ➡️ Explain the difference between synchronous and asynchronous functions.

> * Synchronous functions are those that execute one after the other, in the order they are called, and each function must complete before the next one begins. In other words, synchronous functions block further execution of code until they finish.

```bash
console.log('Start');
const data = fetchData(); // Ta funkcja może chwilę trwać
console.log('Data:', data); // Wykonanie kodu czeka, aż fetchData() zakończy działanie
console.log('End');

// Start
// Data: data
// End
```

> * Asynchronous functions, on the other hand, allow other code to run while they execute in the background. Instead of waiting for an operation to complete, asynchronous functions return immediately, and the program continues to execute. Once the asynchronous operation finishes, a callback function is called to handle the result.

```bash
console.log('Start');
fetchData((data) => { // Ta funkcja działa asynchronicznie
  console.log('Data:', data); // Ta linia zostanie wykonana później
});
console.log('End');

// Start
// End
// Data: data

```

### Wyjasnij roznice miedzy sychronicznymi a asynchronicznymi funkcjami

> * Funkcje synchroniczne są tymi, które wykonują się kolejno, w kolejności, w jakiej są wywoływane, i każda funkcja musi zakończyć się przed rozpoczęciem następnej. Innymi słowy, funkcje synchroniczne blokują dalsze wykonywanie kodu, dopóki się nie zakończą.

```bash
console.log('Start');
const data = fetchData(); // Ta funkcja może chwilę trwać
console.log('Data:', data); // Wykonanie kodu czeka, aż fetchData() zakończy działanie
console.log('End');

// Start
// Data: data
// End
```

> *  Funkcje asynchroniczne pozwalają na wykonywanie innego kodu podczas ich wykonywania się w tle. Zamiast czekać, aż operacja zostanie zakończona, funkcje asynchroniczne zwracają natychmiast, a program kontynuuje wykonywanie. Po zakończeniu operacji asynchronicznej wywoływana jest funkcja zwrotna (callback), która obsługuje wynik.

```bash
console.log('Start');
fetchData((data) => { // Ta funkcja działa asynchronicznie
  console.log('Data:', data); // Ta linia zostanie wykonana później
});
console.log('End');

// Start
// End
// Data: data

```

## ➡️ What is event loop?

> This is how the event loop works

> * Call Stack JavaScript is single-threaded, meaning it can only execute one piece of code at a time. The call stack is a data structure that keeps track of the currently executing function or context. When a function is called, it is pushed onto the stack, and when it returns, it is popped off the stack.

> * Task Queue (Callback Queue) Asynchronous operations, such as setTimeout callbacks, DOM events, or AJAX requests, are handled separately from the call stack. When these operations complete, their callback functions are placed into the task queue.

> * Event Loop The event loop continuously monitors the call stack and the task queue. If the call stack is empty, it takes the first function from the task queue and pushes it onto the call stack to be executed.

> This process repeats indefinitely, allowing JavaScript to handle asynchronous operations efficiently without blocking the main thread. It ensures that the execution of JavaScript code remains non-blocking and responsive, even when dealing with time-consuming tasks or I/O operations.

### Jak działa petla zdarzen

> Oto jak działa pętla zdarzen

> * Stos Wywołań JavaScript jest jednowątkowy, co oznacza, że może wykonywać tylko jedną część kodu na raz. Stos wywołań to struktura danych, która śledzi aktualnie wykonywaną funkcję lub kontekst. Gdy funkcja jest wywoływana, jest dodawana na stos, a gdy zwraca wartość, jest zdejmowana ze stosu

> * Kolejka Zadań (Kolejka Zwrotnych Funkcji): Operacje asynchroniczne, takie jak zwroty z funkcji setTimeout, zdarzenia DOM lub żądania AJAX, są obsługiwane oddzielnie od stosu wywołań. Gdy te operacje zostają zakończone, ich funkcje zwrotne są umieszczane w kolejce zadań

> * Pętla Zdarzeń: Pętla zdarzeń ciągle monitoruje stos wywołań i kolejkę zadań. Jeśli stos wywołań jest pusty, pętla zdarzeń pobiera pierwszą funkcję z kolejki zadań i dodaje ją na stos, aby została wykonana

> Ten proces powtarza się w nieskończoność, umożliwiając JavaScriptowi skuteczne obsługiwanie operacji asynchronicznych bez blokowania głównego wątku. Zapewnia to, że wykonanie kodu JavaScript pozostaje nieblokujące i responsywne, nawet przy wykonywaniu czasochłonnych zadań lub operacji wejścia/wyjścia.

## ➡️ What are the differences between variables created using `let`, `var` or `const`?

> <b>Range</b>
> * `var` Function scope or global scope.
> * `let` Block scope.
> * `const` Block scope.

> <b>Hoisting</b>

> * `var` Raised to the top of its function or global scope and initialized to undefined.
> * `let` Raised to the top of its block scope, but not initialized. Accessing them before declaration causes a ReferenceError.
> * `const` Like let, uninitialized and also cannot be reassigned. Accessing them before declaration also causes a ReferenceError.

> <b>Reassignment</b>

> * `var` Can be reassigned and redeclared in its scope.
> * `let` Can be reassigned within its scope, but cannot be redeclared.
> * `const` Cannot be reassigned or redeclared. However, objects and arrays declared as const can still be modified.

> <b>Code Dead Zone (TDZ)</b>

> * `var` No code dead zone, variables are initialized to undefined.
> * `let` and `const` There is a dead code zone, accessing them before declaration causes a ReferenceError.

> <b>Global object property</b>

> * `var` Declares a property on a global object (window in browsers).
> * `let` and `const` Do not create properties on the global object when declared globally.

### Jakie sa roznice miedzy zmiennymi `let`, `var` i `const`

> <b>Zasięg</b>
> * `var` Zasięg funkcji lub globalny.
> * `let` Zasięg blokowy.
> * `const` Zasięg blokowy.

> <b>Hoisting</b>

> * `var` Podnoszone na górę swojej funkcji lub globalnego zakresu i inicjowane jako undefined.
> * `let` Podnoszone na górę swojego blokowego zakresu, ale nieinicjowane. Dostęp do nich przed deklaracją powoduje ReferenceError.
> * `const` Podobnie jak let, nieinicjowane i również nie można ich ponownie przypisać. Dostęp do nich przed deklaracją również powoduje ReferenceError.

> <b>Przypisanie ponowne</b>

> * `var` Może być ponownie przypisany i ponownie zadeklarowany w swoim zakresie.
> * `let` Może być ponownie przypisany w swoim zakresie, ale nie może być ponownie zadeklarowany.
> * `const` Nie może być ponownie przypisany ani ponownie zadeklarowany. Jednak obiekty i tablice zadeklarowane jako const mogą nadal być modyfikowane.

> <b>Strefa martwego kodu (TDZ)</b>

> * `var` Brak strefy martwego kodu, zmienne są inicjowane jako undefined.
> * `let` i `const` Istnieje strefa martwego kodu, dostęp do nich przed deklaracją powoduje ReferenceError.

> <b>Właściwość globalnego obiektu</b>

> * `var` Deklaruje właściwość na obiekcie globalnym (window w przeglądarkach).
> * `let` i `const` Nie tworzą właściwości na obiekcie globalnym, gdy są deklarowane globalnie.

## ➡️ What are the differences between ES6 class and ES5 function constructors?

> <b> Syntax </b>
> * ES6 Classes - Use the `class` keyword to define a class.
> * ES5 Function Builders - Defines constructor functions using regular functions.

> <b> Prototype inheritance </b>
> * ES6 Classes - Use the Extends keyword to implement inheritance between classes.
> * ES5 Function Builders - Use function prototypes to make the device inheritable.
> * `extend` - The Extends keyword is used in JavaScript to create inheritance between classes. An inherited class (also called a child class or subclass) can inherit behavior (methods) and properties (fields) from another class (called a parent class or superclass). When a class inherits another class using extends, it inherits on all methods and properties from the parent class. To access the constructor of the parent class in the constructor of the inheriting class, use the super() keyword. This is necessary because the constructor of the parent class can initialize fields that are later inherited by the inherited class.

### Jakie są różnice między konstruktorami funkcji klasy ES6 i ES5?

> <b> Składnia </b> 
> * Klasy ES6 - Używają słowa kluczowego `class` do definiowania klasy.
> * Konstruktory funkcji ES5 - Definiują funkcje konstruktora za pomocą zwykłych funkcji.

```bash
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  sayHello() {
    console.log(`Hello, my name is ${this.name} and I'm ${this.age} years old.`);
  }
}

const person1 = new Person('John', 30);
person1.sayHello(); // Output: Hello, my name is John and I'm 30 years old.

```

```bash
function Person(name, age) {
  this.name = name;
  this.age = age;
}

Person.prototype.sayHello = function() {
  console.log('Hello, my name is ' + this.name + ' and I\'m ' + this.age + ' years old.');
};

var person2 = new Person('Alice', 25);
person2.sayHello(); // Output: Hello, my name is Alice and I'm 25 years old.

```

> <b> Dziedziczenie prototypowe </b> 
> * Klasy ES6 - Używają słowa kluczowego extends do implementowania dziedziczenia między klasami.
> * Konstruktory funkcji ES5 - Używają właściwości prototype, aby ręcznie ustawić dziedziczenie.
> * `extend` - Słowo kluczowe extends jest używane w JavaScript do tworzenia dziedziczenia między klasami. Klasa dziedzicząca (nazywana również klasą potomną lub podklasą) może dziedziczyć zachowanie (metody) i właściwości (pola) od innej klasy (nazywanej klasą nadrzędną lub nadklasą). Kiedy klasa dziedzicząca rozszerza inną klasę za pomocą extends, dziedziczy ona wszystkie metody i właściwości z klasy nadrzędnej. W celu dostępu do konstruktora klasy nadrzędnej w konstruktorze klasy dziedziczącej, używamy słowa kluczowego super(). Jest to konieczne, ponieważ konstruktor klasy nadrzędnej może inicjować pola, które są później wykorzystywane przez klasę dziedziczącą.

```bash
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a sound.`);
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(name); // Wywołanie konstruktora nadklasy
    this.breed = breed;
  }

  speak() {
    console.log(`${this.name} barks.`);
  }
}

const dog = new Dog('Buddy', 'Labrador');
dog.speak(); // Output: Buddy barks.

```
## ➡️ Can you offer a use case for the new arrow `=>` function syntax? How does this new syntax differ from other functions?

> Arrow functions `=>` allow you to preserve the lexical context of `this`, which is useful when working with nested functions or callbacks. They do not have their own arguments object, cannot be used as `new` constructors, and do not have the `super` keyword.

```bash
const numbers = [1, 2, 3, 4, 5];

// Regular function
const square = numbers.map(function(x) {
   return x * x;
});

console.log(square); // Output: [1, 4, 9, 16, 25]

// Arrow function
const squareArrow = numbers.map(x => x * x);

console.log(squareArrow); // Output: [1, 4, 9, 16, 25]

```

### Czy możesz zaproponować przypadek użycia nowej składni funkcji strzałka `=>`? Czym ta nowa składnia różni się od innych funkcji?

> Funkcje strzałkowe `=>` pozwalają na zachowanie leksykalnego kontekstu `this`, co jest przydatne w przypadku pracy z zagnieżdżonymi funkcjami lub wywołaniami zwrotnymi. Nie posiadają własnego obiektu arguments, nie mogą być używane jako konstruktory `new`, ani nie posiadają słowa kluczowego `super`.

```bash
const numbers = [1, 2, 3, 4, 5];

// Zwykła funkcja
const square = numbers.map(function(x) {
  return x * x;
});

console.log(square); // Output: [1, 4, 9, 16, 25]

// Funkcja strzałkowa
const squareArrow = numbers.map(x => x * x);

console.log(squareArrow); // Output: [1, 4, 9, 16, 25]

```

## ➡️ What advantage is there for using the arrow syntax for a method in a constructor?

> In the first example, using regular function syntax, this inside sayHello() loses its context when assigned to sayHello. When sayHello is called, this no longer refers to the person object, which causes a TypeError.

> However, in the second example, using arrow function syntax, this is lexically bound to the Person instance, ensuring that it always refers to the correct object, no matter how the method is called or referenced. Therefore, the method works correctly even when it is assigned to a variable and called separately. This is especially convenient when defining methods in constructors, which reduces potential errors and improves code readability.

```bash
// Using regular function syntax
function Person(name) {
   this.name = name;
   this.sayHello = function() {
     console.log('Hi, my name is ' + this.name);
   };
}

const person = new Person('Alice');
const sayHello = person.sayHello;
sayHello(); // Result: TypeError: Could not read property 'name' undefined

// Using arrow function syntax
function Person(name) {
   this.name = name;
   this.sayHello = () => {
     console.log('Hi, my name is ' + this.name);
   };
}

const person = new Person('Bartek');
const sayHello = person.sayHello;
sayHello(); // Result: Hello, my name is Bartek

```

### Jaka jest korzyść ze stosowania składni strzałek dla metody w konstruktorze?

> W pierwszym przykładzie, używając składni funkcji regularnej, this wewnątrz sayHello() traci swój kontekst, gdy jest przypisany do sayHello. Gdy jest wywołany sayHello, this nie odnosi się już do obiektu person, co powoduje TypeError.

> Jednakże, w drugim przykładzie, korzystając ze składni funkcji strzałkowej, this jest leksykalnie związane z instancją Person, co zapewnia, że zawsze odnosi się do poprawnego obiektu, bez względu na to, jak metoda jest wywoływana lub odwoływana. Dlatego metoda działa poprawnie nawet wtedy, gdy jest przypisana do zmiennej i wywołana osobno. Jest to szczególnie wygodne w przypadku definiowania metod w konstruktorach, co redukuje potencjalne błędy i poprawia czytelność kodu.

```bash
// Za pomocą składni funkcji regularnej
function Person(name) {
  this.name = name;
  this.sayHello = function() {
    console.log('Cześć, nazywam się ' + this.name);
  };
}

const person = new Person('Alicja');
const sayHello = person.sayHello;
sayHello(); // Wynik: TypeError: Nie można odczytać właściwości „name” undefined

// Za pomocą składni funkcji strzałkowej
function Person(name) {
  this.name = name;
  this.sayHello = () => {
    console.log('Cześć, nazywam się ' + this.name);
  };
}

const person = new Person('Bartek');
const sayHello = person.sayHello;
sayHello(); // Wynik: Cześć, nazywam się Bartek

```

## ➡️ What is the definition of a higher-order function?

> A higher-order function is a function that takes another function as an argument or returns a function as a result, or both. In other words, it treats functions as first-class citizens, allowing them to be manipulated and passed around like any other value.

> > In this example, the `operateOnArray` function is a higher-order function that takes another operation function as an argument. It then iterates through the `array` and applies the operation function to each element of the array, and stores the results in a new `result` array. Finally, it returns an array with the transformed values. In this case, the `double` function is passed as an `operation` function and is used to double each number in the input array.

```bash
// Higher order function
function operateOnArray(array, operation) {
   let result = [];
   for (let element of array) {
     result.push(operation(element));
   }
   return result;
}

// The function we pass as an argument
function double(x) {
   return x * 2;
}

// Input array
const numbers = [1, 2, 3, 4, 5];

// Call a higher order function with the double function as an argument
const doubledNumbers = operateOnArray(numbers, double);

console.log(doubledNumbers); // Output: [2, 4, 6, 8, 10]

```

### Jaka jest definicja funkcji wyższego rzędu?

> Funkcja wyższego rzędu to funkcja, która przyjmuje inną funkcję jako argument lub zwraca funkcję jako wynik, lub oba te przypadki. Innymi słowy, traktuje funkcje jako obiekty pierwszej klasy, pozwalając na manipulowanie nimi i przekazywanie ich jak każdej innej wartości.

> W tym przykładzie funkcja `operateOnArray` jest funkcją wyższego rzędu, która przyjmuje inną funkcję operation jako argument. Następnie iteruje po tablicy `array` i stosuje funkcję operation do każdego elementu tablicy, a wyniki zapisuje w nowej tablicy `result`. W końcu zwraca tablicę z przekształconymi wartościami. W tym przypadku funkcja `double` jest przekazana jako funkcja `operation` i jest używana do podwajania każdej liczby w tablicy wejściowej.

```bash
// Funkcja wyższego rzędu
function operateOnArray(array, operation) {
  let result = [];
  for (let element of array) {
    result.push(operation(element));
  }
  return result;
}

// Funkcja, którą przekazujemy jako argument
function double(x) {
  return x * 2;
}

// Tablica wejściowa
const numbers = [1, 2, 3, 4, 5];

// Wywołanie funkcji wyższego rzędu z funkcją double jako argumentem
const doubledNumbers = operateOnArray(numbers, double);

console.log(doubledNumbers); // Output: [2, 4, 6, 8, 10]

```

## ➡️ Can you give an example for destructuring an object or an array?

> In the first example, the object person is destructured into individual variables name, age, and country. In the second example, the array numbers is destructured into individual variables first, second, and the rest of the elements are gathered into the array rest. Destructuring makes it easier to extract values from objects and arrays and assign them to variables in a more concise way.

```bash
// Object to be destructured
const person = {
  name: 'Alice',
  age: 30,
  country: 'USA'
};

// Destructuring the object
const { name, age, country } = person;

console.log(name);     // Output: Alice
console.log(age);      // Output: 30
console.log(country);  // Output: USA

```

```bash
// Array to be destructured
const numbers = [1, 2, 3, 4, 5];

// Destructuring the array
const [first, second, ...rest] = numbers;

console.log(first);   // Output: 1
console.log(second);  // Output: 2
console.log(rest);    // Output: [3, 4, 5]

```

### Czy możesz podać przykład destrukturyzacji obiektu lub tablicy?

> W pierwszym przykładzie obiekt person jest destrukturyzowany na indywidualne zmienne `name`, `age` i `country`. W drugim przykładzie tablica `numbers` jest destrukturyzowana na indywidualne zmienne `first`, `second`, a pozostałe elementy są zbierane do tablicy `rest`. Destrukturyzacja ułatwia ekstrakcję wartości z obiektów i tablic oraz przypisanie ich do zmiennych w bardziej zwięzły sposób.

```bash
// Obiekt poddany destrukturyzacji
const person = {
  name: 'Alicja',
  age: 30,
  country: 'USA'
};

// Destrukturyzacja obiektu
const { name, age, country } = person;

console.log(name);     // Wynik: Alicja
console.log(age);      // Wynik: 30
console.log(country);  // Wynik: USA

```

```bash
// Tablica poddana destrukturyzacji
const numbers = [1, 2, 3, 4, 5];

// Destrukturyzacja tablicy
const [first, second, ...rest] = numbers;

console.log(first);   // Wynik: 1
console.log(second);  // Wynik: 2
console.log(rest);    // Wynik: [3, 4, 5]

```

## ➡️ Can you give an example of generating a string with ES6 Template Literals?

> In this example, the string message is generated using backticks (`) to define the string, and placeholders ${} to insert variables directly into the string. This makes the string interpolation more concise and readable compared to traditional string concatenation methods.

```bash
// Example variables
const name = 'Alice';
const age = 30;

// Generating a string using Template Literals
const message = `Hello, my name is ${name} and I am ${age} years old.`;

console.log(message); // Output: Hello, my name is Alice and I am 30 years old.

```

### Czy możesz podać przykład generowania ciągu znaków za pomocą literałów szablonu ES6?

> W tym przykładzie ciąg znaków message jest generowany za pomocą delty do zdefiniowania ciągu znaków oraz miejsc podstawiania `${}` , aby wstawić zmienne bezpośrednio do ciągu znaków. Dzięki temu interpolacja ciągów znaków jest bardziej zwięzła i czytelna w porównaniu z tradycyjnymi metodami konkatenacji ciągów znaków.

```bash
// Przykładowe zmienne
const name = 'Alicja';
const age = 30;

// Generowanie ciągu znaków za pomocą szablonów literałów
const message = `Cześć, nazywam się ${name} i mam ${age} lat.`;

console.log(message); // Wynik: Cześć, nazywam się Alicja i mam 30 lat.

```

## ➡️ Can you give an example of a curry function and why this syntax offers an advantage?

> In this example, the curry function takes the fn function as an argument and returns a currified version of the function. A currified function takes arguments one at a time, returning a new function with each argument until all required arguments are provided. When all arguments are provided, the original function is called and the result is returned.

> This syntax offers the advantage of allowing partial argument supply, making the function more flexible and reusable. It allows you to create new functions by providing a subset of the arguments in advance, which can be useful in scenarios where you want to repeatedly use a function with some fixed arguments. Additionally, currification promotes feature composition and helps create more compositional and modular code.

```bash
// Curry function
function curry(fn) {
   return function curried(...args) {
     if (args.length >= fn.length) {
       return fn(...args);
     } else {
       return function(...moreArgs) {
         return curried(...args, ...moreArgs);
       };
     }
   };
}

// Example function to be currified
function add(a, b, c) {
   return a + b + c;
}

// Currified version of the add function
const curriedAdd = curry(add);

console.log(curriedAdd(1)(2)(3)); // Score: 6
console.log(curriedAdd(1, 2)(3)); // Score: 6
console.log(curriedAdd(1)(2, 3)); // Score: 6
console.log(curriedAdd(1, 2, 3)); // Score: 6

```

### Czy możesz podać przykład funkcji curry i dlaczego ta składnia oferuje przewagę?

> W tym przykładzie funkcja curry przyjmuje funkcję fn jako argument i zwraca zcurryfikowaną wersję tej funkcji. Funkcja zcurryfikowana przyjmuje argumenty po jednym, zwracając nową funkcję z każdym argumentem, aż wszystkie wymagane argumenty zostaną dostarczone. Gdy wszystkie argumenty są dostarczone, oryginalna funkcja jest wywoływana, a wynik zostaje zwrócony.

> Ta składnia oferuje przewagę, ponieważ pozwala na częściowe dostarczanie argumentów, sprawiając, że funkcja staje się bardziej elastyczna i wielokrotnego użytku. Umożliwia tworzenie nowych funkcji, dostarczając podzbioru argumentów z góry, co może być przydatne w scenariuszach, gdzie chcemy wielokrotnie użyć funkcji z pewnymi ustalonymi argumentami. Dodatkowo, zcurryfikowanie promuje kompozycję funkcji i pomaga w tworzeniu bardziej kompozycyjnego i modularnego kodu.

```bash
// Funkcja curry
function curry(fn) {
  return function curried(...args) {
    if (args.length >= fn.length) {
      return fn(...args);
    } else {
      return function(...moreArgs) {
        return curried(...args, ...moreArgs);
      };
    }
  };
}

// Przykładowa funkcja do zcurryfikowania
function add(a, b, c) {
  return a + b + c;
}

// Zcurryfikowana wersja funkcji add
const curriedAdd = curry(add);

console.log(curriedAdd(1)(2)(3)); // Wynik: 6
console.log(curriedAdd(1, 2)(3)); // Wynik: 6
console.log(curriedAdd(1)(2, 3)); // Wynik: 6
console.log(curriedAdd(1, 2, 3)); // Wynik: 6

```

## ➡️ What are the benefits of using spread syntax and how is it different from rest syntax?

> Spread Syntax

> * Array/Object Manipulation: The spread syntax allows you to expand arrays and objects into single elements or properties. This is useful for tasks such as concatenating arrays, copying arrays/objects, and passing multiple arguments to functions.

> * Array/Object Cloning: Provides a concise way to clone arrays and objects without mutating the original data.

> * Function Calls: Can be used to pass multiple arguments to a function where multiple parameters are expected.

> Example of using the spread syntax:

```bash
// Sample array
const numbers = [1, 2, 3];

// Create a copy of the array using the spread syntax
const copyNumbers = [...numbers];

console.log(copyNumbers); // Result: [1, 2, 3]
```

>Rest Syntax:

> * Parameter collection: The rest syntax allows you to collect the remaining arguments in a function into an array. This is especially useful when you have a variable number of arguments in your function definition.

> * Destructuring: The rest syntax can be used in destructuring to capture the remaining elements into an array.

> * Flexible Function Signatures: Provides flexibility in function signatures by allowing functions to accept any number of arguments.

> Difference

> * Syntax Spread: Used to expand an iterable (such as an array or string) into single elements. Typically used in function calls, array literals, and object literals.

> * Syntax Rest: Used to collect multiple elements into one array. It is mainly used in function parameters and destructuring assignments.

> Example of using the rest syntax in a function:

```bash
// A function that sums any number of arguments
function sum(...args) {
   return args.reduce((total, current) => total + current, 0);
}

console.log(sum(1, 2, 3, 4, 5)); // Result: 15

```

### Jakie są korzyści ze stosowania składni rozproszonej i czym różni się ona od składni reszty?

> Spread Syntax

> * Manipulacja tablicami/obiektami: Składnia spread pozwala na rozwijanie tablic i obiektów na pojedyncze elementy lub właściwości. Jest to przydatne do zadań takich jak łączenie tablic, kopiowanie tablic/obiektów i przekazywanie wielu argumentów do funkcji.

> * Klonowanie tablic/obiektów: Zapewnia zwięzły sposób klonowania tablic i obiektów bez mutowania oryginalnych danych.

> * Wywołania funkcji: Może być używany do przekazywania wielu argumentów do funkcji, gdzie oczekuje się wielu parametrów.

> Przykład użycia składni spread:

```bash
// Przykładowa tablica
const numbers = [1, 2, 3];

// Tworzenie kopii tablicy za pomocą składni spread
const copyNumbers = [...numbers];

console.log(copyNumbers); // Wynik: [1, 2, 3]

```

> Rest Syntax:

> * Gromadzenie parametrów: Składnia rest pozwala na zbieranie pozostałych argumentów w funkcji do tablicy. Jest to szczególnie przydatne, gdy masz zmienną liczbę argumentów w definicji funkcji.

> * Destrukturyzacja: Składnia rest może być używana w destrukturyzacji do przechwytywania pozostałych elementów do tablicy.

> * Elastyczne sygnatury funkcji: Zapewnia elastyczność w sygnaturach funkcji, pozwalając funkcjom akceptować dowolną liczbę argumentów.

> Różnica

> * Składnia Spread: Służy do rozwijania iterowalnego (takiego jak tablica lub łańcuch) na pojedyncze elementy. Zazwyczaj używana jest w wywołaniach funkcji, literałach tablic i literałach obiektów.

> * Składnia Rest: Służy do zbierania wielu elementów do jednej tablicy. Jest głównie używana w parametrach funkcji i destrukturyzacji przypisań.

> Przykład użycia składni rest w funkcji:

```bash
// Funkcja sumująca dowolną liczbę argumentów
function sum(...args) {
  return args.reduce((total, current) => total + current, 0);
}

console.log(sum(1, 2, 3, 4, 5)); // Wynik: 15

```

## ➡️ How can you share code between files?

> * Module Import/Export (ES6):

```bash
// In the module.js file
export function greet(name) {
   return `Hello, ${name}!`;
}

// In the file using.js
import { greet } from './module';
console.log(greet('World')); // Result: Hello, World!

```

> * CommonJS modules (Node.js):

```bash
// In the module.js file
function greet(name) {
   return `Hello, ${name}!`;
}
module.exports = greet;

// In the file using.js
const greet = require('./module');
console.log(greet('World')); // Result: Hello, World!
```

> * Global variables:

```bash
// In the variables.js file
window.myVariable = 42;

// In the file using.js
console.log(window.myVariable); // Result: 42

```

### Jak udostępnić kod pomiędzy plikami?

> * Import/Export modułów (ES6):

```bash
// W pliku modułu.js
export function greet(name) {
  return `Hello, ${name}!`;
}

// W pliku korzystającym.js
import { greet } from './moduł';
console.log(greet('World')); // Wynik: Hello, World!

```

> * Moduły CommonJS (Node.js):

```bash
// W pliku moduł.js
function greet(name) {
  return `Hello, ${name}!`;
}
module.exports = greet;

// W pliku korzystającym.js
const greet = require('./moduł');
console.log(greet('World')); // Wynik: Hello, World!
```

> * Zmienne globalne:

```bash
// W pliku zmiennych.js
window.myVariable = 42;

// W pliku korzystającym.js
console.log(window.myVariable); // Wynik: 42

```
## ➡️ Why you might want to create static class members?

> * Performance: Static elements can improve performance by reducing memory usage and avoiding unnecessary data duplication. Because they are shared between all instances, they only need to be initialized once and can be accessed without having to create a new instance of the class.

> * Global Access: Static elements can be accessed directly from the class without the need to create an instance. This makes it easier to provide global access to specific functionality or data related to the class as a whole.

```bash
class MathUtils {
   // Static method to calculate the sum of two numbers
   static add(a, b) {
     return a + b;
   }

   // Static property with a constant value
   static PI = 3.14159;
}

// Calling a static method
console.log(MathUtils.add(2, 3)); // Score: 5

//Access the static property
console.log(MathUtils.PI); // Result: 3.14159

```

### Dlaczego warto tworzyć statyczne elementy klasy?

> * Wydajność: Statyczne elementy mogą poprawić wydajność, zmniejszając zużycie pamięci i unikając niepotrzebnego duplikowania danych. Ponieważ są one współdzielone między wszystkimi instancjami, potrzebują zostać zainicjalizowane tylko raz i mogą być dostępne bez konieczności tworzenia nowej instancji klasy.

> * Globalny Dostęp: Statyczne elementy mogą być dostępne bezpośrednio z klasy bez konieczności tworzenia instancji. Ułatwia to zapewnienie globalnego dostępu do określonej funkcjonalności lub danych związanych z klasą jako całością.

```bash
class MathUtils {
  // Statyczna metoda do obliczania sumy dwóch liczb
  static add(a, b) {
    return a + b;
  }

  // Statyczna właściwość z wartością stałą
  static PI = 3.14159;
}

// Wywołanie statycznej metody
console.log(MathUtils.add(2, 3)); // Wynik: 5

// Dostęp do statycznej właściwości
console.log(MathUtils.PI); // Wynik: 3.14159

```

## ➡️ What is the difference between while and do-while loops in JavaScript?

> In the while loop, the condition i < 5 is evaluated first, so if i is initially not less than 5, the loop body is never executed. In contrast, in the do-while loop, the loop body is executed at least once before checking the condition, ensuring that the loop body executes at least once even if the condition is initially false.

```bash
// while loop
let i = 0;
while (i < 5) {
  console.log(i);
  i++;
}

// do-while loop
let j = 0;
do {
  console.log(j);
  j++;
} while (j < 5);

```
### Jaka jest różnica między pętlami while i do-while w JavaScript?

> W pętli while warunek i < 5 jest najpierw oceniany, więc jeśli i początkowo nie jest mniejsze niż 5, ciało pętli nigdy nie zostanie wykonane. W przeciwieństwie do tego, w pętli do-while ciało pętli jest wykonywane co najmniej raz przed sprawdzeniem warunku, co zapewnia wykonanie ciała pętli przynajmniej raz, nawet jeśli warunek początkowo jest fałszywy.

```bash
// pętla while
let i = 0;
while (i < 5) {
  console.log(i);
  i++;
}

// pętla do-while
let j = 0;
do {
  console.log(j);
  j++;
} while (j < 5);

```

## ➡️ What is a promise? Where and how would you use promise?

> `Promise` is an object representing the eventual completion or failure of an asynchronous operation. It is used to support asynchronous operations in JavaScript, such as retrieving data from a server, reading a file, or performing a time-consuming task where the result is not immediately available.

>States of promises

> * Pending: Initial status, neither fulfilled nor rejected.

> * Fulfilled: The operation completed successfully.

> * Rejected: The operation failed with an error.

> Promises provide cleaner and more flexible alternatives to traditional callback-based asynchronous programming. They allow you to chain multiple asynchronous operations, handle errors efficiently, and simplify error handling using the `.catch()` method.

```bash
const fetchData = () => {
   return new Promise((resolve, reject) => {
     setTimeout(() => {
       const data = 'Data from server';
       // Simulate a successful download
       resolve(date);
      
       // Simulate an error while downloading
       // reject('Error while retrieving data');
     }, 2000);
   });
};

fetchData()
   .then(date => {
     console.log('Data:', date);
   })
   .catch(error => {
     console.error('Error:', error);
   });

```

> In this example, the fetchData function returns a promise that will be resolved with data fetched from the server after a simulated delay. The `.then()` method is used to handle the successful completion of the promise, while the `.catch()` method is used to handle errors that will occur during the asynchronous operation.

### Co to jest obietnica? Gdzie i jak użyłbyś obietnicy?

> `Promise` to obiekt reprezentujący eventualną realizację lub niepowodzenie operacji asynchronicznej. Jest używany do obsługi operacji asynchronicznych w JavaScript, takich jak pobieranie danych z serwera, czytanie pliku lub wykonanie zadania czasochłonnego, gdzie wynik nie jest natychmiast dostępny.

> Stany obietnic 

> * Oczekujący: Stan początkowy, ani spełniony, ani odrzucony.

> * Spełniony: Operacja została zakończona pomyślnie.

> * Odrzucony: Operacja zakończyła się niepowodzeniem z błędem.

> Obietnice zapewniają czystsze i bardziej elastyczne alternatywy dla tradycyjnego programowania asynchronicznego opartego na wywołaniach zwrotnych. Pozwalają one na łączenie wielu operacji asynchronicznych, efektywne obsługiwania błędów i upraszczanie obsługi błędów za pomocą metody `.catch()`.

```bash
const fetchData = () => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const data = 'Dane z serwera';
      // Symulacja udanego pobrania
      resolve(data);
      
      // Symulacja błędu podczas pobierania
      // reject('Błąd podczas pobierania danych');
    }, 2000);
  });
};

fetchData()
  .then(data => {
    console.log('Dane:', data);
  })
  .catch(error => {
    console.error('Błąd:', error);
  });

```

> W tym przykładzie funkcja fetchData zwraca obietnicę, która zostanie rozwiązana danymi pobranymi z serwera po symulowanym opóźnieniu. Metoda `.then()` jest używana do obsługi pomyślnego zakończenia obietnicy, podczas gdy metoda `.catch()` służy do obsługi błędów, które wystąpią podczas operacji asynchronicznej.

## ➡️ Discuss how you might use Object Oriented Programming principles when coding with JavaScript.

> Object-oriented programming (OOP) principles can be effectively applied when coding with JavaScript to create modular, reusable, and maintainable code. Here's how you might use OOP principles in JavaScript:

> * Encapsulation: Use objects to encapsulate related data and behavior into a single unit. This helps in organizing code and preventing unintended interference with data.
javascript

```bash
// Encapsulation example
class Car {
  constructor(brand, model) {
    this.brand = brand;
    this.model = model;
  }
  
  drive() {
    console.log(`Driving ${this.brand} ${this.model}`);
  }
}

const myCar = new Car('Toyota', 'Corolla');
myCar.drive(); // Output: Driving Toyota Corolla
```

> * Abstraction: Hide the complex implementation details of an object and only expose the necessary interfaces. This allows for simpler usage and reduces complexity.
javascript

```bash
// Abstraction example
class Shape {
  constructor(color) {
    this.color = color;
  }
  
  draw() {
    throw new Error('Method draw() must be implemented');
  }
}

class Circle extends Shape {
  constructor(radius, color) {
    super(color);
    this.radius = radius;
  }
  
  draw() {
    console.log(`Drawing a ${this.color} circle with radius ${this.radius}`);
  }
}

const myCircle = new Circle(5, 'blue');
myCircle.draw(); // Output: Drawing a blue circle with radius 5
```

> * Inheritance: Use inheritance to create a hierarchy of classes where child classes inherit properties and methods from parent classes. This promotes code reuse and makes it easier to maintain and extend code.
javascript

```bash
// Inheritance example
class Animal {
  constructor(name) {
    this.name = name;
  }
  
  speak() {
    console.log(`${this.name} makes a sound`);
  }
}

class Dog extends Animal {
  constructor(name) {
    super(name);
  }
  
  speak() {
    console.log(`${this.name} barks`);
  }
}

const myDog = new Dog('Buddy');
myDog.speak(); // Output: Buddy barks

```

> * Polymorphism: Use polymorphism to allow objects of different classes to be treated as objects of a common superclass. This promotes flexibility and simplifies code.
javascript

```bash
// Polymorphism example
class Shape {
  draw() {
    console.log('Drawing a shape');
  }
}

class Circle extends Shape {
  draw() {
    console.log('Drawing a circle');
  }
}

class Rectangle extends Shape {
  draw() {
    console.log('Drawing a rectangle');
  }
}

const shapes = [new Circle(), new Rectangle()];
shapes.forEach(shape => shape.draw());
```

> By applying these OOP principles, you can write cleaner, more modular, and maintainable JavaScript code that is easier to understand and scale.

### Omów, w jaki sposób możesz wykorzystać zasady programowania obiektowego podczas kodowania za pomocą JavaScript.


> Zasady programowania obiektowego (OOP) można skutecznie zastosować podczas kodowania za pomocą JavaScript w celu stworzenia kodu modułowego, wielokrotnego użytku i łatwego w utrzymaniu. Oto jak możesz wykorzystać zasady OOP w JavaScript:

> * Enkapsulacja: Wykorzystuj obiekty do enkapsulacji powiązanych danych i zachowań w jednostkę. Pomaga to w organizacji kodu i zapobiega niezamierzonemu ingerowaniu w dane.

```bash
// Encapsulation example
class Car {
  constructor(brand, model) {
    this.brand = brand;
    this.model = model;
  }
  
  drive() {
    console.log(`Driving ${this.brand} ${this.model}`);
  }
}

const myCar = new Car('Toyota', 'Corolla');
myCar.drive(); // Output: Driving Toyota Corolla
```

> * Abstrakcja: Ukryj złożone szczegóły implementacyjne obiektu i udostępnij tylko niezbędne interfejsy. Umożliwia to prostsze użycie i redukuje złożoność.

```bash
// Abstraction example
class Shape {
  constructor(color) {
    this.color = color;
  }
  
  draw() {
    throw new Error('Method draw() must be implemented');
  }
}

class Circle extends Shape {
  constructor(radius, color) {
    super(color);
    this.radius = radius;
  }
  
  draw() {
    console.log(`Drawing a ${this.color} circle with radius ${this.radius}`);
  }
}

const myCircle = new Circle(5, 'blue');
myCircle.draw(); // Output: Drawing a blue circle with radius 5
```

> * Dziedziczenie: Wykorzystuj dziedziczenie do tworzenia hierarchii klas, gdzie klasy potomne dziedziczą właściwości i metody po klasach nadrzędnych. Promuje to ponowne wykorzystanie kodu i ułatwia jego utrzymanie i rozbudowę.

```bash
// Inheritance example
class Animal {
  constructor(name) {
    this.name = name;
  }
  
  speak() {
    console.log(`${this.name} makes a sound`);
  }
}

class Dog extends Animal {
  constructor(name) {
    super(name);
  }
  
  speak() {
    console.log(`${this.name} barks`);
  }
}

const myDog = new Dog('Buddy');
myDog.speak(); // Output: Buddy barks

```

> * Polimorfizm: Wykorzystuj polimorfizm, aby obiekty różnych klas mogły być traktowane jako obiekty wspólnego nadklasy. Promuje to elastyczność i upraszcza kod.

```bash
// Polymorphism example
class Shape {
  draw() {
    console.log('Drawing a shape');
  }
}

class Circle extends Shape {
  draw() {
    console.log('Drawing a circle');
  }
}

class Rectangle extends Shape {
  draw() {
    console.log('Drawing a rectangle');
  }
}

const shapes = [new Circle(), new Rectangle()];
shapes.forEach(shape => shape.draw());
```

> Stosując te zasady OOP, możesz napisać czystszy, bardziej modułowy i łatwiejszy w utrzymaniu kod JavaScript, który będzie łatwiejszy do zrozumienia i skalowania.

## ➡️ What is the difference between `event.target` and `event.currentTarget`?

> The difference between event.target and event.currentTarget is how they behave when propagating events through the DOM:

> * `event.target` Refers to the element on which the event originally occurred (that is, the deepest element where the event started). Always represents the element that caused the event.

> * `event.currentTarget` Refers to the element to which the event handler is currently attached (that is, the element to which the event listener has been assigned). It remains unchanged throughout the event propagation and does not change.
Here is a simplified explanation:

> If you have nested elements with event listeners (for example a button inside a div), clicking on the inner element (for example the button) will trigger an event on that element, making it an event.target. However, event.currentTarget will remain the same (i.e. the outer element to which the event listener is attached).

> In cases where the event listener is directly attached to a target, both event.target and event.currentTarget will refer to the same element.

```bash
<div id="outer">
   <button id="inner">Click me</button>
</div>

```
```bash
document.getElementById('outer').addEventListener('click', function(event) {
   console.log('Current target:', event.currentTarget.id);
   console.log('Target:', event.target.id);
});

```

```bash
Current target: outer
Target: inner

```

### Jaka jest różnica między `event.target` a `event.currentTarget`?

> Różnica między event.target a event.currentTarget polega na tym, jak się zachowują podczas propagacji zdarzeń w DOM:

> * `event.target` Odnosi się do elementu, na którym pierwotnie wystąpiło zdarzenie (czyli najgłębszego elementu, gdzie zdarzenie się zaczęło). Zawsze reprezentuje element, który spowodował zdarzenie.

> * `event.currentTarget` Odnosi się do elementu, do którego obecnie jest przyczepiony obsługiwacz zdarzeń (czyli elementu, do którego został przypisany nasłuchiwacz zdarzeń). Pozostaje on niezmieniony przez całą propagację zdarzeń i nie ulega zmianie.
Oto uproszczone wyjaśnienie:

> Jeśli masz zagnieżdżone elementy z nasłuchiwaczami zdarzeń (na przykład przycisk wewnątrz diva), kliknięcie na wewnętrznym elemencie (na przykład przycisku) spowoduje wywołanie zdarzenia na tym elemencie, co czyni go event.target. Jednak event.currentTarget pozostanie taki sam (czyli zewnętrzny element, do którego przyczepiony jest nasłuchiwacz zdarzeń).

> W przypadkach, gdy nasłuchiwacz zdarzeń jest bezpośrednio przyczepiony do elementu docelowego, zarówno event.target, jak i event.currentTarget będą odnosić się do tego samego elementu.

```bash
<div id="outer">
  <button id="inner">Kliknij mnie</button>
</div>

```
```bash
document.getElementById('outer').addEventListener('click', function(event) {
  console.log('Bieżący cel:', event.currentTarget.id);
  console.log('Cel:', event.target.id);
});

```

```bash
Bieżący cel: outer
Cel: inner

```

## ➡️ What is the difference between `event.preventDefault()` and `event.stopPropagation()`?

> The difference between `event.preventDefault()` and `event.stopPropagation()` is their impact on event handling:

> `event.preventDefault()`
This method is used to prevent the default action of an event.
Prevents the browser from defaulting on the event, such as submitting a form, navigating to a link, or refreshing a page.
Does not stop the event from propagating through the DOM hierarchy.


> `event.stopPropagation()`
This method is used to stop the event from propagating through the DOM hierarchy.
Prevents an event from rising to its parents or catching down to its children after being handled by the current target.
Does not prevent the default action of the event.

> In summary, `event.preventDefault()` prevents the default event action, while `event.stopPropagation()` stops an event from further propagating through the DOM hierarchy. They are often used together to control both default behavior and event propagation behavior.

```bash
<a href="#" id="link">Click me</a>
<div id="container">
  <button id="button">Button</button>
</div>

```

```bash
document.getElementById('link').addEventListener('click', function(event) {
  event.preventDefault(); // Prevents the default action of following the link
});

document.getElementById('container').addEventListener('click', function(event) {
  event.stopPropagation(); // Stops the event from propagating further
});

```

### Jaka jest różnica między `event.preventDefault()` a `event.stopPropagation()`?


> Różnica między `event.preventDefault()` a `event.stopPropagation()` polega na ich wpływie na obsługę zdarzeń:

> `event.preventDefault()`
Ta metoda jest używana do zapobiegania domyślnej akcji związanej z zdarzeniem.
Uniemożliwia przeglądarce domyślne zachowanie dla zdarzenia, takie jak przesłanie formularza, przejście do linku lub odświeżenie strony.
Nie zatrzymuje zdarzenia przed propagacją przez hierarchię DOM.


> `event.stopPropagation()`
Ta metoda jest używana do zatrzymania propagacji zdarzenia przez hierarchię DOM.
Zapobiega zdarzeniu wzbijającemu się do elementów nadrzędnych lub przechwytującemu w dół do elementów podrzędnych po obsłużeniu przez bieżący element docelowy.
Nie zapobiega domyślnej akcji związanego z zdarzeniem.

> Podsumowując, `event.preventDefault()` zapobiega domyślnej akcji zdarzenia, podczas gdy `event.stopPropagation()` zatrzymuje zdarzenie przed dalszą propagacją przez hierarchię DOM. Często są one używane razem, aby kontrolować zarówno domyślne działanie, jak i zachowanie propagacji zdarzeń.

```bash
<a href="#" id="link">Kliknij mnie</a>
<div id="container">
  <button id="button">Przycisk</button>
</div>

```
```bash
document.getElementById('link').addEventListener('click', function(event) {
  event.preventDefault(); // Zapobiega domyślnej akcji przejścia do linku
});

document.getElementById('container').addEventListener('click', function(event) {
  event.stopPropagation(); // Zatrzymuje zdarzenie przed dalszą propagacją
});

```
