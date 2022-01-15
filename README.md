## My changes

  - If you put one `<img...>` in a slide, it will be displayed as background.
    - You can set background opacity 0..1 using `BIG_IMAGE_OPACITY` (in the same way as [`BIG_ASPECT_RATIO`](#customizing-the-aspect-ratio)):

      ```html
      <script>BIG_IMAGE_OPACITY=0.5;</script>
      <script src='big.js'></script>
      ```
      
    - If present, text in slides with a background image is aligned to bottom.
  - You can set text & background color usign inline css:

    ```html
    <div style="background-color: #002744; color: #ffe;">
      Text<br>&amp; background colors.
    </div>
    ```

# Big

A presentation system that works great for creative, hurried people making focused presentations. Stop tweaking fonts and filling slides with text. Big is a configuration-free system that naturally encourages good style.

- [Features](#features)
- [Writing a presentation](#writing-a-presentation)
- [Giving presentations](#giving-presentations)
- [Using Big](#using-big)
  - [Customizing the aspect ratio](#customizing-the-aspect-ratio)
  - [Avoiding line breaks](#avoiding-line-breaks)
  - [Auto advancing slides](#auto-advancing-slides)
  - [Showing code](#showing-code)
  - [Themes](#themes)

## Features

- The entire system is about 16kb
- Speakers notes appear in your developer console, which you can put on your other screen
- Themes are just CSS, and easy to make

## Writing a presentation

Big presentations are webpages: slides are `div` elements, and any text styling or additional elements are addable by using HTML. The text in each div is sized to fit the screen. A slide can be as simple as:

```html
<div>Big</div>
```

If you want speakers notes - notes that you can see on your laptop screen but aren't shown on the main projector - you can use a `<notes>` element:

```html
<div>
  Citrus
  <notes>Aren't oranges, lemons, and limes great?</notes>
</div>
```

Open your [developer console](http://debugbrowser.com/), and you'll see your speaker notes in it when you visit that slide! In most browsers, the console is detachable, so you can move it to a different screen or window when you're giving the presentation.

That's all you need to start writing presentations!

## Giving presentations

You can advance slides the usual way, by clicking them. You can also use the left & right arrow keys, and the up and down arrow keys. On touch devices, you can navigate forward by tapping and also navigate forward and backwards by swiping.

Big also has three modes if you want to quickly jump to a slide, or print a presentation. You can switch between modes by hitting the `t`, `p`, and `j` keys.

* **t**alk is the default mode. Slides are shown one at a time.
* **p**rint: is useful for print output or as an overview: it'll include
  two slides per printed page, and shows speakers notes along with slides
* **j**ump: Shows many slides per page, useful for quickly finding a slide and 'jumping' to it. When you're in jump mode, you can use the arrow keys to quickly select a slide and hit Enter to jump to that slide, or click the
  slide you want.

## Using Big

Big is designed to be simple, so if you just want to give a [Takahashi](https://en.wikipedia.org/wiki/Takahashi_method) style presentation with just text, you don't need to read any further! But it can also go far beyond the basics.

### Customizing the aspect ratio

To keep presentations uniform across devices, Big keeps the aspect ratio of presentations constant by default: by default, presentations are 4:3 aspect ratio.

You can customize the aspect ratio by setting a `BIG_ASPECT_RATIO` variable _before_ Big is included on a page:

```html
<script>BIG_ASPECT_RATIO=2;</script>
<script src='big.js'></script>
```

You can also turn this feature off, by setting `BIG_ASPECT_RATIO` to `false`, which will let presentations occupy the aspect ratio of the device they're displayed on:

```html
<script>BIG_ASPECT_RATIO=false;</script>
<script src='big.js'></script>
```

### Avoiding line breaks

By default, Big will wrap lines of text. Sometimes you don't want this to happen, if you have some text that would look odd wrapped. In this case, you can use the `nowrap` class to keep some text from wrapping.

```html
<div>
  beyond the <code>for</code> loop
  <br />
  <small class=nowrap>@tmcw / Tom MacWright</small>
</div>
```

### Auto advancing slides

Sometimes you'll give presentations like [PechaKucha](https://en.wikipedia.org/wiki/PechaKucha) and [Ignite](https://en.wikipedia.org/wiki/Ignite_(event)) involve auto-advancing slides. You can achieve this by adding a `data-time-to-next` attributes to slides: this will cause  them to auto-advance after a specific number of seconds:

```html
<div data-time-to-next=20>
  My sales pitch in 20 seconds
</div>
```

### Showing code

There are many ways to do code highlighting in presentations. My personal
philosophy is that you should never show more than 8 lines of code
on a slide, and instead of using traditional semantic highlighting, you should
manually add emphasis to focus points in the code.

```html
<div>
    problem one: make some animals rock
    <pre>var animals = <em>['cats', 'dogs']</em>;</pre>
</div>
```

```css
pre {
  margin:0;
  padding:0.2em;
  background:#fff;
  color:#000;
  font-weight:normal;
}

pre em {
  color:#000;
  background:yellow;
}
```

But if you want traditional code highlighting, you can include [highlight.js](https://highlightjs.org/) to do just that. You'll want to include [the library](https://highlightjs.org/download/), and use `hljs.initHighlightingOnLoad();` like [in their usage instructions](https://highlightjs.org/usage/).

### Themes

Big presentations are hackable, so you can design yours from scratch, or by customizing one of the default themes, but there are also a few default themes so that you can get going with a solid aesthetic right off the bat.

At the very least, themes are CSS files. You can pick a theme by picking one in the `themes` directory. Bundled with Big are these themes:

- **dark**: near-black background and near-white text, this one is my go-to for most presentations that rely on underpowered projectors.
- **light**: like dark, but flipped.
- **white**: instead of tastefully off-white and off-black, this theme uses stark, literal black & white colors.
