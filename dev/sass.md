<img src="/uploads/logos/sass-logo.png" align="right" />

# SASS
##### Best practices and rules for the SASS (Syntactically Awesome StyleSheets) language

Standards and rules to follow are defined per team / project.

- [Code Style](#code-style)
- [Categorizing CSS Rules](#categorizing-css-rules)
  - [Base](#base)
  - [Layout](#layout)
  - [Module](#module)
- [Selectors](#selectors)
  - [Formatting](#formatting)
  - [**Avoid**: ID selectors](#avoid-id-selectors)
  - [**Avoid**: Element selectors](#avoid-element-selectors)
  - [**Avoid**: Specificity](#avoid-specificity)
  - [**Avoid**: Deep Nesting](#avoid-deep-nesting)
- [States](#states)
- [Properties](#properties)
  - [Formatting](#formatting-1)
  - [Ordering](#ordering)
  - [**Avoid**: Browser-specific prefixes](#avoid-browser-specific-prefixes)
  - [**Avoid**: !important](#avoid-important)
- [Colors](#colors)
  - [Material Design mixin](#material-design-mixin)
- [Comments](#comments)
- [Media Queries](#media-queries)
- [Units](#units)

## Code Style

The style guide presented here is a mix of SMACSS and BEM best practices.

Always use the `.scss` syntax, never the old `.sass` syntax.

## Categorizing CSS Rules

- Base
- Layout
- Module

### Base

The base folder should contains the following items:

- CSS Resets
- Variables
- Global Mixins
- Global Element Styles (no classes / IDs): e.g. head, body, a, etc.
- Grid
- Colors Palette
- Animations

### Layout

The layout folder should contains styles that are common to all pages on the site. Usually the header, footer, sidebar, etc. files.

- Header
- Footer
- Navigation
- Sidebar
- Containers

### Module

The module folder should contains styles that apply to specific components, modules, pages, etc. Basically anything that doesn't fit in the Base or Layout categories.

## Selectors

### Formatting

- Selectors (and variables) should be written in kebab-case *(e.g. some-element-class)*.
- When using multiple selectors in a rule declaration, give each selector its own line.
- Put a space before the opening brace { in rule declarations.
- Put closing braces } of rule declarations on a new line.
- Put blank lines between rule declarations

### **Avoid**: ID selectors

IDs should not be used for CSS at all.

```scss
/* BAD */
#ad-placement { }

/* GOOD */
.ad-placement { }
```

### **Avoid**: Element selectors

Using plain element selectors simply add complexity to the project as it grows. Define classes for all elements instead.

```scss
/* BAD */
.folder > span { }
.folder span:nth-child(2) { }
custom-element-tag { }

/* GOOD */
.folder { }
.folder-span { }
.folder-span-secondary { }
```

### **Avoid**: Specificity

Do not attach an element to a class or use immediate child operators (unless absolutely necessary). They add pointless complexity, makes it harder to override styles and decrease browser performance when applying styles.

```scss
/* BAD */
div.content > img.thumbnail { }

/* GOOD */
.content .thumbnail { }
```

### **Avoid**: Deep Nesting

Nesting should be limited to **at most 3 levels deep**.

```scss
/* BAD */
.content {
  .section {
    .banner {
      &-featured {
        &-title { }
      }
    }
  }
}

/* DO */
.content { }
.section { }
.banner {
  &-featured { }
  &-title { }
}
```

As you can see in the example above, you can use the `&-` syntax to specify children elements without nesting them. The `.banner` selector above would produce the following output:

```css
.banner { }
.banner-featured { }
.banner-title { }
```

## States

States are classes that changes the behavior / look of another class, such as active, featured, shown, hidden, collapsed, pressed, position, etc.

States should be prefixed by either:
- **is-** for states affecting the current element only.
- **has-** for states affecting child content.

```scss
.content {
  background-color: #FFF;

  &.is-featured {
    background-color: #555;
  }
  &.is-hidden {
    display: none;
  }
}

.item-list {
  margin-left: 0;
  
  /* HAS- example */
  
  &.has-children {
    margin-left: 50px;
    
    .item-list-item {
      background-color: #CCC;
    }
  }
  
  /* IS- example */
  
  &-item {
    color: #000;
    
    &.is-active {
      color: #F00;
    }
  }
}
```

## Properties

### Formatting

- In properties, put a space after, but not before, the : character.
- Do not put units when the value is 0. *(e.g. border-width: 0;)*
- Use `border: 0;` instead of `border: none;` to specify that a style has no border.

### Ordering

1. Property definitions

    List all standard property declarations, anything that isn't an @include or a nested selector.

    ```scss
    .btn-green {
      background: green;
      font-weight: bold;
      // ...
    }
    ```

2. `@include` declarations

    Grouping `@include`s at the end makes it easier to read the entire selector.

    ```scss
    .btn-green {
      background: green;
      font-weight: bold;
      @include transition(background 0.5s ease);
      // ...
    }
    ```

3. Nested selectors

    Nested selectors, if necessary, go last, and nothing goes after them. Add whitespace between your rule declarations and nested selectors, as well as between adjacent nested selectors. Apply the same guidelines as above to your nested selectors.

    ```scss
    .btn {
      background: green;
      font-weight: bold;
      @include transition(background 0.5s ease);

      .icon {
        margin-right: 10px;
      }
    }
    ```

### **Avoid**: Browser-specific prefixes

Do not include browser prefix such as `-webkit-`, `-moz-`, `-ms-` and `-o-` when defining properties. Only include the W3C standard property. Prefixes should be handled by the compiler only.

### **Avoid**: !important

Under (almost!) no circumstances should the `!important` qualifier be used.

## Colors

**Use defined variables or color mixins!** Avoid defining color codes directly unless they are unique to that element across the project (which is very rare). However, white `#FFF` and black `#000` values should be written as such.

In the rare cases you must use HEX codes, use the 3 characters version when all channels have the same value (e.g. greyscale).

When defining color opacity, use the `rgba(x,x,x,x)` syntax when using greyscale values and `rgba($var, .7)`:

```scss
.content {
  background-color: rgba(0,0,0,.75);
}

.content {
  background-color: rgba($color-variable, .4);
}
```

### Material Design Mixin

Playster is using the [Material Design color palette](https://www.materialui.co/colors) across the site. A mixin is available when defining colors:

```scss
.content {
  color: mc('orange', '500');
  background-color: mc('teal', '800');
}
```

The mixin should be used when defining colors and greyscale (with the exception of black and white).

## Comments

- Prefer line comments (// in SCSS) to block comments.
- Prefer comments on their own line. Avoid end-of-line comments.
- Write detailed comments only for code that isn't self-documenting:
  - Uses of z-index
  - Complex media queries

## Media Queries

When defining media queries for responsive layouts, values should **always** be variables:

```scss
/* BAD */
@media screen and (max-width: 25rem) { }
@media screen and (min-width: 25rem) and (max-width: 50rem) { }

/* GOOD */
@media screen and (max-width: $media-mobile) { }
@media screen and (min-width: $media-mobile) and (max-width: $media-tablet) { }
```

## Units

Different units should be used depending on the property. In general, the **rem** is preferable.

- **border-width**: px
- **margin / padding**: rem, em or px
- **font-size:** rem or em
- **elements > min-,max-,width / min-,max-,height**: rem, em or px
- **media queries > min-width / max-width**: rem or em *(identical behavior)*

> Pixel-based units should be avoided for media queries because of inconsistent behaviors on Safari.
