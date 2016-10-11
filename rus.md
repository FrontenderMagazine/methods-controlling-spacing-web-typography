Если вы разрабатывали сайты в 2006, то работали с дазайнерами типа меня, которые -придирались- к шрифтам, которые *хоть немного* отличались от макета в браузере.

Тогда вы, возможно, пробовали объяснить мне всю боль кросс-браузерной совместимости или как разные браузеры рендерят шрифты -по-разному-. В ответ я, скорее всего, отправлял картинку, чтобы убедиться, что все выглядит одинаково во всех браузерах. Да, я был одним из тех дизайнеров.

Веб шрифты прошли очень долгий путь с тех пор и теперь у нас есть инструменты управления рендерингом в браузерах. Некоторые существуют уже давно. Я помню, как чуть не лопнул от восторга, когда нашел [FitText.js][1] и [Lettering.js][2].

Сегодня все еще существует множество ситуаций, в которых необходима настройка шрифтов, которая может обеспечить необходимую четкость, несмотря на все эти замечательные инструменты. Мы узнаем, как справиться с несколькими из них в этой статье.

## Добавление одного точного заголовка, чтобы выглядеть правильно

Я часто пользуюсь этим, особенно когда в дизайне используются высоко кастомизированные шрифты, которые отлично выглядят в целом, но могут смотреться нелепо в конкретном контексте.

Возьмем следующий заголовок, набранный [Abril Fatface][3] из Google Fonts:
<img src="img/letter-spacing-figure2a-1024x113.png 1024w">
Это отличный шрифт! Как бы то ни было, пара нюансов этого конкретного заголовка мне не нравится, особенно интервалы между некоторыми буквами, которые делают его немного стиснутым
<img src="img/letter-spacing-figure2-1024x225.jpg 1024w">
Вот где **кернинг** приходит на помощь! Кернинг буквально значит «интервал между буквами». Все файлы шрифтов, вне зависимости от того, знаем мы или нет, содержат несколько степеней кернинга и у нас есть CSS-свойство `font-kerning`, чтобы удалить их:
```
	.no-kern-please {
      font-kerning: none;
    }

    <h1 class="no-kern-please">Rubber Baby Buggy Bumpers</h1>
```
Это неуловимая разница, но она может пригодится, если ваш дизайнер (или ваше собственное видение) хочет этого.
<img src="img/letter-spacing-figure3-1024x225.jpg 1024w">