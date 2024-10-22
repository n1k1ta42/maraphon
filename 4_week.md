## **Четвёртая Неделя: Углубление в JavaScript и Основы Работы с API**

### **1. JavaScript: Асинхронные Операции и Работа с API**

#### **1.1. Асинхронные Операции**

Асинхронные операции позволяют выполнять задачи без блокировки основного потока выполнения, что особенно важно для операций ввода-вывода, таких как запросы к серверу или задержки.

**1.1.1. `setTimeout` и `setInterval`**

- **`setTimeout`**: Выполняет функцию один раз после указанной задержки в миллисекундах.

  ```javascript
  setTimeout(() => {
      console.log("Прошло 3 секунды");
  }, 3000);
  ```

- **`setInterval`**: Повторяет выполнение функции через каждые указанные миллисекунды.

  ```javascript
  setInterval(() => {
      console.log("Прошло еще 2 секунды");
  }, 2000);
  ```

**1.1.2. Промисы (Promises)**

Промисы представляют результат асинхронной операции. Они могут быть в одном из состояний:
- **Pending (Ожидание)**
- **Fulfilled (Выполнено)**
- **Rejected (Отклонено)**

**Пример использования промиса:**

```javascript
const fetchData = new Promise((resolve, reject) => {
    const success = true;

    if (success) {
        resolve("Данные успешно получены.");
    } else {
        reject("Произошла ошибка при получении данных.");
    }
});

fetchData
    .then((message) => {
        console.log(message);
    })
    .catch((error) => {
        console.error(error);
    });
```

#### **1.2. Работа с API: `fetch` и JSON**

**1.2.1. Что такое API?**
API (Application Programming Interface) — это интерфейс, позволяющий программам взаимодействовать друг с другом. Веб-API предоставляют доступ к сервисам через HTTP-запросы.

**1.2.2. Использование `fetch`**

`fetch` — современный метод для выполнения HTTP-запросов.

**Пример: Получение данных из API JSONPlaceholder**

```javascript
fetch('https://jsonplaceholder.typicode.com/posts/1')
    .then(response => response.json())
    .then(data => {
        console.log(data);
    })
    .catch(error => {
        console.error("Ошибка:", error);
    });
```

**Пояснения:**
- **`fetch(URL)`**: Отправляет GET-запрос по указанному URL.
- **`response.json()`**: Преобразует ответ в формат JSON.
- **`then`**: Обработчик успешного выполнения запроса.
- **`catch`**: Обработчик ошибок.

**1.2.3. Основы Работы с JSON**

JSON (JavaScript Object Notation) — формат обмена данными, широко используемый в веб-приложениях.

- **Преобразование JSON в объект:**
  ```javascript
  const jsonString = '{"name": "Анна", "age": 25}';
  const obj = JSON.parse(jsonString);
  console.log(obj.name); // Анна
  ```

- **Преобразование объекта в JSON:**
  ```javascript
  const person = { name: "Иван", age: 30 };
  const json = JSON.stringify(person);
  console.log(json); // {"name":"Иван","age":30}
  ```

### **2. Практическое Задание: Веб-Страница "Погода в Вашем Городе"**

Создайте веб-страницу, которая позволяет пользователю ввести название города и получить текущий прогноз погоды, используя API OpenWeatherMap.

#### **Шаг 1: Регистрация и Получение API-ключа**

1. Перейдите на [OpenWeatherMap](https://openweathermap.org/) и зарегистрируйтесь.
2. После регистрации получите API-ключ (API Key), необходимый для доступа к сервису погоды.

#### **Шаг 2: Создание HTML-Структуры**

**HTML:**

```html
<section>
    <h2>Погода в Вашем Городе</h2>
    <form id="weather-form">
        <input type="text" id="city-input" placeholder="Введите название города" required>
        <button type="submit">Получить Погоду</button>
    </form>
    <div id="weather-result">
        <!-- Результаты погоды будут отображаться здесь -->
    </div>
</section>
```

#### **Шаг 3: Стилизация с помощью CSS**

**CSS:**

```css
#weather-form {
    display: flex;
    justify-content: center;
    margin-bottom: 20px;
}

#city-input {
    width: 60%;
    padding: 10px;
    border: 2px solid #bdc3c7;
    border-radius: 4px 0 0 4px;
    font-size: 1em;
}

#weather-form button {
    padding: 10px 20px;
    border: 2px solid #bdc3c7;
    border-left: none;
    background-color: #3498db;
    color: #ffffff;
    cursor: pointer;
    border-radius: 0 4px 4px 0;
}

#weather-form button:hover {
    background-color: #2980b9;
}

#weather-result {
    max-width: 500px;
    margin: 0 auto;
    padding: 20px;
    background-color: #ecf0f1;
    border-radius: 8px;
    text-align: center;
    display: none; /* Скрыто по умолчанию */
}

#weather-result.active {
    display: block;
}

.weather-icon {
    width: 100px;
    height: 100px;
}
```

#### **Шаг 4: Добавление Функционала с помощью JavaScript**

**JavaScript (`script.js`):**

```javascript
const weatherForm = document.getElementById('weather-form');
const cityInput = document.getElementById('city-input');
const weatherResult = document.getElementById('weather-result');

// Ваш API-ключ OpenWeatherMap
const apiKey = 'ВАШ_API_КЛЮЧ';

weatherForm.addEventListener('submit', function(event) {
    event.preventDefault(); // Предотвращает перезагрузку страницы

    const city = cityInput.value.trim();

    if (city !== "") {
        getWeather(city);
        cityInput.value = ""; // Очищает поле ввода
    }
});

// Функция для получения данных о погоде
function getWeather(city) {
    // URL API с параметрами
    const url = `https://api.openweathermap.org/data/2.5/weather?q=${encodeURIComponent(city)}&appid=${apiKey}&units=metric&lang=ru`;

    fetch(url)
        .then(response => {
            if (!response.ok) {
                throw new Error("Город не найден");
            }
            return response.json();
        })
        .then(data => {
            displayWeather(data);
        })
        .catch(error => {
            displayError(error.message);
        });
}

// Функция для отображения данных о погоде
function displayWeather(data) {
    const cityName = data.name;
    const temperature = data.main.temp;
    const description = data.weather[0].description;
    const icon = `https://openweathermap.org/img/wn/${data.weather[0].icon}@2x.png`;

    weatherResult.innerHTML = `
        <h3>${cityName}</h3>
        <img src="${icon}" alt="${description}" class="weather-icon">
        <p>Температура: ${temperature}°C</p>
        <p>Описание: ${description}</p>
    `;
    weatherResult.classList.add('active');
}

// Функция для отображения ошибок
function displayError(message) {
    weatherResult.innerHTML = `<p style="color: red;">${message}</p>`;
    weatherResult.classList.add('active');
}
```

**Пояснения:**
- **`apiKey`**: Замените `'ВАШ_API_КЛЮЧ'` на ваш реальный API-ключ из OpenWeatherMap.
- **Функция `getWeather`**: Выполняет запрос к API с указанным городом, обрабатывает ответ и вызывает `displayWeather` при успехе или `displayError` при ошибке.
- **Функции `displayWeather` и `displayError`**: Отображают полученные данные или сообщение об ошибке на странице.

#### **Шаг 5: Тестирование Функционала**

1. **Ввод корректного названия города:**
    - Введите существующий город (например, "Москва") и нажмите "Получить Погоду".
    - Убедитесь, что отображаются название города, температура, описание погоды и иконка.

2. **Ввод некорректного названия города:**
    - Введите несуществующий город (например, "НетГорода") и нажмите "Получить Погоду".
    - Убедитесь, что отображается сообщение об ошибке.

3. **Валидация:**
    - Попробуйте отправить форму с пустым полем ввода. Убедитесь, что форма не отправляется.

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
