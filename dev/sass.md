<img src="/uploads/logos/sass-logo.png" align="right" />

# SASS
##### Best practices and rules for the SASS (Syntactically Awesome StyleSheets) language

Standards and rules to follow are defined per team / project.

- [Code Style](#code-style)
- [Categorizing CSS Rules](#categorizing-css-rules)
- [Selectors](#selectors)
- [States](#states)

## Code Style

The style guide presented here is a mix of SMACSS and BEM best practices.

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

### **Avoid**: ID selectors.

IDs should not be used for CSS at all.

```scss
/* BAD */
#ad-placement { }

/* GOOD */
.ad-placement { }
```

### **Avoid**: Element selectors.

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

Nesting should be limited to at most 3 levels deep.

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

States are classes that changes the behavior / look of another class, such as active, featured, shown, hidden, position, etc.

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
