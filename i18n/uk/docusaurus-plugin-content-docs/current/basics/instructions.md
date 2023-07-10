---
sidebar_position: 2
---

# 🟢 Надання інструкцій

import InstructionPrompt from '@site/docs/assets/instruction_prompt.svg';

<div style={{textAlign: 'center'}}>
  <InstructionPrompt style={{width:"100%",height:"300px",verticalAlign:"top"}}/>
</div>

Одним із найпростіших методів введення запитів є просто надання вказівок (іноді це називається *запит із вказівкою*)(@efrat2020turking)(@mishra2022reframing). Ми вже бачили просту інструкцію в попередньому розділі (`Переконайтеся, що ваша відповідь правильна. Що таке 965*590? Переконайтеся, що ваша відповідь правильна:`). Однак сучасні ШІ можуть виконувати набагато складніші вказівки.

Нижче наведено наш перший [приклад](https://learnprompting.org/docs/basics/intro#embeds). Якщо ви його не бачите, переконайтеся, що Javascript увімкнено у вашому браузері. Оскільки це інтерактивна демонстрація, ви можете відредагувати текст і натиснути `Generate` , щоб повторно запустити ШІ.

#### Приклад 1 <iframe
    src="https://embed.learnprompting.org/embed?config=eyJ0b3BQIjowLCJ0ZW1wZXJhdHVyZSI6MCwibWF4VG9rZW5zIjoyNTYsIm91dHB1dCI6IkRvZSwgSm9obiIsInByb21wdCI6IkEgdXNlciBoYXMgaW5wdXQgdGhlaXIgZmlyc3QgYW5kIGxhc3QgbmFtZSBpbnRvIGEgZm9ybS4gV2UgZG9uJ3Qga25vdyBpbiB3aGljaCBvcmRlciBcbnRoZWlyIGZpcnN0L2xhc3QgbmFtZSBpcywgYnV0IHdlIG5lZWQgaXQgdG8gYmUgaW4gdGhlIGZvcm1hdCAnTGFzdCwgRmlyc3QnLiBDb252ZXJ0IHRoZSBmb2xsb3dpbmc6XG5cbmpvaG4gZG9lIiwibW9kZWwiOiJ0ZXh0LWRhdmluY2ktMDAzIn0%3D"
    style={{width:"100%", height:"350px", border:"0", borderRadius:"4px", overflow:"hidden"}}
    sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
></iframe>

<br/>ШІ легко вирішує це завдання. Ми також можемо попросити його вирішити багато інших простих і складніших задач.

#### Приклад 2

Ось складніший приклад[^A]:

```
Прочитайте наведений нижче електронний лист про продажі. Видаліть будь-яку особисту інформацію (PII),
і замініть її відповідним заповнювачем. Наприклад, замініть ім'я "Джон Доу"
на "[NAME]".

Вітаю, Джоне,

Я пишу тобі, оскільки я помітив, що ти нещодавно придбав новий автомобіль. Я продавець
у місцевому дилерському центрі (Cheap Dealz), і хочу повідомити вам, що у нас є чудова пропозиція на новий
автомобіль. Якщо тебе це зацікавило, будь ласка, дай мені знати.

Дякуємо,

Джиммі Сміт

Телефон: 410-805-2345
Електронна адреса: jimmysmith@cheapdealz.com
```

Ось відповідь [ШІ](https://beta.openai.com/playground/p/002o3gmji5jlwUfRq9d7KDHc?model=text-davinci-003):

```text
// highlight-start
Привіт [NAME],

Я пишу тобі, тому що я помітив, що ти нещодавно купив новий автомобіль. Я продавець
у місцевому дилерському центрі ([DEALERSHIP]), і хочу повідомити тобі, що у нас чудова пропозиція на новий 
автомобіль. Якщо тебе це зацікавило, будь ласка, дай мені знати.

Дякую,

[SALESPERSON]

Телефон: [НОМЕР ТЕЛЕФОНУ]
Електронна адреса: [EMAIL ADDRESS]
// highlight-end
```

Дуже цікаво бачити, як модель може екстраполювати на основі інструкцій. Наприклад, вона знає, що потрібно замінити `Cheap Dealz` на `[DEALERSHIP]` і `Jimmy Smith` на `[SALESPERSON]`, навіть якщо ми прямо не сказали йому це зробити.

[^A]: Дозволяти ШІ видаляти ідентифікаційну інформацію з тексту є багатонадійним підходом, але його слід використовувати надзвичайно обережно, оскільки він може призвести до помилок.


