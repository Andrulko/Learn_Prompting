---
sidebar_position: 99
---

# 🟢 Midjourney

[Midjourney](https://www.midjourney.com) – це генератор зображень на основі ШІ, який працює через інтерфейс бота в Discord або вебдодаток (планується також API-версія Midjourney). Процес створення зображень за допомогою Midjourney дотримується тих самих основних принципів, що й інші генератори зображень на основі ШІ, включно з використанням запитів для керування процесом створення.

Однією з унікальних характеристик Midjourney у порівнянні з іншими генераторами зображень на основі ШІ є його здатність створювати візуально виняткові зображення високого рівня художності. Це пояснюється спеціальним навчанням моделі, яке дає їй змогу створювати високоякісні зображення з конкретними художніми параметрами (докладніше про це в розділі «Розширені запити» > «Параметри»).

Ви можете експериментувати з ботом Midjourney на сервері [Learn Prompting у Discord](http://learnprompting.org/discord) або на [офіційному Discord-сервері Midjourney](https://discord.gg/midjourney).

import midjourney_astronaut from '@site/docs/assets/images_chapter/midjourney_astronaut.png';
import midjourney_astronaut_params from '@site/docs/assets/images_chapter/midjourney_astronaut_params.png';
import midjourney_astronaut_multi1 from '@site/docs/assets/images_chapter/midjourney_astronaut_multi1.png';
import midjourney_astronaut_multi2 from '@site/docs/assets/images_chapter/midjourney_astronaut_multi2.png';
import midjourney_astronaut_ip2 from '@site/docs/assets/images_chapter/midjourney_astronaut_ip2.png';

import midjourney_astronaut_params_a12 from '@site/docs/assets/images_chapter/midjourney_astronaut_params_a12.png';
import midjourney_astronaut_params_a169 from '@site/docs/assets/images_chapter/midjourney_astronaut_params_a169.png';

import midjourney_astronaut_params_c20 from '@site/docs/assets/images_chapter/midjourney_astronaut_params_c20.png';
import midjourney_astronaut_params_c80 from '@site/docs/assets/images_chapter/midjourney_astronaut_params_c80.png';

import midjourney_astronaut_params_q05 from '@site/docs/assets/images_chapter/midjourney_astronaut_params_q05.png';
import midjourney_astronaut_params_q2 from '@site/docs/assets/images_chapter/midjourney_astronaut_params_q2.png';

import midjourney_astronaut_params_s50 from '@site/docs/assets/images_chapter/midjourney_astronaut_params_s50.png';
import midjourney_astronaut_params_s900 from '@site/docs/assets/images_chapter/midjourney_astronaut_params_s900.png';

import midjourney_astronaut_params_sameseed from '@site/docs/assets/images_chapter/midjourney_astronaut_params_sameseed.png';
import midjourney_astronaut_params_seed123 from '@site/docs/assets/images_chapter/midjourney_astronaut_params_seed123.png';

import midjourney_astronaut_params_tile from '@site/docs/assets/images_chapter/midjourney_astronaut_params_tile.png';
import midjourney_astronaut_params_tilegrid from '@site/docs/assets/images_chapter/midjourney_astronaut_params_tilegrid.png';
import midjourney_astronaut_params_tilecomplete from '@site/docs/assets/images_chapter/midjourney_astronaut_params_tilecomplete.jpeg';

import midjourney_astronaut_params_v1 from '@site/docs/assets/images_chapter/midjourney_astronaut_params_v1.png';
import midjourney_astronaut_params_v2 from '@site/docs/assets/images_chapter/midjourney_astronaut_params_v2.png';
import midjourney_astronaut_params_v3 from '@site/docs/assets/images_chapter/midjourney_astronaut_params_v3.png';



# Базове застосування

Основна анатомія запитів у Midjourney — `/imagine prompt: [ЗАПИТ ДЛЯ ЗОБРАЖЕННЯ] [--НЕОБОВ’ЯЗКОВІ ПАРАМЕТРИ]`.

Наприклад: `/imagine prompt: космонавт на коні`

<div style={{textAlign: 'center'}}>
  <img src={midjourney_astronaut} style={{width: "350px"}} />
</div>

Приклад із параметрами: `/imagine prompt: космонавт на коні --ar 3:2 --c 70 --q 2 --seed 1000`

<div style={{textAlign: 'center'}}>
  <img src={midjourney_astronaut_params} style={{width: "350px"}} />
</div>

У цьому базовому прикладі були використані такі параметри:


`--ar 3:2` встановлює співвідношення сторін зображення як 3:2;

`--c 70` додає значення невизначеності 70, щоб дозволити Midjourney вільніше інтерпретувати запит (діапазон значень невизначеності: 0–100);

`--seed 100` встановлює довільне початкове значення, яке можна використати для повторного рендерингу або перероблення зображення пізніше.


(дізнайтеся більше про параметри Midjourney у розділі «Розширені запити» > «Параметри»)


# Розширені запити
Розширені запити в Midjourney використовують параметри та спеціальні методи запитів, які підтримуються алгоритмом Midjourney.

## Мультизапити
За замовчуванням Midjourney інтерпретує ваш запит комплексно. Використання подвійної двокрапки `::` наказує Midjourney інтерпретувати кожну частину запиту окремо.

Приклад:

```text
/imagine prompt: космонавт і кінь
```

<div style={{textAlign: 'center'}}>
  <img src={midjourney_astronaut_multi1} style={{width: "350px"}} />
</div>

```text
/imagine prompt: космонавт:: і кінь
```

<div style={{textAlign: 'center'}}>
  <img src={midjourney_astronaut_multi2} style={{width: "350px"}} />
</div>

## Запити-зображення
Завантаживши зображення в Discord і використовуючи його URL-адресу в запиті, ви можете дати вказівку Midjourney використовувати це зображення для впливу на вміст, стиль і композицію ваших результатів. Приклад: [Космонавт (Джерело: Вікіпедія)](https://en.wikipedia.org/wiki/Astronaut#/media/File:STS41B-35-1613_-_Bruce_McCandless_II_during_EVA_(Retouched).jpg)

```text
/imagine prompt: [URL-адреса зображення], імпресіоністський живопис
```

<div style={{textAlign: 'center'}}>
  <img src={midjourney_astronaut_ip2} style={{width: "350px"}} />
</div>

## Параметри (v4)

Наступні параметри підтримуються останньою моделлю Midjourney (v4).

### Співвідношення сторін:

`--ar [ratio]` змінює співвідношення за замовчуванням (1:1) до нового співвідношення (наразі максимальне підтримуване співвідношення становить 2:1)

Приклад: `космонавт на коні --ar 16:9` і `космонавт на коні --ar 1:2`

<div style={{textAlign: 'center'}}>
  <img src={midjourney_astronaut_params_a169} style={{width: "350px"}} />
  &nbsp;
   <img src={midjourney_astronaut_params_a12} style={{width: "175px"}} />
</div>

### Значення невизначеності:

`--c [value]` встановлює значення невизначеності, яке визначає, наскільки Midjourney змінює запит; що вище значення невизначеності, то більш незвичні та несподівані результати та композиції (діапазон: 0–100)

Приклад: `космонавт на коні --c20` і `космонавт на коні --c 80`

<div style={{textAlign: 'center'}}>
  <img src={midjourney_astronaut_params_c20} style={{width: "350px"}} />
  &nbsp;
   <img src={midjourney_astronaut_params_c80} style={{width: "350px"}} />
</div>

### Якість:

`--q [value]` визначає, скільки часу буде витрачено на створення зображення, таким чином підвищуючи якість. Значення за замовчуванням — «1». Вищі значення використовують більше GPU-хвилин вашої підписки (допускаються значення «.25», «.5», «1» і «2»)

Приклад: `космонавт на коні --q .5` і `космонавт на коні --q 2`

<div style={{textAlign: 'center'}}>
  <img src={midjourney_astronaut_params_q05} style={{width: "350px"}} />
  &nbsp;
   <img src={midjourney_astronaut_params_q2} style={{width: "350px"}} />
</div>

### Початкове значення:

`--seed [value]` встановлює початковий номер, який визначає початкову точку (шумове поле) для створення зображення. Початкові значення для кожного зображення генеруються випадковим чином, якщо не вказано параметр початкового значення. Використання того самого початкового значення та запиту створить подібні зображення.

Приклад: `космонавт на коні --seed 123`

<div style={{textAlign: 'center'}}>
  <img src={midjourney_astronaut_params_seed123} style={{width: "350px"}} />
  &nbsp;
   <img src={midjourney_astronaut_params_seed123} style={{width: "350px"}} />
</div>

### Стилізація:

`--stylize [value]` або `--s [value]` впливає на те, наскільки сильно Midjourney застосовує свій художній алгоритм.  Низькі значення створюють зображення, які точно відповідають запиту, високі значення створюють дуже художні зображення, які менше пов’язані з запитом. Значення за замовчуванням – 100, діапазон значень 0–1000. (Примітка: ви можете скористатися командою `/settings`, щоб змінити значення стилізації за замовчуванням із «🖌️ Стиль середній» (=`--s 100`) до «🖌️ Стиль низький» (=`--s 50`), «🖌️ Стиль високий» (=`--s 250`) або «🖌️ Стиль дуже високий» (=`--s 750`))

Приклад: `космонавт на коні --s 50` і `космонавт на коні --s 900`

<div style={{textAlign: 'center'}}>
  <img src={midjourney_astronaut_params_s50} style={{width: "350px"}} />
  &nbsp;
   <img src={midjourney_astronaut_params_s900} style={{width: "350px"}} />
</div>

### Версія:
`--v [номер версії]` або `--version [номер версії]` дозволяє отримати доступ до попередніх моделей Midjourney (1–3)

Приклад: `--v 1`, `--v 2` та `--v 3`

<div style={{textAlign: 'center'}}>
  <img src={midjourney_astronaut_params_v1} style={{width: "220px"}} />
  &nbsp;
   <img src={midjourney_astronaut_params_v2} style={{width: "220px"}} />
   &nbsp;
      <img src={midjourney_astronaut_params_v3} style={{width: "220px"}} />
</div>

## Параметри (попередні моделі)

### Однакові початкові значення

`--sameseed`: у той час, як параметр `--seed` створює єдине шумове поле, застосоване до всіх зображень у початковій мережі, параметр sameseed застосовує той самий початковий шум до всіх зображень у початковій мережі, тому отримані зображення будуть дуже схожими.

Приклад: `космонавт на коні --sameseed --v 3`

<div style={{textAlign: 'center'}}>
  <img src={midjourney_astronaut_params_sameseed} style={{width: "350px"}} />
</div>

### Клітинка

`--tile` створює зображення, які можна використовувати як повторювані клітинки для створення безшовних візерунків для тканин, шпалер і текстур (працює лише з моделями 1–3)

Приклад: `космонавт на коні --tile --v 3`

<div style={{textAlign: 'center'}}>
  <img src={midjourney_astronaut_params_tilegrid} style={{width: "220px"}} />
  &nbsp;
  <img src={midjourney_astronaut_params_tile} style={{width: "220px"}} />
  &nbsp;
  <img src={midjourney_astronaut_params_tilecomplete} style={{width: "220px"}} />
</div>

### Відео

`--video` компонує короткий фільм із мережі зображень, що створюється. Реакція з емодзі ✉️ дозволяє боту Midjourney надіслати вам приватне повідомлення із посиланням на відео.

Приклад: `космонавт на коні --video --v 3`

<div style={{textAlign: 'center'}}>
 <video width="320" height="240" autoplay muted>
  <source src="https://i.mj.run/27c89699-d96d-4834-b6fa-b022a453eb28/video.mp4" type="video/mp4">
</source>
</video>
</div>

## Посилання

[Офіційна документація Midjourney](https://docs.midjourney.com/)