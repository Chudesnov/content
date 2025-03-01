---
title: "`object-fit`"
authors:
  - solarrust
contributors:
  - skorobaeus
keywords:
  - стили картинок
  - положение картинок
  - object
  - fit
  - img
tags:
  - doka
---

## Кратко

Свойство, которое позволяет управлять тем, как картинка [`<img>`](/html/img) или видео [`<video>`](/html/video) будет подстраиваться под заданные размеры.

По своему поведению очень похоже на свойство [`background-size`](/css/background-size) для фоновых изображений.

## Пример

Представим, что у нас есть картинка размером 500 на 150 пикселей:

```html
<img
  class="image"
  src="images/landscape.jpg"
  alt="Картинка из примера про object-fit"
>
```

По дизайну картинка должна занимать 250 на 250 пикселей. Если мы просто зададим эти размеры, то картинка сильно деформируется.

```css
.parent {
  width: 250px;
  height: 250px;
  border: 1px solid #FFFFFF; /* Для наглядности */
}
```

<iframe title="Искажённая картинка" src="demos/no-fit/" height="448"></iframe>

Выглядит не очень. Но тут на помощь приходит свойство `object-fit`, которое позволит нам сохранить пропорции исходного изображения при _подстройке_ под нужные нам размеры.

```css
.image {
  /* ---//--- */
  object-fit: cover;
}
```

Картинка не деформировалась, подстроилась под нужные размеры. Другой вопрос, что на ней теперь почти ничего не видно 😅, но это мелочи.

<iframe title="Картинка полностью помещается" src="demos/fit/" height="448"></iframe>

## Как пишется

Свойство задаётся для самого тега `<img>`, не для родителя. Пишем свойство, а в качестве значения задаём одно из ключевых слов. В отличие от [`background-size`](/css/background-size) мы не можем задать конкретные размеры в качестве значения 🤔

Доступные значения:

- `fill` — картинка полностью вписывается в указанные размеры без соблюдения собственных пропорций. Часто это приводит к ощутимым деформациям.
- `contain` — картинка подстроится под заданные размеры так, чтобы поместится внутри целиком без нарушения пропорций.
- `cover` — картинка без нарушения пропорций заполнит всю доступную область, обрезая всё ненужное.
- `none` — значение по умолчанию, картинка отображается без изменения пропорций или размеров.
- `scale-down` — браузер сравнивает размеры картинки со значением `none` и со значением `contain` и выбирает одно из этих значений, деформируя картинку соответствующим образом. Сложно объяснить, посмотрите демку 🥴

<iframe title="Варианты object-fit" src="demos/every/" height="500"></iframe>

Советую поизменять размер окна браузера чтобы наглядно увидеть как картинки подстраиваются (или нет) под заданные размеры.

## Как это понять

Дословно свойство переводится как «объект подходит», что вполне точно отражает принцип его работы. Свойство управляет тем, как подгружаемая картинка будет вписываться в рамки заданных размеров.

## Подсказки

💡 Задавайте свойство самой картинке `<img>`, не родительскому контейнеру.

💡 Работает только если картинке задан хотя бы один размер: ширина или высота. Иначе браузер не понимает в какую область нужно вписать картинку.

💡 Свойство и его значение не наследуется. Хотя я бы посмотрела на то, как вы вложите что-нибудь внутрь картинки 0_о

💡 Не анимируется 😒

💡 Классно работает в сочетании со свойством [`object-position`](/css/object-position).
