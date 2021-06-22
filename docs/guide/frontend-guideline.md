# Frontend Guidelines 
These guidelines will govern how we write frontend code for BiznetGio.

- [HTML](#html)
  * [Semantics](#semantics)
  * [Accessibility](#accessibility)
  * [Performance](#performance)
- [CSS/SASS](#css)
  * [BEM Syntax](#bem)
  * [Structure](#structure)
    + [Components](#components)
    + [Variables](#variables)
    + [Mixins](#mixins)
- [Javascript](#javascript)
  * [NuxtJs](#sub-heading-2)

## HTML

### Semantics

**Author semantic markup** - HTML gives structure to content, and browsers, search engines, and assistive devices make use of that structure to benefit users. Headings should be `<h1>` through `<h6>` tags, groups of objects should be marked up as `<ul>` or `<ol>` tags, and so on.

```html
<!-- bad -->
<div id=main>
  <div class=article>
    <div class=header>
      <h1>Blog post</h1>
      <p>Published: <span>21st Feb, 2015</span></p>
    </div>
    <p>…</p>
  </div>
</div>

<!-- good -->
<main>
  <article>
    <header>
      <h1>Blog post</h1>
      <p>Published: <time datetime=2015-02-21>21st Feb, 2015</time></p>
    </header>
    <p>…</p>
  </article>
</main>
```
### Accessibility
**Bake in accessibility** - Incorporate [accessibility best practices](http://a11yproject.com/checklist.html) into markup as you author markup rather than tacking it on as an afterthought. For example:

* always using the `alt` attribute properly
* making sure your links and buttons are marked as such (no `<div class=button>` atrocities)
* not relying exclusively on colors to communicate information
* explicitly labelling form controls

```html
<!-- bad -->
<h1><img alt=Logo src=logo.png></h1>

<!-- good -->
<h1><img alt=Company src=logo.png></h1>
```

### Performance
**Place your script at the bottom** - Place script tags at the bottom of the document. Officially, script tags live inside the head. But if we place them in the bottom of the document, just before the closing of the body tag, we can delay their download. This allows our document to load in the dom first, show it to the user, and then request the scripts.

![HTML Script](https://miro.medium.com/max/1200/1*JNOs5MDxiVyw301n0BCy2A.png)

## CSS
#### BEM
We're using [BEM](http://getbem.com/introduction/) as the CSS methodology. BEM stands for “Block Element Modifier”, which means:

- **Block** is the primary component block, such as `.card` or `.btn`
- **Element** is a child of the primary block, such as `.card__title`.
- **Modifier** is a variation of a component style, such as `.alert--error`. 

Utilizing this methodology removes ambiguity about the job a class is doing and allows us to create more legible code.
#### Structure
While the UI Framework contains the base styles and features needed for a solid foundation, the majority of styles and components written will be specific to an application.

The architecture we use looks like this:

```
/main.scss
    settings/
        …partials.scss
    styles/
        …folders/
            …partials.scss
```
#### Components 

Components are finite, discrete, implementation-specific parts of our UI that most people (users, designers, developers, the business) would be able to identify.

Components range from smaller pieces of UI, such as buttons to pagination or more complex "view" components like header banners which need to separated in to multiple BEM blocks (and files) for each component to follow our authoring/architectural process.

#### Variables 
[Sass variables](http://sass-lang.com/guide) are used to control. Here are some prefixes we'll follow for Sass variables:

#### Colors
- `$color-brand-` as a prefix for brand-related colors
- `$color-gray-` for neutral colors. The value of the variable is the percentage of black, so `$color-gray-50` means "50% black", aka `#808080`.
- `$color-dim-` for semi-transparent colors. This
- `$color-utility-` for utility colors, such as success, error, warning, and info messages.

#### Fonts
- `$font-family-` is used to define a font stack.
- `$font-size-` for font sizes. We use t-shirt sizing for font size variables, such as `$font-size-small` or `$font-size-large`.

#### Layout
- `$l-` for layout-specific rules, such as `$l-max-width` for capping the maximum width of a container.

#### Border
- `$border-` for border-related variables, such as border width or radius values.

#### Animation
- `$anim-` for animation-specific variables, such as animation duration or easing values.

#### Breakpoints
- `$bp-` for major breakpoint values that are shared across

### Mixins 
A mixin lets you make groups of CSS declarations that you want to reuse throughout the application, and also allow arguments to be passed in to make them more flexible. A good example is the [`triangle() @mixin`](https://gist.githubusercontent.com/jwebcat/8593788/raw/5bc33f1309c79564b50c94d1f281c07613462764/triangle.scss), which can understand easily.

## Javascript
Coming soon