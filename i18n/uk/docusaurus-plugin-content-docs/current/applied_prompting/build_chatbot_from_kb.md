---
sidebar_position: 40
---

# 🟢 Чат-бот + База знань

import ImageIntents from '@site/docs/assets/chatbot_from_kb_intents.png'
import ImageGPT3 from '@site/docs/assets/chatbot_from_kb_gpt3.png'
import ImageGPT3Organized from '@site/docs/assets/chatbot_from_kb_gpt3_organized.png'
import ImagePrompt from '@site/docs/assets/chatbot_from_kb_prompt.png'
import ImageLogin from '@site/docs/assets/chatbot_from_kb_login.png'

Останні досягнення у великих мовних моделях (ВММ), таких як [GPT-3](https://arxiv.org/abs/2005.14165) і [ChatGPT](https://chat.openai.com/chat) викликали багато шуму в індустрії технологій. Ці моделі неймовірно потужні для створення контенту, але вони також мають деякі недоліки, такі як упередженість (@nadeem-etal-2021-stereoset) і галюцинації (@Ji_2022). Однією зі сфер, у якій ці ВММ можуть бути особливо корисними, є розробка чат-ботів.

## Чат-боти на основі намірів

Традиційні чат-боти зазвичай базуються на намірах, тобто вони розроблені, щоб реагувати на конкретні наміри користувача. Кожен намір складається з набору зразкових запитань і відповідної відповіді. Наприклад, намір "Погода" може містити питання-зразки: "Яка сьогодні погода?" або "Чи буде сьогодні дощ?" і відповідь типу "Сьогодні буде сонячно." Коли користувач ставить запитання, чат-бот порівнює його з наміром із найбільш схожими питаннями-зразками та дає відповідну відповідь.

<div style={{textAlign: 'left'}}>
  <img src={ImageIntents} style={{width: "700px"}} />
  <p style={{color: "gray", fontSize: "12px", fontStyle: "italic"}}>Як працює традиційний чат-бот на основі намірів. Зображення від автора.</p>
</div>

Однак у чат-ботів на основі намірів є свій набір проблем. Одна проблема полягає в тому, що вони вимагають великої кількості конкретних намірів, щоб дати конкретні відповіді. Наприклад, такі висловлювання користувача, як "Я не можу увійти", "Я забув свій пароль" або "Помилка входу", можуть вимагати трьох різних відповідей і, отже, трьох різних намірів, навіть якщо всі вони досить схожі.

## Чим може допомогти GPT-3

Тут GPT-3 може бути особливо корисним. Замість того, щоб мати багато дуже конкретних намірів, кожен намір може бути ширшим і використовувати документ із вашої [Бази знань](https://en.wikipedia.org/wiki/Knowledge_base). База знань (БЗ) — це інформація, що зберігається у вигляді структурованих і неструктурованих даних, готових до використання для аналізу чи висновків. Ваша БЗ може складатися з низки документів, які пояснюють, як використовувати ваші продукти.

Таким чином, кожен намір пов’язується з документом замість списку запитань і конкретної відповіді, напр. один намір для "проблем із входом", один намір для "як підписатися" тощо. Коли користувач ставить запитання щодо входу, ми можемо передати документ "проблеми входу" до GPT-3 як контекстну інформацію та створити конкретну відповідь на запитання користувача.

<div style={{textAlign: 'left'}}>
  <img src={ImageGPT3} style={{width: "700px"}} />
  <p style={{color: "gray", fontSize: "12px", fontStyle: "italic"}}>Як може працювати чат-бот, що використовує GPT-3. Зображення від автора.</p>
</div>

Цей підхід зменшує кількість намірів, якими потрібно керувати, і дозволяє отримати відповіді, які краще адаптуються до кожного запитання. Крім того, якщо документ, пов’язаний із наміром, описує різні процеси (наприклад, процес для "входу на вебсайт" та інший для "входу в мобільному додатку"), GPT-3 може автоматично запитати у користувача роз’яснення, перш ніж дати остаточну відповідь.

## Чому ми не можемо передати всю БЗ до GPT-3?

Сьогодні такі ВММ, як GPT-3, мають максимальний розмір запиту приблизно 4 тис. токенів (для моделі [`text-davinci-003`](https://beta.openai.com/docs/models/gpt-3)), що багато, але недостатньо для того, щоб помістити всю базу знань в один запит. ВММ мають максимальний розмір запиту з обчислювальних причин, оскільки генерування тексту за допомогою них передбачає ряд обчислень, які швидко зростають зі збільшенням розміру запиту.

Майбутні ВММ можуть не мати цього обмеження, але також збережуть можливості генерування тексту. Однак наразі нам потрібно розробити рішення стосовно цього.

## Як може працювати чат-бот із GPT-3

Отже, послідовність чат-бота може складатися з двох етапів:

1. По-перше, нам потрібно вибрати відповідний намір для запитання користувача, тобто нам потрібно отримати правильний документ із нашої бази знань.
2. Тоді, коли у нас є потрібний документ, ми можемо використовувати GPT-3, щоб створити відповідну відповідь для користувача. Для цього нам потрібно буде створити хороший запит.

Перший крок по суті вирішується за допомогою [семантичного пошуку](https://en.wikipedia.org/wiki/Semantic_search). Ми можемо використовувати попередньо підготовлені моделі з бібліотеки [`sentence-transformers`](https://www.sbert.net/examples/applications/semantic-search/README.html) і легко призначати бали кожному документу. Документ з найвищим балом буде використаний для створення відповіді чат-бота.

<div style={{textAlign: 'left'}}>
  <img src={ImageGPT3Organized} style={{width: "700px"}} />
  <p style={{color: "gray", fontSize: "12px", fontStyle: "italic"}}>Як може працювати чат-бот, що використовує GPT-3. GPT-3 можна використовувати для створення правильної відповіді, використовуючи інформацію з документів бази знань. Зображення від автора.</p>
</div>

## Генерування відповідей за допомогою GPT-3

Коли у нас буде потрібний документ, нам потрібно буде створити хороший запит, який буде використовуватися з GPT-3 для створення відповіді. У наступних експериментах ми завжди використовуватимемо модель `text-davinci-003` із температурою `0,7`.

Щоб створити запит, ми поекспериментуємо, використовуючи:

- [**Рольовий запит**](https://learnprompting.org/docs/basics/roles): евристична техніка, яка призначає ШІ певну роль.
- **Релевантна інформація з БЗ**, тобто документ, отриманий на етапі семантичного пошуку.
- **Останні повідомлення, якими обмінювалися користувач і чат-бот**. Це корисно для повідомлень, надісланих користувачем, у яких не вказано повний контекст. Ми побачимо приклад цього пізніше. Перегляньте [цей приклад](https://learnprompting.org/docs/applied_prompting/build_chatgpt) , щоб дізнатися, як керувати розмовами за допомогою GPT-3.
- Нарешті, **запитання користувача**.

<div style={{textAlign: 'left'}}>
  <img src={ImagePrompt} style={{width: "700px"}} />
  <p style={{color: "gray", fontSize: "12px", fontStyle: "italic"}}>Інформація, яка використовується для створення запиту GPT-3. Зображення від автора.</p>
</div>

Почнімо наш запит, використовуючи техніку <span className="yellow-highlight">рольового запиту</span>.

<pre>
    <span className="yellow-highlight">As an advanced chatbot named Skippy, your primary goal is to assist users to the best of your ability.</span>
</pre>

Тоді припустімо, що крок семантичного пошуку дістає цей документ із нашої бази знань. Усі документи описують, як працює продукт VideoGram, який є уявним продуктом, схожим на Instagram, але лише для відео.

<div style={{textAlign: 'left'}}>
  <img src={ImageLogin} style={{width: "700px"}} />
  <p style={{color: "gray", fontSize: "12px", fontStyle: "italic"}}>Документ, що пояснює, як працює вхід у VideoGram. Зображення від автора.</p>
</div>

Таким чином ми можемо додати <span className="yellow-highlight">його вміст</span> у запит.

<pre>
    As an advanced chatbot named Skippy, your primary goal is to assist users to the best of your ability.<br/><br/>

    <span className="yellow-highlight">
    START CONTEXT<br/>
    Login to VideoGram from Website<br/>
    1. Open your web browser and go to the VideoGram website.<br/>
    2. Click on the “Login” button located in the top right corner of the page.<br/>
    3. On the login page, enter your VideoGram username and password.<br/>
    4. Once you have entered your credentials, click on the “Login” button.<br/>
    5. You should now be logged in to your VideoGram account.<br/>
    <br/>
    Login to VideoGram from Mobile App<br/>
    1. Open the VideoGram app on your mobile device.<br/>
    2. On the main page, tap the “Login” button located in the bottom right corner.<br/>
    3. On the login page, enter your VideoGram username and password.<br/>
    4. Once you have entered your credentials, tap the “Login” button.<br/>
    5. You should now be logged in to your VideoGram account.<br/>
    END CONTEXT<br/>
    </span>
</pre>

Нарешті, нам потрібно додати <span className="yellow-highlight">розмову та запитання користувача</span> у кінець запиту, як у наступному прикладі.

<pre>
    As an advanced chatbot named Skippy, your primary goal is to assist users to the best of your ability.<br/>
    <br/>
    START CONTEXT<br/>
    Login to VideoGram from Website<br/>
    1. Open your web browser and go to the VideoGram website.<br/>
    2. Click on the “Login” button located in the top right corner of the page.<br/>
    3. On the login page, enter your VideoGram username and password.<br/>
    4. Once you have entered your credentials, click on the “Login” button.<br/>
    5. You should now be logged in to your VideoGram account.<br/>
    <br/>
    Login to VideoGram from Mobile App<br/>
    1. Open the VideoGram app on your mobile device.<br/>
    2. On the main page, tap the “Login” button located in the bottom right corner.<br/>
    3. On the login page, enter your VideoGram username and password.<br/>
    4. Once you have entered your credentials, tap the “Login” button.<br/>
    5. You should now be logged in to your VideoGram account.<br/>
    END CONTEXT<br/>
    <br/>
    <span className="yellow-highlight">SKIPPY: Hello, I’m Skippy! How can I help you?<br/>
    USER: I can’t find the login button.<br/>
    SKIPPY:</span><br/>
</pre>

Передаючи цей запит GPT-3, я отримав таку згенеровану відповідь.

<pre>
    <span className="bluegreen-highlight">No problem! On the website, the login button is located in the top right corner of the page. On the mobile app, the login button is located in the bottom right corner. Дайте мені знати, якщо вам потрібна додаткова допомога!</span>
</pre>

Зверніть увагу, як інформація у згенерованій відповіді надходить із документа бази знань.

## Усунення неоднозначності запитань з GPT-3

Спробуймо менш чіткий вислів користувача, наприклад <span className="yellow-highlight">"не можу ввійти"</span>. Ось повний запит.

<pre>
    As an advanced chatbot named Skippy, your primary goal is to assist users to the best of your ability.<br/>
    <br/>
    START CONTEXT<br/>
    Login to VideoGram from Website<br/>
    1. Open your web browser and go to the VideoGram website.<br/>
    2. Click on the “Login” button located in the top right corner of the page.<br/>
    3. On the login page, enter your VideoGram username and password.<br/>
    4. Once you have entered your credentials, click on the “Login” button.<br/>
    5. You should now be logged in to your VideoGram account.<br/>
    <br/>
    Login to VideoGram from Mobile App<br/>
    1. Open the VideoGram app on your mobile device.<br/>
    2. On the main page, tap the “Login” button located in the bottom right corner.<br/>
    3. On the login page, enter your VideoGram username and password.<br/>
    4. Once you have entered your credentials, tap the “Login” button.<br/>
    5. You should now be logged in to your VideoGram account.<br/>
    END CONTEXT<br/>
    <br/>
    SKIPPY: Hello, I’m Skippy! How can I help you?<br/>
    USER: <span className="yellow-highlight">Can’t login</span><br/>
    SKIPPY:<br/>
</pre>

GPT-3 відповідає, намагаючись краще зрозуміти, в чому проблема користувача.

<pre>
    <span className="bluegreen-highlight">I’m sorry to hear that. Can you tell me if you are trying to login via the VideoGram website or mobile app?</span>
</pre>

Далі, ось як відбувається повна розмова. Весь запит прихований для кращої видимості.

<pre>
    USER: Can’t login<br/>
    SKIPPY: I’m sorry to hear that. Can you tell me if you are trying to login via the VideoGram website or mobile app?<br/>
    USER: Mobile app<br/>
    <span className="bluegreen-highlight">SKIPPY: OK, no problem. To login via the mobile app, open the VideoGram app on your mobile device. On the main page, tap the “Login” button located in the bottom right corner. On the login page, enter your VideoGram username and password. Once you have entered your credentials, tap the “Login” button. You should now be logged in to your VideoGram account. Please let me know if you need any further assistance.</span>
</pre>

GPT-3 може керувати усуненням неоднозначності за умови, що він має правильну контекстну інформацію.

## Проблеми з генеруванням відповідей за допомогою GPT-3

Попередні приклади спрацювали добре. Однак є кілька випадків, в яких цей чат-бот може не впоратися.

Якщо ми запитаємо "Чи мобільний додаток безплатний?" у GPT-3, передаючи документ для входу як контекст, ви часто отримуєте відповідь на кшталт "Так, мобільний додаток VideoGram можна завантажити та використовувати безплатно", навіть якщо така інформація не міститься в контекстній інформації. Створення неправдивої інформації дуже шкідливо для чат-ботів служби підтримки клієнтів!

GPT-3 рідко генерує неправдиву інформацію, якщо відповідь на запитання користувача можна знайти в контексті. Оскільки запитання користувачів часто є короткими та неоднозначними текстами, ми не можемо покладатися на крок семантичного пошуку, щоб завжди отримати правильний документ, і тому ми завжди вразливі до створення неправдивої інформації.

## Висновок

GPT-3 дуже корисний для створення розмовних чат-ботів і здатний відповідати на ряд конкретних запитань на основі контекстної інформації, вставленої в запит. Однак важко змусити модель видавати відповіді, використовуючи лише інформацію в контексті, оскільки модель схильна до галюцинацій (тобто генерування нової інформації, потенційно неправдивої). Створення неправдивої інформації є проблемою різної серйозності залежно від випадку використання.

Автор: [Фабіо Кьюзано](https://www.linkedin.com/in/fabio-chiusano-b6a3b311b/).
