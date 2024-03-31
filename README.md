
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
