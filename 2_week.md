## **Вторая Неделя: Расширение Знаний HTML и CSS**

### **1. HTML: Формы и Таблицы**

#### **1.1. Формы и Элементы Форм**

Формы позволяют пользователям вводить и отправлять данные на сервер. В HTML формы создаются с помощью тега `<form>`, который может содержать различные элементы ввода.

**Основные Элементы Форм:**

1. **`<form>`**: Контейнер для элементов формы.
    - **Атрибуты:**
        - `action`: URL, куда будут отправлены данные формы.
        - `method`: Метод отправки данных (`GET` или `POST`).

2. **`<input>`**: Универсальный элемент для различных типов ввода.
    - **Типы:** `text`, `email`, `password`, `submit`, `button` и др.
    - **Атрибуты:** `type`, `name`, `placeholder`, `value`.

3. **`<textarea>`**: Многострочное текстовое поле.
    - **Атрибуты:** `name`, `rows`, `cols`, `placeholder`.

4. **`<button>`**: Кнопка для отправки или выполнения действий.
    - **Типы:** `submit`, `button`, `reset`.

5. **`<select>` и `<option>`**: Выпадающие списки.
    - **`<select>`** содержит несколько элементов `<option>`, представляющих варианты выбора.

**Пример Формы Обратной Связи:**

```html
<form action="/submit-form" method="POST">
    <label for="name">Имя:</label>
    <input type="text" id="name" name="user_name" placeholder="Введите ваше имя" required>

    <label for="email">Email:</label>
    <input type="email" id="email" name="user_email" placeholder="Введите ваш Email" required>

    <label for="message">Сообщение:</label>
    <textarea id="message" name="user_message" rows="5" placeholder="Введите ваше сообщение" required></textarea>

    <button type="submit">Отправить</button>
</form>
```

**Пояснения:**
- **`<label>`**: Связывает метку с элементом формы через атрибут `for`.
- **`required`**: Делает поле обязательным для заполнения.

#### **1.2. Таблицы**

Таблицы используются для представления структурированных данных в виде строк и столбцов.

**Структура Таблицы:**

1. **`<table>`**: Контейнер для таблицы.
2. **`<thead>`**: Заголовочная часть таблицы.
3. **`<tbody>`**: Основное содержимое таблицы.
4. **`<tr>`**: Строка таблицы.
5. **`<th>`**: Ячейка заголовка.
6. **`<td>`**: Стандартная ячейка таблицы.

**Пример Таблицы Любимых Книг:**

```html
<table>
    <thead>
        <tr>
            <th>Название</th>
            <th>Автор</th>
            <th>Год</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Война и Мир</td>
            <td>Лев Толстой</td>
            <td>1869</td>
        </tr>
        <tr>
            <td>Преступление и наказание</td>
            <td>Фёдор Достоевский</td>
            <td>1866</td>
        </tr>
        <tr>
            <td>Мастер и Маргарита</td>
            <td>Михаил Булгаков</td>
            <td>1967</td>
        </tr>
    </tbody>
</table>
```

**Пояснения:**
- **`<thead>`** содержит заголовки столбцов.
- **`<tbody>`** содержит строки с данными.
- **Строки `<tr>`** внутри `<thead>` обычно содержат элементы `<th>`, а внутри `<tbody>` — `<td>`.

### **2. CSS: Псевдоклассы, Псевдоэлементы и Flexbox**

#### **2.1. Псевдоклассы и Псевдоэлементы**

**Псевдоклассы (`:pseudo-class`)** позволяют применять стили к элементам в определенных состояниях.

- **`:hover`**: Стили при наведении курсора.

  ```css
  a:hover {
      color: #e74c3c;
  }
  ```

- **`:focus`**: Стили при фокусе на элементе (например, при клике на поле ввода).

  ```css
  input:focus {
      border-color: #3498db;
  }
  ```

**Псевдоэлементы (`::pseudo-element`)** позволяют вставлять контент до или после содержимого элемента.

- **`::before` и `::after`**: Используются для добавления декоративного контента.

  ```css
  .highlight::before {
      content: "★ ";
      color: gold;
  }

  .highlight::after {
      content: " ★";
      color: gold;
  }
  ```

#### **2.2. Flexbox: Гибкое Расположение Элементов**

Flexbox — это макетный модуль CSS, который позволяет легко выравнивать и распределять пространство между элементами в контейнере даже при изменении размеров экрана.

**Основные Свойства Контейнера Flex:**

- `display: flex;` — делает элемент контейнером flex.
- `flex-direction` — направление оси (row, column, row-reverse, column-reverse).
- `justify-content` — выравнивание по главной оси (flex-start, flex-end, center, space-between, space-around).
- `align-items` — выравнивание по поперечной оси (flex-start, flex-end, center, baseline, stretch).

**Пример Использования Flexbox:**

```css
.container {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
}

.item {
    background-color: #ecf0f1;
    padding: 20px;
    margin: 10px;
    border: 1px solid #bdc3c7;
    border-radius: 5px;
}
```

**HTML:**
```html
<div class="container">
    <div class="item">Элемент 1</div>
    <div class="item">Элемент 2</div>
    <div class="item">Элемент 3</div>
</div>
```

**Пояснения:**
- **`.container`** становится flex-контейнером, элементы `.item` — flex-элементами.
- **`justify-content: space-between;`** распределяет пространство между элементами.
- **`align-items: center;`** выравнивает элементы по центру по вертикали.

#### **2.3. Адаптивная Верстка: Медиа-Запросы**

Медиа-запросы позволяют изменять стили в зависимости от характеристик устройства, таких как размер экрана.

**Пример Медиа-Запроса для Мобильных Устройств:**

```css
@media (max-width: 600px) {
    .container {
        flex-direction: column;
        align-items: stretch;
    }

    .item {
        margin: 10px 0;
    }
}
```

**Пояснения:**
- Когда ширина экрана менее или равна 600px, `.container` меняет направление Flexbox с `row` на `column`, а элементы `.item` растягиваются по ширине контейнера.
- Изменяются отступы между элементами для лучшего отображения на узких экранах.

### **3. Практическое Задание: Создание Формы Обратной Связи и Таблицы**

#### **Шаг 1: Создание Формы Обратной Связи**

Добавьте форму обратной связи на вашу веб-страницу.

**HTML:**

```html
<section>
    <h2>Форма Обратной Связи</h2>
    <form id="feedback-form">
        <label for="fname">Имя:</label>
        <input type="text" id="fname" name="firstname" placeholder="Ваше имя" required>

        <label for="email">Email:</label>
        <input type="email" id="email" name="email" placeholder="Ваш Email" required>

        <label for="message">Сообщение:</label>
        <textarea id="message" name="message" rows="5" placeholder="Ваше сообщение" required></textarea>

        <button type="submit">Отправить</button>
    </form>
</section>
```

**CSS:**

```css
form {
    display: flex;
    flex-direction: column;
    max-width: 400px;
    margin: 0 auto;
}

label {
    margin-top: 10px;
    margin-bottom: 5px;
    font-weight: bold;
}

input, textarea {
    padding: 8px;
    border: 1px solid #bdc3c7;
    border-radius: 4px;
}

input:focus, textarea:focus {
    border-color: #3498db;
    outline: none;
}

button {
    margin-top: 15px;
    padding: 10px;
    background-color: #2980b9;
    color: #ffffff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background-color: #3498db;
}
```

#### **Шаг 2: Создание Таблицы Любимых Фильмов**

Добавьте таблицу с вашими любимыми фильмами.

**HTML:**

```html
<section>
    <h2>Мои Любимые Фильмы</h2>
    <table>
        <thead>
            <tr>
                <th>Название</th>
                <th>Режиссёр</th>
                <th>Год</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Интерстеллар</td>
                <td>Кристофер Нолан</td>
                <td>2014</td>
            </tr>
            <tr>
                <td>Начало</td>
                <td>Кристофер Нолан</td>
                <td>2010</td>
            </tr>
            <tr>
                <td>Матрица</td>
                <td>Лана и Лилли Вачовски</td>
                <td>1999</td>
            </tr>
        </tbody>
    </table>
</section>
```

**CSS:**

```css
table {
    width: 80%;
    margin: 20px auto;
    border-collapse: collapse;
}

th, td {
    border: 1px solid #bdc3c7;
    padding: 10px;
    text-align: left;
}

th {
    background-color: #ecf0f1;
}

tr:nth-child(even) {
    background-color: #f9f9f9;
}

tr:hover {
    background-color: #dcdde1;
}
```

**Пояснения:**
- **`border-collapse: collapse;`**: Убирает двойные границы между ячейками.
- **`tr:nth-child(even)`**: Добавляет полосатость таблице для улучшения читаемости.
- **`tr:hover`**: Изменяет цвет строки при наведении курсора.


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
