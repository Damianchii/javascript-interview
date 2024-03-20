
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

## ➡️ Explain how this works in JavaScript.
