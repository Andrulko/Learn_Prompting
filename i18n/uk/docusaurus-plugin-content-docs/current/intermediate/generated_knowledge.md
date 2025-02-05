---
sidebar_position: 7
---

# 🟡 Згенеровані знання


Ідея підходу генерованих знань (@liu2021generated) полягає в тому, щоб попросити %%ВММ|LLM%% згенерувати потенційно корисну інформацію про дане питання/запит перед тим, як дати остаточну відповідь.

Наприклад, скажімо, ви хочете написати невеликий допис у блозі про якусь тварину, як-от [«Ведмідь-дух»](https://en.wikipedia.org/wiki/Kermode_bear). Перш ніж задати %%ВММ|LLM%% його написати, ви можете попросити його згенерувати деякі факти про «Ведмедя-духа». Це допоможе великій мовній моделі створити більш інформативний допис для блогу. Для цього є два простих способи.

## Одноступеневий підхід

Перший підхід передбачає, що за допомогою одного запиту ВММ має згенерувати інформацію, а потім вже написати пост.

```text
Згенеруй 4 факти про кермодського ведмедя, а потім, використовуючи цю інформацію, створіть короткий допис для блогу:
// highlight-start
Кермодський ведмідь, також відомий як ведмідь-дух, є рідкісним підвидом ведмедя північноамериканського, що поширений в прибережних районах канадської провінції Британська Колумбія. 

1. Кермодський ведмідь є унікальним підвидом ведмедя північноамериканського, приблизно 10% популяції має біле хутро. 

2. Кермодський ведмідь є символом корінних народів Британської Колумбії й вважається тотемним звіром. 

3. Кермодський ведмідь є важливою частиною екосистеми, сприяючи поширенню насіння та підтримці балансу лісу. 

4. Кермодський ведмідь є охоронюваним видом і за його популяцією пильно стежить влада провінції.

Кермодський ведмідь — рідкісна та унікальна тварина, яка мешкає в прибережних районах канадської провінції Британська Колумбія. Близько 10% популяції цього підвиду американського чорного ведмедя має біле хутро, що робить їх доволі незвичним явищем. Кермодський ведмідь є символом корінних народів Британської Колумбії й вважається тотемним звіром. Вони є важливою частиною екосистеми, сприяючи поширенню насіння та збереженню балансу в лісі. Кермодський ведмідь є охоронюваним видом і за його популяцією пильно стежить влада провінції. Це красива і велична тварина, тому важливо, щоб ми доклали зусиль для захисту і збереження цього виду.
// highlight-end
```


## Двоступеневий підхід

У цьому способі ми спочатку просимо %%ВММ|LLМ%% згенерувати факти про ведмедя:

```text
Згенеруй 10 фактів про кермодських ведмедів:
// highlight-start
1. Кермодський ведмідь, також відомий як «Ведмідь-дух», — це рідкісний підвид ведмедя північноамериканського, що водиться в канадській провінції Британська Колумбія.

2. Кермодський ведмідь має унікальне забарвлення шерсті білого чи кремового кольору, що зумовлено рецесивним геном.

3. Кермодський ведмідь є символом надії та оновлення для корінних народів Британської Колумбії.

4. Кермодський ведмідь знаходиться під охороною і занесений до списку видів, що знаходяться під особливою охороною Комітету з моніторингу диких видів, що перебувають під загрозою зникнення в Канаді.
// highlight-end
```

Потім ми використовуємо цю інформацію для написання нового запиту для допису:

```text
1. Кермодський ведмідь, також під назвою «Ведмідь-дух», — це рідкісний підвид ведмедя північноамериканського, що водиться в канадській провінції Британська Колумбія.

2. Кермодський ведмідь має унікальне забарвлення шерсті білого чи кремового кольору, що зумовлено рецесивним геном.

3. Кермодський ведмідь є символом надії та оновлення для корінних народів Британської Колумбії.

4. Кермодський ведмідь знаходиться під охороною і занесений до списку видів, що знаходяться під особливою охороною Комітету зі моніторингу диких видів, що перебувають під загрозою зникнення в Канаді.

Використовуючи наведені вище факти, створи статтю для блогу на один абзац про кермодських ведмедів:

// highlight-start

Кермодський ведмідь, також відомий під назвою «Ведмідь-дух», — це рідкісний підвид ведмедя північноамериканського, що водиться в канадській провінції Британська Колумбія. Цей унікальний ведмідь, що має шерсть білого чи кремового кольору, зумовлену рецесивним геном, є символом надії та оновлення для корінних народів Британської Колумбії. Кермодський ведмідь це вид, що охороняється та занесений до списку видів, які викликають особливе занепокоєння Комітету з моніторингу видів, що перебувають під загрозою зникнення в Канаді, що робить його важливою частиною біорізноманіття регіону.

// highlight-end
```

Рекомендуємо використовувати другий підхід, оскільки він дозволяє створювати довші обсяги адекватного тексту.

## Інший приклад використання

Підхід до генерованих знань був фактично введений для зовсім іншої задачі — відповіді на складні запитання. Нижче розглянемо питання, на яке GPT-3 відповідає неправильно: 

<iframe    src="https://embed.learnprompting.org/embed?config=eyJ0b3BQIjoxLCJ0ZW1wZXJhdHVyZSI6MCwibWF4VG9rZW5zIjo0MSwib3V0cHV0IjoiU291dGggQWZyaWNhIGlzIGxhcmdlciB0aGFuIENvbmdvLiIsInByb21wdCI6IldoaWNoIGNvdW50cnkgaXMgbGFyZ2VyLCBDb25nbyBvciBTb3V0aCBBZnJpY2E%2FIiwibW9kZWwiOiJ0ZXh0LWRhdmluY2ktMDAzIn0%3D"
    style={{width:"100%", height:"200px", border:"0", borderRadius:"4px", overflow:"hidden"}}
    sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
></iframe>

:::note
Цей приклад може бути неточним. Ми все ще працюємо над його вдосконаленням.
:::

<br/>

Якщо ми спочатку попросимо %%ВММ|LLM%% створити факти про Конґо та Південну Африку, то опісля зможемо використати цю інформацію, щоб правильно відповісти на запитання. Теоретично це схоже на %%CoT|CoT prompting%%, оскільки ми фактично змушуємо її генерувати проміжні міркування у формі пов’язаних фактів.

Розпочнімо з першого кроку — *генерації знань*. Ми можемо попросити %%ВММ|LLМ%% згенерувати факти про Конґо та Південну Африку:

<iframe    src="https://embed.learnprompting.org/embed?config=eyJ0b3BQIjoxLCJ0ZW1wZXJhdHVyZSI6MCwibWF4VG9rZW5zIjo0MSwib3V0cHV0IjoiU291dGggQWZyaWNhIGlzIHRoZSAyNXRoIGxhcmdlc3QgY291bnRyeSBpbiB0aGUgd29ybGQsIHdpdGggYW4gYXJlYSBvZiAxLDIyMSwwMzcgc3F1YXJlIGtpbG9tZXRlcnMgKDQ3MSw0NDUgc3F1YXJlIG1pbGVzKS4gQ29uZ28sIG9uIHRoZSBvdGhlciBoYW5kLCBpcyB0aGUgMTF0aCBsYXJnZXN0IGNvdW50cnkgaW4gdGhlIHdvcmxkLCB3aXRoIGFuIGFyZWEgb2YgMiwzNDQsODU4IHNxdWFyZSBraWxvbWV0ZXJzICg5MDUsNTY3IHNxdWFyZSBtaWxlcykuIFNvdXRoIEFmcmljYSBpcyBhbG1vc3QgaGFsZiB0aGUgc2l6ZSBvZiBDb25nbywgd2l0aCBhIHBvcHVsYXRpb24gb2YgNTcuNyBtaWxsaW9uIGNvbXBhcmVkIHRvIENvbmdvJ3MgcG9wdWxhdGlvbiBvZiA4NC4zIG1pbGxpb24uIFNvdXRoIEFmcmljYSBpcyB0aGUgbW9zdCBwb3B1bG91cyBjb3VudHJ5IGluIHRoZSByZWdpb24sIHdoaWxlIENvbmdvIGlzIHRoZSBzZWNvbmQgbW9zdCBwb3B1bG91cy4iLCJwcm9tcHQiOiJHZW5lcmF0ZSBzb21lIGtub3dsZWRnZSBhYm91dCB0aGUgc2l6ZXMgb2YgU291dGggQWZyaWNhIGFuZCBDb25nbzoiLCJtb2RlbCI6InRleHQtZGF2aW5jaS0wMDMifQ%3D%3D"
    style={{width:"100%", height:"500px", border:"0", borderRadius:"4px", overflow:"hidden"}}
    sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
></iframe>

<br/>

Далі використаймо ці знання, щоб правильно відповісти на запитання. Це *крок інтеграції* знань!

<iframe    src="https://embed.learnprompting.org/embed?config=eyJ0b3BQIjoxLCJ0ZW1wZXJhdHVyZSI6MCwibWF4VG9rZW5zIjo0MSwib3V0cHV0IjoiQ29uZ28gaXMgbGFyZ2VyIHRoYW4gU291dGggQWZyaWNhLlxuIiwicHJvbXB0IjoiU291dGggQWZyaWNhIGlzIHRoZSAyNXRoIGxhcmdlc3QgY291bnRyeSBpbiB0aGUgd29ybGQsIHdpdGggYW4gYXJlYSBvZiAxLDIyMSwwMzcgc3F1YXJlIGtpbG9tZXRlcnMgKDQ3MSw0NDUgc3F1YXJlIG1pbGVzKS4gQ29uZ28sIG9uIHRoZSBvdGhlciBoYW5kLCBpcyB0aGUgMTF0aCBsYXJnZXN0IGNvdW50cnkgaW4gdGhlIHdvcmxkLCB3aXRoIGFuIGFyZWEgb2YgMiwzNDQsODU4IHNxdWFyZSBraWxvbWV0ZXJzICg5MDUsNTY3IHNxdWFyZSBtaWxlcykuIFNvdXRoIEFmcmljYSBpcyBhbG1vc3QgaGFsZiB0aGUgc2l6ZSBvZiBDb25nbywgd2l0aCBhIHBvcHVsYXRpb24gb2YgNTcuNyBtaWxsaW9uIGNvbXBhcmVkIHRvIENvbmdvJ3MgcG9wdWxhdGlvbiBvZiA4NC4zIG1pbGxpb24uIFNvdXRoIEFmcmljYSBpcyB0aGUgbW9zdCBwb3B1bG91cyBjb3VudHJ5IGluIHRoZSByZWdpb24sIHdoaWxlIENvbmdvIGlzIHRoZSBzZWNvbmQgbW9zdCBwb3B1bG91cy5cblxuV2hpY2ggY291bnRyeSBpcyBsYXJnZXIsIENvbmdvIG9yIFNvdXRoIEFmcmljYT8iLCJtb2RlbCI6InRleHQtZGF2aW5jaS0wMDMifQ%3D%3D"
    style={{width:"100%", height:"500px", border:"0", borderRadius:"4px", overflow:"hidden"}}
    sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
></iframe>

## Обговорення більш технічних аспектів

Хоча наведений вище приклад використання був схожий на те, як спочатку впроваджувалися згенеровані знання, це не зовсім те саме. Наведений нижче вміст охоплює більш технічний аспект, у якому було представлено підхід. Він дотримується двох проміжних кроків (генерування знань та інтеграція знань), які ми бачили вище.

import KGImage from '@site/docs/assets/intermediate/knowledge_generation.png';

<div style={{textAlign: 'center'}}>
  <img src={KGImage} style={{width: "750px"}} />
</div>

<div style={{textAlign: 'center'}}>
Згенеровані знання (Liu та ін.)
</div>

### Генерування знань

На етапі генерування знань %%ВММ|LLM%% просять згенерувати набір фактів про **питання**. ВМM запитується за кілька підходів, як показано нижче. M різних завершень генеруються за допомогою одного і того ж запиту (подібно до підходу самоузгодженості).

import KGP1Image from '@site/docs/assets/intermediate/gen_k_p1.png';

<div style={{textAlign: 'center'}}>
  <img src={KGP1Image} style={{width: "500px"}} />
</div>

<div style={{textAlign: 'center'}}>
Приклад генерованих знань (Лю та ін.)
</div>

### Інтеграція знань

Далі ми створюємо запитання з розширеним знанням і створюємо запит для %%ВММ|LLM%% разом з ними, щоб отримати остаточні відповіді. Найпростіший спосіб розібратися в цьому — розглянути на прикладі.

Припустімо, що ми намагаємося відповісти на **запитання** "Більшість кенгуру мають <mask\> кінцівки". Вважаймо, що на кроці генерації знань ми згенерували 2 знання (M=2):

- Знання 1: `Кенгуру — це сумчасті тварини, які мешкають в Австралії.`

- Знання 2: `Кенгуру — це сумчасті тварини, які мають 5 кінцівок.`

Тепер ми об’єднуємо кожне знання із запитанням, щоб створити запитання з розширеними знаннями:

- Запитання 1 із розширенням знань: `Більшість кенгуру мають <mask\> кінцівки. Кенгуру — це сумчасті тварини, які мешкають в Австралії.`

- Запитання 2 із розширенням знань: `Більшість кенгуру мають <mask\> кінцівки. Кенгуру — це сумчасті тварини, які мають 5 кінцівок.`

Потім ми ставимо ВММ ці запитання з розширеними знаннями й отримуємо остаточні пропозиції щодо відповідей:

- Відповідь 1: `4`

- Відповідь 2: `5`

Ми обираємо відповідь з найбільшою ймовірністю як остаточну. Найвищою ймовірністю може бути максимальна ймовірність токену відповіді або логарифмічна ймовірність токену(ів) відповіді.

## Моделі мови, доповнені декламацією

Підхід із доповненим декламуванням (@sun2022recitationaugmented) схожий на згенероване знання (майже те саме). Однак є набагато легшим, ніж формальне впровадження згенерованих знань.


import RImage from '@site/docs/assets/intermediate/recitation.png';

<div style={{textAlign: 'center'}}>
  <img src={RImage} style={{width: "250px"}} />
</div>

Ідея полягає в тому, щоб кількома кроками спонукати ВМM згенерувати інформацію *і* та відповідь у *цьому ж* кроці. Те, що він відтворює/генерує знання і відповідає на питання на одному кроці, є головною відмінністю від підходу, заснованого на згенерованому знанні.

Повторюємо, що цей підхід підказує модель з кількома прикладами (запитання, цитування, відповідь), а потім ставить запитання. Автори зазначають, що цей підхід можна поєднати з самоузгодженістю або кількома шляхами доповнення.



## Примітки

- Підхід генерованих знань демонструє покращення в різних розумних наборах даних.

- Знання, що відповідають обраній відповіді, називаються _обраним знанням_.

- Фактично, ви можете взяти відповідь, яка найчастіше зустрічається, як остаточну.