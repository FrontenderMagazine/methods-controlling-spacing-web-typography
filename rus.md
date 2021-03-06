# Методы управления интервалами в веб-типографике

Если вы разрабатывали сайты в 2006, то вам наверняка доводилось работать с дизайнерами вроде меня, которые не давали вам покоя, если шрифты в браузере *хоть немного* отличались от макета.

Тогда, возможно, вы пробовали объяснить мне всю боль кроссбраузерной совместимости и насколько по-своему разные браузеры рендерят шрифты. В ответ я, скорее всего, отправлял картинку, чтобы убедиться, что все выглядит одинаково во всех браузерах. Да, я был одним из тех дизайнеров.

Веб-шрифты с тех пор прошли очень долгий путь, и теперь у нас есть инструменты управления рендерингом в браузерах, некоторые существуют уже достаточно давно. Я помню, как чуть не умер от восторга, когда нашел [FitText.js][1] и [Lettering.js][2].

Несмотря на все эти замечательные инструменты, сегодня все еще есть множество ситуаций, в которых может понадобиться настройка шрифтов, чтобы обеспечить необходимую удобочитаемость текста. В этой статье мы рассмотрим такие случаи и узнаем как с ними справиться.


## Использование правильного оформления для конкретного заголовка

Я часто так делаю, особенно если в дизайне используются сильно кастомизированные шрифты, которые отлично выглядят в целом, но в конкретном контексте могут смотреться нелепо.

Возьмем заголовок, набранный шрифтом [Abril Fatface][3] из Google Fonts:

![Скриншот][Заголовок шрифтом Abril Fatface]

Отличный шрифт! Однако пара нюансов в этом конкретном заголовке мне не нравится, особенно интервалы между некоторыми буквами, из-за которых он кажется немного сжатым:

![Скриншот][Интервалы между некоторыми буквами Abril Fatface]

Вот где **кернинг** приходит на помощь! Кернинг буквально означает «интервал между буквами». Все файлы шрифтов, знаем мы об этом или нет, содержат несколько степеней кернинга, и у нас есть CSS-свойство `font-kerning`, чтобы их отключить:

    .no-kern-please {
        font-kerning: none;
    }
    
    <h1 class="no-kern-please">Rubber Baby Buggy Bumpers</h1>

Мне кажется, это выглядит намного лучше, даже если на первый взгляд разница незначительна.

![Скриншот][Заголовок шрифтом Abril Fatface без кернинга]

<p data-height="196" data-theme-id="0" data-slug-hash="dOGRwg" data-default-tab="result" data-user="FMRobot" data-embed-version="2" data-pen-title="Пример управления кернингом" class="codepen">Посмотреть <a href="http://codepen.io/FMRobot/pen/dOGRwg/">пример управления кернингом</a>.</p>


### Десктоп

<table class="caniuse">
	<thead>
		<tr>
			<th>Google Chrome</th>
			<th>Mozilla Firefox</th>
			<th>Internet Explorer</th>
			<th>Opera</th>
			<th>Apple Safari</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td class="yes">29*</td>
			<td class="yes">34</td>
			<td class="no">No</td>
			<td class="yes">16*</td>
			<td class="yes">7*</td>
		</tr>
	</tbody>
</table>


### Мобильные и планшеты

<table class="caniuse">
	<thead>
		<tr>
			<th>iOS Safari</th>
			<th>Android</th>
			<th>Opera Mobile</th>
			<th>Android Chrome</th>
			<th>Android Firefox</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td class="yes">8*</td>
			<td class="yes">4.4*</td>
			<td class="yes">37</td>
			<td class="yes">53</td>
			<td class="yes">49</td>
		</tr>
	</tbody>
</table>


## Исправляем межбуквенное расстояние

Если вы хоть раз работали с веб-шрифтом, в котором интервал между символами слишком широкий или слишком узкий, тогда вы знаете, насколько это неприятно. Вот пример использования другого прекрасного шрифта из библиотеки Google Fonts, который называется [Dorsa][10]:

![Скриншот][Пример использования шрифта Dorsa]

Этот шрифт вполне подходит для заголовка, но можете ли вы представить чтение целого параграфа такого текста? Как-то не очень.

![Скриншот][Тяжело читать]

*Это действительно тяжело читать!*

С помощью `letter-spacing` мы можем увеличить межбуквенное расстояние, что значительно повысит читабельность текста:


	.spaced-out {
	    letter-spacing: 2px;
	}


Я бы не сказал, что это лучший шрифт для набора основного текста, но текст стал читабельнее:

<p data-height="346" data-theme-id="0" data-slug-hash="VmeWKX" data-default-tab="result" data-user="FMRobot" data-embed-version="2" data-pen-title="Пример изменения межбуквенного интервала" class="codepen">Посмотреть <a href="http://codepen.io/FMRobot/pen/VmeWKX/">пример изменения межбуквенного интервала</a>.</p>


### Десктоп

<table class="caniuse">
	<thead>
		<tr>
			<th>Google Chrome</th>
			<th>Mozilla Firefox</th>
			<th>Internet Explorer</th>
			<th>Opera</th>
			<th>Apple Safari</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td class="maybe">4</td>
			<td class="yes">2</td>
			<td class="maybe">5.5</td>
			<td class="maybe">9</td>
			<td class="maybe">3.1</td>
		</tr>
	</tbody>
</table>


### Мобильные и планшеты

<table class="caniuse">
	<thead>
		<tr>
			<th>iOS Safari</th>
			<th>Android</th>
			<th>Opera Mobile</th>
			<th>Android Chrome</th>
			<th>Android Firefox</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td class="maybe">3.2</td>
			<td class="maybe">2.1</td>
			<td class="maybe">10</td>
			<td class="yes">53</td>
			<td class="yes">49</td>
		</tr>
	</tbody>
</table>


## Слишком большие или слишком маленькие интервалы между словами

Это частный случай предыдущего пункта, за исключением того, что здесь нас интересуют интервалы вокруг слов, а не вокруг отдельных символов.

Здесь нам поможет свойство [`word-spacing`][14], которое, к тому же, отлично поддерживается браузерами. Вот пример текста, набранного шрифтом [Prompt][15], который несколько шире большинства шрифтов, и, в данном случае, текст будет выглядеть лучше, если немного подкорректировать расстояния между словами.

<p data-height="265" data-theme-id="0" data-slug-hash="QGygNe" data-default-tab="result" data-user="FMRobot" data-embed-version="2" data-pen-title="QGygNe" class="codepen">Посмотреть <a href="http://codepen.io/FMRobot/pen/QGygNe/">пример изменения пробельных интервалов между словами</a>.</p>


## Мерзкий интерлиньяж

Интерлиньяж не всегда одинаков. Так, одни шрифты выглядят больше чем другие, даже если для них установлено одно значение `font-size`.

<p data-height="265" data-theme-id="0" data-slug-hash="Nbxgqm" data-default-tab="result" data-user="FMRobot" data-embed-version="2" data-pen-title="Различия в интерлиньяже в зависимости от шрифта" class="codepen">Посмотреть пример <a href="http://codepen.io/FMRobot/pen/Nbxgqm/">различия интерлиньяжа в зависимости от шрифта</a>.</p>

`font-size` задает блок, в пределах которого шрифту разрешено занимать место. Если мы установим `font-size` в `20px`, это создаст блок, занимающий `20px` вертикального пространства для каждого знака.

![Скриншот][Кегельная площадка]

Некоторые шрифты будут занимать больше места, чем другие, это одновременно создаст видимость того, что одни шрифты больше других, и ощущение большего или меньшего вертикального пространства между линиями.

Мы можем использовать свойство `line-height`, чтобы управлять этим вертикальным пространством. Базовая формула удобочитаемости выглядит так: `font-size * 1.5 = line-height` (или относительный `line-height: 1.5;` без единиц измерения), но это будет зависеть от используемого шрифта и от того, как он занимает вертикальное пространство. Сравните [molten leading][20].


## Четкость и удобочитаемость

Не все шрифты одинаково отображаются в различных операционных системах. Это происходит потому, что в каждой операционной системе, будь то Windows, Mac OS или любая другая, определением, сколько пикселей используется для отображения шрифтов, управляют разные процессы.

Многим из нас, веб-дизайнеров, не нравится зависеть от того, как система интерпретирует наши типографические решения.

![Скриншот][Сглаживание в разных операционных системах]

В нашем распоряжении есть несколько CSS-свойств, которые помогают визуально улучшить то, как шрифты отображаются в разных системах. Формально, этот процесс известен как **субпиксельное сглаживание**, потому что он заставляет браузер постараться визуально отобразить отсутствующие пиксели там, где они должны находится (за счет использования цветовой составляющей — _Прим. ред._).

Нет недостатка в спорах допустимо ли играть с субпиксельным сглаживанием. Несмотря на то, что несколько лет назад Дмитрий Фадеев хорошо [изложил свои аргументы][22] против этой практики.

The antialiasing mode is not a “fix” for subpixel rendering — in most cases it’s a handicap. Subpixel rendering is technically superior, clearer, and more readable than antialiasing because by utilizing every one of the subpixels it increases its effective resolution used for font smoothing by three times.

> Режим сглаживания — это не «фикс» для субпиксельного рендеринга, а, в большинстве случаев, помеха. 
> Субпиксельный рендеринг технически лучше, чище, читабельние
> чем текст, к которому применено сглаживание, потому что использует каждый субпиксель и
> увеличивает его эффективное разрешение, использующееся для сглаживания
> шрифта, в три раза.
> Сглаживание более полезно в конкретных случаях, например, для
> светлого текста на темном фоне, но он не заменяет субпиксельный
> рендеринг и не является «фиксом».

Но, предположим, мы все равно хотим это сделать. CSS дает нам определенный уровень контроля над четкостью и удобочитаемостью через использование [`font-smooth`][23] для заполнения того, что пропустила операционная система.

Значения `font-smooth` включают:

* `auto`: позволяет браузеру выбрать лучший вариант заполнения пикселей в шрифте.
* `never`: отключает системное автосглаживание. Шрифт отображается как есть, со всеми неровными краями.
* `always`: заставляет браузер всегда, когда это возможно, сглаживать шрифт.


> _**Примечание:** Свойство `font-smooth` считается неофициальным на момент написания статьи и не рекомендуется для использования на продакшен-версии сайта. Есть свойства с вендорными префиксами для WebKit и Mozilla, хотя стандартной реализации нет._

Существующие свойства с вендорными префиксами можно использовать с их специфическими значениями:

### -webkit-font-smoothing

* `none`: отключает сглаживание в Webkit-браузерах.
* `antialiased`: сглаживает шрифт на том же уровне, что уже предоставляется системой
* `subpixel-antialiased`: сглаживает шрифт на микроуровне для обеспечения максимальной резкости текста, в частности, на экранах с высоким разрешением.


### -moz-osx-font-smoothing

*   `auto`: позволяет браузеру решать где оптимизировать сглаживание.
*   `inherit`: наследует значение у родительского элемента.
*   `unset`: то же, что и `none` для WebKit.
*   `grayscale`: то же, что и `antialiased` для WebKit.


### Десктоп

<table class="caniuse">
	<thead>
		<tr>
			<th>Google Chrome</th>
			<th>Mozilla Firefox</th>
			<th>Internet Explorer</th>
			<th>Opera</th>
			<th>Apple Safari</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td class="maybe">5*</td>
			<td class="maybe">25*</td>
			<td class="no">No</td>
			<td class="maybe">15*</td>
			<td class="maybe">4*</td>
		</tr>
	</tbody>
</table>


### Мобильные и планшеты

<table class="caniuse">
	<thead>
		<tr>
			<th>iOS Safari</th>
			<th>Android</th>
			<th>Opera Mobile</th>
			<th>Android Chrome</th>
			<th>Android Firefox</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td class="no">No</td>
			<td class="no">No</td>
			<td class="no">No</td>
			<td class="no">No</td>
			<td class="no">No</td>
		</tr>
	</tbody>
</table>


## О, подождите, вы используете SVG?!

У SVG свой собственный уровень поддержки методов, рассмотренных в этой статье. У нас есть кернинг (с не очень широкими возможностями) и обычные свойства `letter-spacing` (межбуквенное расстояние) и `word-spacing` (расстояние между словами). Интересно, что у нас также есть атрибут `textLength`, который может использоваться для явного указания как широко может рендериться текст, и он растягивает или сжимает текст, чтобы вместить его. Атрибут `lengthAdjust` контролирует рендеринг как символов, так и глифов (например, пунктуации).

<p data-height="265" data-theme-id="0" data-slug-hash="ObMgPa" data-default-tab="html,result" data-user="FMRobot" data-embed-version="2" data-pen-title="Межбуквенные расстояния в SVG" class="codepen">Посмотреть пример различных <a href="http://codepen.io/FMRobot/pen/ObMgPa/">межбуквенных расстояний в SVG</a>.</p>


## В заключение

Типографика в вебе — это сложно! Да, мы можем контролировать как разные символы отображаются, отрисовываются и позиционируются на экране. Но с большой силой приходит и большая ответственность. Теперь в вашем распоряжении есть, по меньшей мере, несколько приемов, чтобы отвечать веб-дизайнерам, которые зацикливаются на точности типографического дизайна в браузере.

<style>
	.caniuse td,
	.caniuse th {
		padding: .5rem;
		width: 20%;
		box-sizing: border-box;
	}
	table.caniuse tbody tr:hover td.no,
	td.no {
		box-shadow: none;
		background-color: rgba(255,0,0,.25);
	}
	table.caniuse tbody tr:hover td.yes,
	td.yes {
		box-shadow: none;
		background-color: rgba(0,255,0,.25);
	}
	table.caniuse tbody tr:hover td.maybe,
	td.maybe {
		box-shadow: none;
		background-color: rgba(255,127,0,.25);
	}
</style>


[1]: http://fittextjs.com/
[2]: http://letteringjs.com/
[3]: https://fonts.google.com/specimen/Abril+Fatface
[5]: img/letter-spacing-figure2-1024x225.jpg%201024w
[6]: img/letter-spacing-figure3-1024x225.jpg%201024w
[7]: http://codepen.io/team/css-tricks/pen/PGpOkd/
[8]: http://codepen.io/css-tricks
[9]: http://codepen.io
[10]: https://fonts.google.com/specimen/Dorsa?selection.family=Dorsa
[11]: img/letter-spacing-figure4-1024x230.png%201024w
[12]: img/letter-spacing-figure5-1024x198.png%201024w
[13]: http://codepen.io/team/css-tricks/pen/zKkPqK/
[14]: https://css-tricks.com/almanac/properties/w/word-spacing/
[15]: https://fonts.google.com/specimen/Prompt?selection.family=Prompt
[16]: http://codepen.io/geoffgraham/pen/GjJaaE/
[17]: http://codepen.io/geoffgraham
[18]: http://codepen.io/team/css-tricks/pen/BLWmzv/
[19]: img/letter-spacing-figure6-1024x270.png%201024w
[20]: https://css-tricks.com/molten-leading-css/
[21]: img/letter-spacing-figure7-300x48.png%20300w
[22]: http://usabilitypost.com/2012/11/05/stop-fixing-font-smoothing/
[23]: https://www.w3.org/TR/WD-font/#font-smooth
[24]: http://codepen.io/team/css-tricks/pen/KgWyXw/

[Заголовок шрифтом Abril Fatface]: img/letter-spacing-figure2a.png "Заголовок шрифтом Abril Fatface"
[Интервалы между некоторыми буквами Abril Fatface]: img/letter-spacing-figure2.jpg "Интервалы между некоторыми буквами Abril Fatface"
[Заголовок шрифтом Abril Fatface без кернинга]: img/letter-spacing-figure3.jpg "Заголовок шрифтом Abril Fatface без кернинга"
[Пример использования шрифта Dorsa]: img/letter-spacing-figure4.png "Пример использования шрифта Dorsa"
[Тяжело читать]: img/letter-spacing-figure5.png "Тяжело читать"
[Кегельная площадка]: img/letter-spacing-figure6.png "Кегельная площадка"
[Сглаживание в разных операционных системах]: img/letter-spacing-figure7.png "Сглаживание в разных операционных системах"

