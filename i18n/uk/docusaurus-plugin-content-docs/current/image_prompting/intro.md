---
sidebar_position: 1
---

# 🟢 Вступ

Написати якомога кращий запит для створення ідеального зображення – особливий виклик. На відміну від запитів, які зосереджені на створенні тексту, методи написання запитів для генерування зображень все ще не достатньо вивчені та сформовані. Причиною цього можуть бути постійні труднощі під час створення об’єктів, які є переважно суб’єктивними та часто не мають критеріїв, за якими їх можна було б оцінити. Однак не лякайтеся, оскільки спільнота, яка займається написанням запитів для створення зображень, (@parsons2022dalleprompt) провела кілька експериментів, у яких дослідила, як правильно робити запити в певних моделях, щоб отримати гарний результат (@rombach2021highresolution) (@ramesh2022hierarchical).

У цьому посібнику висвітлено основні методики написання запитів для зображень, і ми наполегливо рекомендуємо переглянути добірку корисних ресурсів в кінці розділу. Крім того, нижче ми надаємо покроковий опис процесу написання запитів для зображень.


## Приклад

Ось приклад того, як я створив зображення для першої сторінки цього курсу. Я експериментував із низькополігональним стилем у рамках проєкту глибокого навчання з підкріпленням в нейронній мережі, що створює 3D-модель на основі 2D-зображення (NeRF). Мені сподобався низькополігональний стиль, і я хотів використати його для зображень цього курсу.

Для зображень на першій сторінці я обрав космонавта, ракету та комп’ютер.

Я багато досліджував, як створювати низькополігональні зображення, на [r/StableDiffusion](https://www.reddit.com/r/StableDiffusion/) та інших сайтах, але не міг знайти нічого справді корисного.

Я вирішив просто розпочати з запиту до DALLE: `Low poly white and blue rocket shooting to the moon in front of a sparse green meadow` і подивитися, що вийде.

import rockets1 from '@site/docs/assets/images_chapter/rockets_dalle_1.png';
import rockets2 from '@site/docs/assets/images_chapter/rockets_dalle_2.png';
import computer_1 from '@site/docs/assets/images_chapter/computer_dalle_1.png';
import astronaut_1 from '@site/docs/assets/images_chapter/astronaut_dalle_1.png';
import astronaut_2 from '@site/docs/assets/images_chapter/astronaut_sd_1.png';
import rocket_sd_1 from '@site/docs/assets/images_chapter/rocket_sd_1.png';
import rocket_final from '../../static/img/rocket.png';
import laptop_sd_1 from '@site/docs/assets/images_chapter/laptop_sd_1.png';
import gemstone_sd_1 from '@site/docs/assets/images_chapter/gemstone_sd_1.png';
import gemstone_sd_2 from '@site/docs/assets/images_chapter/gemstone_sd_2.png';
import gemstone_sd_3 from '@site/docs/assets/images_chapter/gemstone_sd_3.png';
import focus_final from '../../static/img/computer.png';
import astronaut_final from '../../static/img/astronaut.png';

<div style={{textAlign: 'center'}}>
  <img src={rockets1} style={{width: "750px"}} />
</div>

<div style={{textAlign: 'center'}}>
  <img src={rockets2} style={{width: "750px"}} />
</div>

Я подумав, що ці результати були досить прийнятними як для першої спроби; особливо мені сподобалася нижня ракета зліва.

Також я хотів комп’ютер у такому самому стилі: `Low poly white and blue computer sitting in a sparse green meadow`

<div style={{textAlign: 'center'}}>
  <img src={computer_1} style={{width: "750px"}} />
</div>

Зрештою, мені потрібен ще й космонавт! Запит `Low poly white and blue astronaut sitting in a sparse green meadow with low poly mountains in the background`, здається, підходить.

<div style={{textAlign: 'center'}}>
  <img src={astronaut_1} style={{width: "750px"}} />
</div>

Другий здався мені прийнятним.

Тепер у мене були й космонавт, і ракета, і комп’ютер. Я був задоволений ними, тому розмістив їх на першій сторінці. Після декількох днів і коментарів моїх друзів я зрозумів, що стиль зображень відрізняється😔.


Я ще трохи пошукав на [r/StableDiffusion](https://www.reddit.com/r/StableDiffusion/) і знайшов людей, які використовують слово «ізометричний». Я теж вирішив спробувати, використовуючи Stable Diffusion замість DALLE. Я також зрозумів, що мені потрібно додати більше модифікаторів до мого запиту, щоб окреслити стиль. Я спробував наступний запит: `A low poly world, with an astronaut in white suit and blue visor sitting in a sparse green meadow with low poly mountains in the background. Дуже детальний, ізометричний, 4K`

<div style={{textAlign: 'center'}}>
  <img src={astronaut_2} style={{width: "250px"}} />
</div>

Вийшло не надто добре, тож я вирішив натомість почати з ракети:

`Низькополігональний світ із біло-блакитною ракетою, що вилітає з розмитого зеленого лугу з низькополігональними горами на фоні. Highly detailed, isometric, 4K`

<div style={{textAlign: 'center'}}>
  <img src={rocket_sd_1} style={{width: "250px"}} />
</div>

Не надто якісно, але після декількох повторів у мене вийшло це: 

<div style={{textAlign: 'center'}}>
  <img src={rocket_final} style={{width: "250px"}} />
</div>

Тепер мені потрібен був кращий ноутбук

`Низькополігональний світ з біло-блакитним ноутбуком на розмитому зеленому лузі з низькополігональними горами на фоні. Екран повністю синій. Дуже детальний ізометричний, 4K`

<div style={{textAlign: 'center'}}>
  <img src={laptop_sd_1} style={{width: "250px"}} />
</div>

Я отримав деякі суперечливі результати; мені подобається правий нижній, але я вирішив спробувати дещо інше.

`Низькополігональний світ із яскравим біло-блакитним дорогоцінним каменем на розмитому зеленому лузі з низькополігональними горами на фоні. Дуже детальний, ізометричний, 4K`

<div style={{textAlign: 'center'}}>
  <img src={gemstone_sd_1} style={{width: "250px"}} />
</div>

Це було не зовсім те, що треба. Спробуймо дещо чарівне та яскраве.

`Низькополігональний світ із яскравим біло-блакитним дорогоцінним каменем, що за допомогою магії завис у центрі екрану над розмитим зеленим лугом із низькополігональними горами на фоні. Дуже детальний, ізометричний, 4K`

<div style={{textAlign: 'center'}}>
  <img src={gemstone_sd_2} style={{width: "250px"}} />
</div>

Мені сподобалися результати, але я хотів, щоб камінь був чітко посередині екрану.

`Низькополігональний світ із яскравим біло-блакитним дорогоцінним каменем, що за допомогою магії завис у центрі екрану над розмитим зеленим лугом із низькополігональними горами на фоні. Дуже детальний, ізометричний, 4K`

<div style={{textAlign: 'center'}}>
  <img src={gemstone_sd_3} style={{width: "250px"}} />
</div>

Десь тут я використав здатність SD забезпечувати вплив попереднього результату на наступні зображення. І таким чином я дійшов до:

<div style={{textAlign: 'center'}}>
  <img src={focus_final} style={{width: "250px"}} />
</div>

Нарешті я почав працювати над космонавтом.

`Низькополігональний світ із космонавтом у білому костюмі та блакитному шоломі, який сидить на розмитому зеленому лузі із низькополігональними горами на фоні. Дуже детальний ізометричний, 4K`

<div style={{textAlign: 'center'}}>
  <img src={astronaut_final} style={{width: "250px"}} />
</div>

На цьому етапі я був достатньо задоволений однаковістю стилю на моїх трьох зображеннях, щоб використовувати їх на вебсайті. Головний висновок, якого я дійшов, полягав у тому, що це був багаторазово повторюваний процес, що вимагав значних досліджень, і мені довелося змінювати свої очікування та ідеї, експериментуючи з різними запитами та моделями.