<img src="/uploads/logos/sass-logo.png" align="right" />

# SASS
##### Best practices and rules for the SASS (Syntactically Awesome StyleSheets) language

Standards and rules to follow are defined per team / project.

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

### Layout

The layout folder should contains styles that are common to all pages on the site. Usually the header, footer, sidebar, etc. files.

- Header
- Footer
- Navigation
- Sidebar
- Containers

### Module

The module folder should contains styles that apply to specific components, modules, pages, etc.

## Selectors

### **Avoid**: ID selectors.

```scss
/* DON'T */
#ad-placement { }

/* DO */
.ad-placement { }
```

### **Avoid**: Element selectors.

Using plain element selectors simply add complexity to the project as it grows.

```scss
/* DON'T */
.folder > span { }
.folder span:nth-child(2) { }

/* DO */
.folder { }
.folder-span { }
.folder-span-secondary { }
```

### **Avoid**: Specificity

Do not attach an element to a class or use immediate child operators (unless absolutely necessary). They add pointless complexity, makes it harder to override styles and decrease browser performance when applying styles.

```scss
/* DON'T */
div.content > img.thumbnail { }

/* DO */
.content .thumbnail { }
```
