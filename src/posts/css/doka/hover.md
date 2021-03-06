---
title: :hover
name: hover
autor: ABatickaya
co-autors:
designers:
contributors:
summary:
  - :hover
  - LVHA
  - псевдокласс
---

## Кратко

Хорошим паттерном в сайтостроении считается реакция элементов на действия пользователя. Например, если на элемент можно нажать, то при наведении курсора его стили должны немного меняться, как бы говоря пользователю «нажми меня!».

Раньше интерактив можно было реализовать только при помощи JS, что сильно усложняло жизнь верстальщикам. Но сегодня у нас существует отличный помощник — псевдокласс `:hover`.

![/assets/images/posts/hover/hover-gif.gif](/assets/images/posts/hover/hover-gif.gif)

## Пример

Ссылка в спокойном состоянии будет чёрного цвета и без подчёркивания, а при наведении курсора мыши сменит цвет на розовый и у неё появится подчёркивание. Пользователь поймёт, что это интерактивный элемент с которым можно взаимодействовать.

```css
.link {
  color: #000;
  text-decoration: none;
}

.link:hover {
  color: pink;
  text-decoration: underline;
}
```

## Как пишется

После любого селектора ставим двоеточие и пишем ключевое слово `hover`.

```css
a:hover {
} /* Селектор по тегу + :hover */
.link:hover {
} /* Селектор по классу + :hover */
li .link:hover {
} /* Составной селектор + :hover */
#id:hover {
} /* Селектор по тегу + :hover */
.link:before:hover {
} /* Селектор по классу + псевдоэлемент + :hover */
```

## Как это понять

Браузер подставляет любому элементу, на который наводится курсор, _пометку_ в виде класса, который создаётся автоматически. Мы можем стилизовать этот класс на своё усмотрение, при этом сама логика и механизм отслеживания наведения курсора будет скрыт под капотом движка браузера.

## Подсказки

💡 `:hover` можно очень круто анимировать, добавив в блок кода свойство [transition](/posts/css/doka/transition) 🎉

💡 На наведения курсора может реагировать абсолютно любой элемент, не обязательно ссылка или кнопка.

💡 Если дизайнер не нарисовал в макете разные состояния либо просите у него это сделать, либо пропишите стили на своё усмотрение. Но любой элемент, на который можно нажать, должен иметь как минимум стили для `:hover`.

## В работе

{% include "autors/ABatickaya/in-work.njk" %}

🛠 Пользователь может зайти на ваш сайт не только с ПК, где есть мышка и её можно на что-то навести, но и с планшета или телефона, где мышкой выступает палец, а его нельзя на что-то навести, им можно только кликнуть.

Хорошей практикой является сбрасывать `:hover` стили для тач-устройств. Иначе при нажатии на какой-то элемент ховер-стили будут _залипать_ — телефон не знает, когда вы отводите палец в сторону.

🛠 Сайт смотрится аккуратнее и интереснее, если изменение стилей хотя бы немного анимировано, а не происходит резко. Этот принцип взят из окружающего нас мира. Вспомните хоть одно событие, которое происходит резко, моментально, без промежуточных стадий. Не вспомните 😏

Я в своей работе стараюсь делать анимацию ховер-стилей по принципу "появляется быстро, пропадает медленно". Это позволяет пользователю быстро увидеть реакцию на свои действия и не дожидаться окончания анимации.

```css
.link {
  color: #000;
  transition: color 0.5s; /* Скорость изменения цвета с розового на чёрный */
}

.link:hover {
  color: pink;
  transition: color 0.1s; /* Скорость изменения цвета с чёрного на розовый */
}
```

<p class="codepen" data-height="265" data-theme-id="dark" data-default-tab="result" data-user="solarrust" data-slug-hash="qBbgdYo" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title=":hover + transition">
  <span>See the Pen <a href="https://codepen.io/solarrust/pen/qBbgdYo">
  :hover + transition</a> by Alena (<a href="https://codepen.io/solarrust">@solarrust</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

Ссылка быстро (за 0.2 секунды) меняет цвет с чёрного на розовый при наведении курсора и чуть медленнее (за 0.5 секунды) меняет цвет обратно с розового на чёрный когда курсор уводится за пределы ссылки.

🛠 Если вы задаёте стили для разных состояний ссылок, то следует придерживаться определённого порядка в объявлении стилей: `:link` — `:visited` — `:hover` — `:active`.

Этот порядок легко запомнить в виде аббревиатуры LVHA.

{% include "autors/ABatickaya/autor.njk" %}
