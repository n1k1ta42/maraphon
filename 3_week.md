## **Третья Неделя: Основы JavaScript и Взаимодействие с DOM**

### **1. JavaScript: Управление DOM**

#### **1.1. Что такое DOM?**
DOM (Document Object Model) — это программный интерфейс для HTML и XML документов. Он представляет страницу в виде объекта, с которым можно взаимодействовать через JavaScript, изменяя структуру, стиль и содержание страницы.

#### **1.2. Выбор Элементов на Странице**

1. **`document.getElementById`**: Выбирает элемент по его ID.

   ```javascript
   const header = document.getElementById('main-header');
   ```

2. **`document.querySelector`**: Выбирает первый элемент, соответствующий CSS-селектору.

   ```javascript
   const firstButton = document.querySelector('button');
   ```

3. **`document.querySelectorAll`**: Выбирает все элементы, соответствующие CSS-селектору.

   ```javascript
   const allButtons = document.querySelectorAll('button');
   ```

4. **`document.getElementsByClassName`**: Выбирает элементы по классу.

   ```javascript
   const items = document.getElementsByClassName('item');
   ```

#### **1.3. Изменение Содержимого и Стилей Элементов**

1. **Изменение Текста:**

   ```javascript
   const paragraph = document.querySelector('p');
   paragraph.textContent = "Новый текст абзаца.";
   ```

2. **Изменение HTML Содержимого:**

   ```javascript
   const container = document.querySelector('.container');
   container.innerHTML = "<h2>Обновленный Контент</h2>";
   ```

3. **Изменение Стилей:**

   ```javascript
   const header = document.querySelector('h1');
   header.style.color = "#e74c3c";
   header.style.fontSize = "3em";
   ```

#### **1.4. Добавление и Удаление Классов**

1. **Добавление Класса:**

   ```javascript
   const box = document.querySelector('.box');
   box.classList.add('highlight');
   ```

2. **Удаление Класса:**

   ```javascript
   box.classList.remove('highlight');
   ```

3. **Переключение Класса:**

   ```javascript
   box.classList.toggle('active');
   ```

#### **1.5. Изменение Стилей через CSS Классы**

Вместо непосредственного изменения стилей через `element.style`, можно добавлять или удалять CSS-классы для управления стилями.

**CSS:**

```css
.highlight {
    background-color: yellow;
    font-weight: bold;
}

.hide {
    display: none;
}
```

**JavaScript:**

```javascript
const paragraph = document.querySelector('p');

// Добавление класса 'highlight'
paragraph.classList.add('highlight');

// Удаление класса 'highlight'
paragraph.classList.remove('highlight');

// Переключение между классами
paragraph.classList.toggle('highlight');
```

### **2. JavaScript: Обработка Событий**

#### **2.1. Что такое События?**
События — это действия или происшествия, происходящие в браузере, к которым можно привязать обработчики для выполнения определенных действий. Примеры событий: клики мышкой, ввод текста, загрузка страницы и др.

#### **2.2. Добавление Обработчиков Событий**

**Синтаксис:**
```javascript
element.addEventListener('event', function);
```

**Пример: Обработка Кликов по Кнопке**

```javascript
const button = document.querySelector('button');

button.addEventListener('click', function() {
    alert("Кнопка была нажата!");
});
```

#### **2.3. Типичные Типы Событий**

1. **Клик (click):**

   ```javascript
   button.addEventListener('click', () => {
       console.log("Кнопка кликнута.");
   });
   ```

2. **Ввод (input):**

   ```javascript
   const input = document.querySelector('input');

   input.addEventListener('input', (event) => {
       console.log("Текущее значение:", event.target.value);
   });
   ```

3. **Отправка формы (submit):**

   ```javascript
   const form = document.getElementById('feedback-form');

   form.addEventListener('submit', (event) => {
       event.preventDefault(); // Предотвращает перезагрузку страницы
       console.log("Форма отправлена!");
   });
   ```

#### **2.4. Делегирование Событий**

Делегирование событий позволяет добавлять один обработчик событий для нескольких элементов, используя всплытие событий.

**Пример:**

```html
<ul id="item-list">
    <li>Элемент 1</li>
    <li>Элемент 2</li>
    <li>Элемент 3</li>
</ul>
```

```javascript
const itemList = document.getElementById('item-list');

itemList.addEventListener('click', (event) => {
    if (event.target && event.target.nodeName === "LI") {
        console.log("Нажатый элемент:", event.target.textContent);
    }
});
```

**Пояснения:**
- Обработчик события добавляется к родительскому элементу `<ul>`.
- При клике на `<li>` проверяется, что цель события — именно `<li>`, и выполняется действие.

### **3. JavaScript: Функции и Область Видимости**

#### **3.1. Объявление и Вызов Функций**

1. **Function Declaration:**

   ```javascript
   function sayHello(name) {
       console.log("Привет, " + name + "!");
   }

   sayHello("Анна"); // Выведет: Привет, Анна!
   ```

2. **Function Expression:**

   ```javascript
   const greet = function(name) {
       console.log("Здравствуйте, " + name + "!");
   };

   greet("Иван"); // Выведет: Здравствуйте, Иван!
   ```

3. **Arrow Function:**

   ```javascript
   const welcome = (name) => {
       console.log("Добро пожаловать, " + name + "!");
   };

   welcome("Мария"); // Выведет: Добро пожаловать, Мария!
   ```

#### **3.2. Параметры и Возврат Значений**

1. **Параметры:**

   ```javascript
   function add(a, b) {
       return a + b;
   }

   let result = add(5, 3); // result = 8
   ```

2. **Возврат Значений:**

   ```javascript
   const multiply = (a, b) => a * b;
   let product = multiply(4, 6); // product = 24
   ```

#### **3.3. Область Видимости (Scope)**

1. **Глобальная Область Видимости:**
    - Переменные, объявленные вне функций или блоков, доступны повсеместно.

   ```javascript
   let globalVar = "Я глобальная переменная.";

   function showVar() {
       console.log(globalVar);
   }

   showVar(); // Выведет: Я глобальная переменная.
   ```

2. **Локальная Область Видимости:**
    - Переменные, объявленные внутри функции або блока, доступны только внутри них.

   ```javascript
   function display() {
       let localVar = "Я локальная переменная.";
       console.log(localVar);
   }

   display(); // Выведет: Я локальная переменная.
   console.log(localVar); // Ошибка: localVar не определена
   ```

### **4. Практическое Задание: Интерактивная Страница "Список Дел"**

Создайте интерактивную страницу "Список дел", где пользователи могут добавлять и удалять задачи.

#### **Шаг 1: Создание HTML-Структуры**

**HTML:**

```html
<section>
    <h2>Список Дел</h2>
    <form id="todo-form">
        <input type="text" id="todo-input" placeholder="Добавить новое дело" required>
        <button type="submit">Добавить</button>
    </form>
    <ul id="todo-list">
        <!-- Задачи будут добавляться здесь -->
    </ul>
</section>
```

#### **Шаг 2: Стилизация с помощью CSS**

**CSS:**

```css
#todo-form {
    display: flex;
    justify-content: center;
    margin-bottom: 20px;
}

#todo-input {
    width: 60%;
    padding: 10px;
    border: 2px solid #bdc3c7;
    border-radius: 4px 0 0 4px;
    font-size: 1em;
}

#todo-form button {
    padding: 10px 20px;
    border: 2px solid #bdc3c7;
    border-left: none;
    background-color: #27ae60;
    color: #ffffff;
    cursor: pointer;
    border-radius: 0 4px 4px 0;
}

#todo-form button:hover {
    background-color: #2ecc71;
}

#todo-list {
    list-style-type: none;
    max-width: 600px;
    margin: 0 auto;
    padding: 0;
}

#todo-list li {
    display: flex;
    justify-content: space-between;
    background-color: #ecf0f1;
    margin-bottom: 10px;
    padding: 10px;
    border-radius: 4px;
}

#todo-list li:hover {
    background-color: #dcdde1;
}

.delete-button {
    background-color: #e74c3c;
    border: none;
    color: #ffffff;
    padding: 5px 10px;
    cursor: pointer;
    border-radius: 4px;
}

.delete-button:hover {
    background-color: #c0392b;
}
```

#### **Шаг 3: Добавление Функционала с помощью JavaScript**

**JavaScript (`script.js`):**

```javascript
// Выбор элементов формы и списка
const todoForm = document.getElementById('todo-form');
const todoInput = document.getElementById('todo-input');
const todoList = document.getElementById('todo-list');

// Обработчик отправки формы
todoForm.addEventListener('submit', function(event) {
    event.preventDefault(); // Предотвращает перезагрузку страницы

    const todoText = todoInput.value.trim();

    if (todoText !== "") {
        addTodoItem(todoText);
        todoInput.value = ""; // Очищает поле ввода
    }
});

// Функция добавления нового элемента списка
function addTodoItem(text) {
    // Создание нового элемента <li>
    const li = document.createElement('li');

    // Создание текста задачи
    const span = document.createElement('span');
    span.textContent = text;

    // Создание кнопки удаления
    const deleteBtn = document.createElement('button');
    deleteBtn.textContent = "Удалить";
    deleteBtn.classList.add('delete-button');

    // Добавление обработчика события удаления
    deleteBtn.addEventListener('click', function() {
        todoList.removeChild(li);
    });

    // Добавление элементов в <li>
    li.appendChild(span);
    li.appendChild(deleteBtn);

    // Добавление <li> в список
    todoList.appendChild(li);
}
```

**Пояснения:**
- **Обработчик `submit` на форме:** Вызывается при отправке формы. Предотвращает стандартное поведение формы и добавляет новую задачу, если поле ввода не пусто.
- **Функция `addTodoItem`:** Создает новый элемент списка `<li>`, добавляет в него текст задачи и кнопку удаления, а затем добавляет `<li>` в основной список.
- **Кнопка удаления:** При клике удаляет соответствующий элемент списка из DOM.

#### **Шаг 4: Тестирование Функционала**

1. **Добавление задач:**
    - Введите текст в поле ввода и нажмите "Добавить".
    - Убедитесь, что новая задача появляется в списке.

2. **Удаление задач:**
    - Нажмите кнопку "Удалить" рядом с задачей.
    - Убедитесь, что задача исчезает из списка.

3. **Валидация:**
    - Попробуйте добавить пустую задачу. Убедитесь, что она не добавляется (поле ввода обязательно для заполнения).


---
## **Дополнительные Советы и Рекомендации**

1. **Используйте Инструменты Разработчика в Браузере:**
   - Инструменты разработчика (обычно открываются клавишей `F12`) позволяют отлаживать JavaScript, проверять стили CSS и анализировать структуру DOM.

2. **Практикуйтесь Регулярно:**
   - Программирование требует постоянной практики. Создавайте небольшие проекты, чтобы закрепить знания.

3. **Читайте Документацию:**
   - Ознакомьтесь с официальной документацией по HTML, CSS и JavaScript. Хорошими ресурсами являются:
      - [MDN Web Docs](https://developer.mozilla.org/ru/)
      - [W3Schools](https://www.w3schools.com/)

4. **Используйте Валидаторы:**
   - Проверяйте корректность вашего HTML и CSS с помощью [W3C Validators](https://validator.w3.org/).
   - Используйте инструменты проверки кода, такие как [ESLint](https://eslint.org/) для JavaScript.

5. **Участвуйте в Сообществах:**
   - Присоединяйтесь к форумам и сообществам разработчиков, таким как [Stack Overflow](https://stackoverflow.com/) или [Dev.to](https://dev.to/), чтобы получать помощь и делиться опытом.

6. **Следите за Безопасностью:**
   - Всегда проверяйте и обрабатывайте вводимые пользователями данные, особенно при работе с API.

7. **Оптимизируйте Код:**
   - Стремитесь к чистому и читаемому коду. Используйте комментарии для объяснения сложных частей.
