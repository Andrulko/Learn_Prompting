---
sidebar_position: 60
---

# 🟢 Терміни із заданою значущістю

Деякі моделі (Stable Diffusion, Midjourney тощо) дозволяють задавати значущість терміну в запиті. Це можна використовувати для акценту на певних словах або фразах в отриманому зображенні. Його також можна використовувати, щоб зменшити акцент на певних словах або фразах в отриманому зображенні. Розглянемо простий приклад:

import mountains from '@site/docs/assets/images_chapter/mountains.png';
import mountains_no_trees from '@site/docs/assets/images_chapter/mountains_no_trees.png';
import planets from '@site/docs/assets/images_chapter/planets.png';


# Приклад

Ось кілька гір, отриманих за допомогою Stable Diffusion, за запитом `гора`.

<div style={{textAlign: 'center'}}>
  <img src={mountains} style={{width: "350px"}} />
</div>

Однак, якщо нам потрібні гори без дерев, ми можемо використати запит `гора | дерево:-10`. Оскільки ми задали деревам дуже негативну значущість, їх немає на створеному зображенні.

<div style={{textAlign: 'center'}}>
  <img src={mountains_no_trees} style={{width: "350px"}} />
</div>

Терміни із заданою значущістю можна об’єднати в складніші запити, наприклад `Планета в космосі:10 | наповнена червоним, синім і фіолетовим кольором:4 | інопланетяни:-10 | 4K, висока якість`

<div style={{textAlign: 'center'}}>
  <img src={planets} style={{width: "350px"}} />
</div>

## Примітки

Дізнайтеся більше про задання значущості в деяких ресурсах у кінці цього розділу.