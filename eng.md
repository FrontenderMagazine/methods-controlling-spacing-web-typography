<article id="post-245796" class="instapaper_body h-entry e-content">
If you were developing sites in 2006, then you may have worked with a designer
like me who was all up in your business about fonts not looking*exactly* the
same in the browser as they did in mockups.

Then you may have tried explaining to me the pains of cross-browser
compatibility and how different browsers render fonts differently from one 
another. In response, I likely would have sent you an image file that contains 
the content instead to make sure everything looked the same in all browsers. Yes,
I was one of those designers.

Web fonts have come a very long way since then and we now have tools to tweak
the way fonts render in browsers. Some have been around for quite a while. I 
remember my mind nearly bursting with excitement when I discovered
[FitText.js][1] and [Lettering.js][2] way back when.

There are still plenty of situations today where adjusting fonts is needed to
ensure the best legibility despite having all these fancy tools. We're going to 
cover a few of those in this post along with methods for how to deal with them.

### Getting one exact headline to look right

I often run into this one, especially when a design contains a highly
customized web font that looks great in general, but might look funky when used 
in a certain context.

Take the following headline using [Abril Fatface][3] from Google Fonts:<figure
id="post-245805" class="align-none media-245805
">

![][4]</figure>
It a lovely font! However, there are a couple of points I'm not loving with
this particular headline, specifically the spacing between a couple of letters, 
which makes things a little crowded:<figure id="post-245798" class="align-none
media-245798
">

![][5]</figure>
This is where **kerning** comes to the rescue! Kerning is literally defined as
the spacing between letters. All font files, whether we know it or not, contain 
some degree of kerning and we have the CSS`font-kerning` property to remove it
:

    .no-kern-please {
      font-kerning: none;
    }

    <h1 class="no-kern-please">Rubber Baby Buggy Bumpers</h1>

Ah, that looks much better to me, even if it is a subtle difference.<figure id
="post-245799" class="align-none media-245799
">

![][6]</figure>
See the Pen [Kerning Toggle][7] by CSS-Tricks ([@css-tricks][8]) on 
[CodePen][9].

#### Desktop

| Google Chrome | Mozilla Firefox | Internet Explorer | Opera | Apple Safari
|

| 29*           | 34              | No                | 16*   | 7
*           |

#### Mobile / Tablet

| iOS Safari | Android | Opera Mobile | Android Chrome | Android Firefox |

| 8
*         | 4.4*    | 37           | 51             | 48
|

### Fixing poor letter-spacing across the board

If you've ever worked with a web font where the space between every single
letter is either too wide or too narrow, then you know exactly how painful this 
situation is. Here's an example using another beautiful Google web font called
[Dorsa][10]:<figure id="post-245800" class="align-none media-245800">

![][11]</figure>
That might make for a decent display font for headlines, but could you imagine
trying to read that as a paragraph? No bueno.<figure id="post-245801" class="
align-none media-245801
">

![][12]  
<figcaption>Kinda hard to read that content!</figcaption></figure>
The CSS `letter-spacing` property can help make a sweeping change to the
paragraph content if we add a couple pixels between each letter:

    .spaced-out {
      letter-spacing: 2px;
    }

I wouldn't go so far as to say this is still the best font for paragraph text,
but it is much easier to read with that extra spacing:

See the Pen [zKkPqK][13] by CSS-Tricks ([@css-tricks][8]) on [CodePen][9].

#### Desktop

| Google Chrome | Mozilla Firefox | Internet Explorer | Opera | Apple Safari
|

| 4             | 2               | 5.5               | 9     | 3.1
|

#### Mobile / Tablet

| iOS Safari | Android | Opera Mobile | Android Chrome | Android Firefox |

| 3.2
| 2.1     | 10           | 51             | 48
|

### Too little or too much spacing between words

This is an offshoot of the last situation except that the spacing issues are
between each word rather than individual characters.

This is where the CSS [`word-spacing`][14] property is great and universally
accepted by all browsers. Here's an example of a prose using the
[Prompt web font][15] which is a little wider than many other fonts and would
look nicer if it was dialed down a bit for this use case.

See the Pen [GjJaaE][16] by Geoff Graham ([@geoffgraham][17]) on [CodePen][9]

### Gnarly spacing between lines

Not all line heights are considered equal. Take the way some fonts look bigger
than others, even though they have the same assigned`font-size` value.

See the Pen [Difference in line height by font][18] by CSS-Tricks (
[@css-tricks][8]) on [CodePen][9].

Setting the `font-size` sets the bounding box for which a font is allowed to
take up space. If we set our`font-size` at `20px` then that creates a box that
takes up`20px` of vertical space for each character to occupy.<figure id="post-
245802" class="align-none media-245802
">

![][19]</figure>
Some fonts will take up more of the space than others and that will both give
the appearance that one font is larger than the other but also that there is 
more or less vertical space between lines.

We can use the `line-height` property to help adjust that vertical space. A
decent rule of thumb is something like`font-size * 1.5 = line-height` (or use a
unitless`line-height: 1.5;`) for legibility but that will depend on the font
being used and how it occupies vertical space. Check out[molten leading][20].

### Crispness and Legibility

Not all fonts are created equal across operating systems. That's because each
operating system, be it Windows, Mac OS or anything else, will have different 
process for how many pixels to use when displaying fonts.

Many of us web designers loathe the thought of being beholden to how a system
interprets our typography decisions.<figure id="post-245803" class="align-none
media-245803
">

![][21]  
<figcaption>Image source: webtype.com</figcaption></figure>
There are CSS properties at our disposal to increase the apparent resolution of
how fonts are displayed on different systems. This process is more formally 
known as**subpixel rendering** because it instructs the browser to attempt to
fill missing pixels where they might exist.

There is no shortage of #hotdrama over whether it is appropriate to play with
the subpixel rendering of fonts. Despite being written a few years ago, Dmitry 
Fadeyev[summed up his argument][22] against the practice nicely.

> The antialiasing mode is not a “fix” for subpixel rendering — in most
> cases it’s a handicap. Subpixel rendering is technically superior, clearer, and 
> more readable than antialiasing because by utilizing every one of the subpixels 
> it increases its effective resolution used for font smoothing by three times. 
> Antialiasing is useful for certain circumstances, such as for light on dark text,
> but it is absolutely not a replacement for subpixel rendering, and certainly not
> a “fix
> ”.

But let's say we wanted to do it anyway. CSS gives us a certain level of
control over the crispness and legibility by using[`font-smooth`][23] to fill
in what operating systems might leave behind.

The `font-smooth` values include:

*   `auto`: Allows the browser to decide the best case for filling in pixels on
    fonts.
   
*   `never`: Disables the system from auto-smoothing fonts. This will display
    the font in its natural state, jagged edges and all.
   
*   `always`: Instructs the browser toll always add pixels to fonts where it
    sees the opportunity.
   

***Note:** The `font-smooth` property is considered an unofficial property at
the time of this writing and is not recommended for use on a production site. 
There are vendor prefixes to achieve the effect in WebKit and Mozilla, though 
there is no standard implementation.*

Given that note, the following vendor prefixes are currently available with
their own values:

#### -webkit-font-smoothing

*   `none`: Disables font smoothing in WebKit browsers.
*   `antialiased`: Smooths the font on the same level as the pixels already
    provided by the system.
   
*   `subpixel-antialiased`: Smooths the font on a more micro level to give the
    sharpest text possible, particularly on high-resolution screens.
   

#### -moz-osx-font-smoothing

*   `auto`: Allows the browser to decide whether to optimize the font
    smoothness.
   
*   `inherit`: Takes the property value of the parent element.
*   `unset`: The same as specifying `none` in the WebKit prefix.
*   `grayscale`: Similar to the `antialiased` value in the WebKit prefix.

#### Desktop

| Google Chrome | Mozilla Firefox | Internet Explorer | Opera | Apple Safari
|

| 5*            | 25*             | No                | 15*   | 4
*           |

#### Mobile / Tablet

| iOS Safari | Android | Opera Mobile | Android Chrome | Android Firefox |

| No
| No      | No           | No             | No
|

### Oh, wait, you're using SVG?!

SVG has its own level of support for the techniques we've been covering in this
post. We've got kerning (not likely to do much) and the usual suspects letter-
spacing and word-spacing. Interestingly, we also have a`textLength` attribute
which can be used to explicitly set how wide the text should be rendered, and it
will stretch/squish the text to accommodate. The lengthAdjust attribute controls
whether that should happen to just the characters or the glyphs (like 
punctuation) too.

See the Pen [SVG Text Spacing][24] by CSS-Tricks ([@css-tricks][8]) on 
[CodePen][9].

### In Conclusion

Typography on the web is hard! Yes, we do have a ton of control over how type
is displayed, rendered and positioned on the screen. But with great power comes 
great responsibility. At least you now have a few tools at your disposal to 
respond back to web designers who are stuck on the the precision of 
typographical design in the browser.</article>

 [1]: http://fittextjs.com/
 [2]: http://letteringjs.com/
 [3]: https://fonts.google.com/specimen/Abril+Fatface
 [4]: img/letter-spacing-figure2a-1024x113.png%201024w
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