# 🎨 SCSS Fundamentals: A Complete Guide

## What is SCSS?

**SCSS (Sass)** is a **CSS preprocessor** that extends CSS with powerful features. Think of it as "CSS with superpowers" that helps you write cleaner, more maintainable stylesheets.

### Why Use SCSS?
- **Variables**: Store colors, fonts, and values for reuse
- **Nesting**: Write cleaner, more organized code
- **Mixins**: Reusable code blocks
- **Functions**: Dynamic calculations and color manipulation
- **Partials**: Split code into smaller files

---

## 🎯 1. Variables

Variables let you store values and reuse them throughout your stylesheet.

### Basic Variables
```scss
// Define variables
$primary-color: #e67e22;
$font-family: 'Segoe UI', sans-serif;
$border-radius: 0.5rem;

// Use variables
.button {
  background-color: $primary-color;
  font-family: $font-family;
  border-radius: $border-radius;
}
```

### Variable Types
```scss
// Colors
$primary: #e67e22;
$secondary: #f39c12;

// Numbers
$spacing: 1rem;
$border-width: 2px;

// Strings
$font-stack: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;

// Lists
$shadows: 0 2px 4px rgba(0, 0, 0, 0.1), 0 4px 8px rgba(0, 0, 0, 0.1);

// Maps (advanced)
$breakpoints: (
  small: 480px,
  medium: 768px,
  large: 1024px
);
```

---

## 🏗️ 2. Nesting

Nesting allows you to write styles that match your HTML structure.

### Basic Nesting
```scss
.container {
  background: white;
  padding: 2rem;
  
  // Nested selector
  h1 {
    color: $primary-color;
    font-size: 2rem;
    
    // Further nesting
    span {
      font-weight: bold;
    }
  }
  
  .button {
    background: $primary-color;
    
    &:hover {
      background: darken($primary-color, 10%);
    }
  }
}
```

### The `&` Parent Selector
The `&` symbol refers to the parent selector:

```scss
.button {
  background: $primary-color;
  
  &:hover {
    background: darken($primary-color, 10%);
  }
  
  &.large {
    padding: 1rem 2rem;
  }
  
  &--secondary {
    background: $secondary-color;
  }
}
```

This compiles to:
```css
.button { background: #e67e22; }
.button:hover { background: #d35400; }
.button.large { padding: 1rem 2rem; }
.button--secondary { background: #f39c12; }
```

---

## 🔧 3. Mixins

Mixins are reusable blocks of code that can accept parameters.

### Basic Mixin
```scss
@mixin button-style {
  padding: 0.75rem 1.5rem;
  border: none;
  border-radius: 0.5rem;
  cursor: pointer;
  transition: all 0.3s ease;
}

.primary-button {
  @include button-style;
  background: $primary-color;
  color: white;
}
```

### Mixins with Parameters
```scss
@mixin button-style($bg-color, $text-color: white) {
  padding: 0.75rem 1.5rem;
  background-color: $bg-color;
  color: $text-color;
  border: none;
  border-radius: 0.5rem;
  cursor: pointer;
  transition: all 0.3s ease;
}

.primary-button {
  @include button-style($primary-color);
}

.secondary-button {
  @include button-style($secondary-color, black);
}
```

### Mixins with Default Values
```scss
@mixin card($bg-color: white, $shadow: 0 2px 4px rgba(0,0,0,0.1)) {
  background: $bg-color;
  border-radius: 0.5rem;
  box-shadow: $shadow;
  padding: 1rem;
}

.weather-card {
  @include card;
}

.weather-card-dark {
  @include card(#333, 0 4px 8px rgba(0,0,0,0.3));
}
```

---

## 🎨 4. SCSS Functions

SCSS provides built-in functions for color manipulation and calculations.

### Color Functions
```scss
$primary: #e67e22;

.element {
  // Lighten a color by 20%
  color: lighten($primary, 20%);
  
  // Darken a color by 10%
  background: darken($primary, 10%);
  
  // Adjust saturation
  border-color: saturate($primary, 20%);
  
  // Mix two colors
  background: mix($primary, white, 50%);
  
  // Get complementary color
  color: complement($primary);
}
```

### Math Functions
```scss
.container {
  width: 100% - 2rem;  // 100% minus 2rem
  height: 50vh + 100px; // 50vh plus 100px
  margin: 1rem * 2;     // 2rem
  padding: 1rem / 2;    // 0.5rem
}
```

### String Functions
```scss
$font-family: 'Segoe UI';

.text {
  font-family: quote($font-family); // Adds quotes
  content: unquote('Hello');        // Removes quotes
}
```

---

## 📁 5. Partials and Imports

Partials help you organize code into smaller, manageable files.

### Creating Partials
Create files that start with `_` (underscore):

```
styles/
├── _variables.scss
├── _mixins.scss
├── _buttons.scss
└── main.scss
```

### _variables.scss
```scss
// Colors
$primary-color: #e67e22;
$secondary-color: #f39c12;

// Spacing
$spacing-sm: 0.5rem;
$spacing-md: 1rem;
$spacing-lg: 1.5rem;
```

### _mixins.scss
```scss
@mixin button-style($bg-color: $primary-color) {
  padding: 0.75rem 1.5rem;
  background-color: $bg-color;
  border: none;
  border-radius: 0.5rem;
}
```

### main.scss
```scss
// Import partials
@import 'variables';
@import 'mixins';
@import 'buttons';

// Your main styles
.container {
  @include button-style();
}
```

---

## 📱 6. Media Queries with Nesting

SCSS makes media queries more readable with nesting:

```scss
.container {
  width: 320px;
  padding: 2rem;
  
  @media (max-width: 768px) {
    width: 90%;
    padding: 1rem;
  }
  
  @media (max-width: 480px) {
    width: 95%;
    padding: 0.5rem;
  }
}
```

### Using Variables for Breakpoints
```scss
$breakpoint-tablet: 768px;
$breakpoint-mobile: 480px;

.container {
  width: 320px;
  
  @media (max-width: $breakpoint-tablet) {
    width: 90%;
  }
  
  @media (max-width: $breakpoint-mobile) {
    width: 95%;
  }
}
```

---

## 🎬 7. Interpolation

Use `#{}` to insert variables into property names or selectors:

```scss
$side: 'top';
$property: 'margin';

.element {
  #{$property}-#{$side}: 1rem;
  border-#{$side}: 2px solid black;
}
```

Compiles to:
```css
.element {
  margin-top: 1rem;
  border-top: 2px solid black;
}
```

---

## 🔄 8. Control Directives

### @if, @else if, @else
```scss
@mixin theme-colors($theme: 'light') {
  @if $theme == 'dark' {
    background: #333;
    color: white;
  } @else if $theme == 'blue' {
    background: #0066cc;
    color: white;
  } @else {
    background: white;
    color: black;
  }
}

.light-theme {
  @include theme-colors();
}

.dark-theme {
  @include theme-colors('dark');
}
```

### @for Loops
```scss
@for $i from 1 through 4 {
  .col-#{$i} {
    width: percentage($i / 4);
  }
}
```

Compiles to:
```css
.col-1 { width: 25%; }
.col-2 { width: 50%; }
.col-3 { width: 75%; }
.col-4 { width: 100%; }
```

### @each Loops
```scss
$colors: red, green, blue;

@each $color in $colors {
  .bg-#{$color} {
    background-color: $color;
  }
}
```

---

## 🚀 9. Compiling SCSS

### Using Sass CLI
```bash
# Install Sass
npm install -g sass

# Compile once
sass style.scss style.css

# Watch for changes
sass --watch style.scss style.css

# Compressed output
sass style.scss style.css --style compressed
```

### Using npm scripts
```json
{
  "scripts": {
    "sass": "sass style.scss style.css",
    "sass:watch": "sass --watch style.scss style.css",
    "sass:build": "sass style.scss style.css --style compressed"
  }
}
```

---

## 💡 10. Best Practices

### 1. Use Meaningful Variable Names
```scss
// Good
$primary-color: #e67e22;
$border-radius-large: 1rem;

// Bad
$color1: #e67e22;
$br: 1rem;
```

### 2. Organize with Partials
```scss
// main.scss
@import 'variables';
@import 'mixins';
@import 'base';
@import 'components';
@import 'utilities';
```

### 3. Use Mixins for Repeated Patterns
```scss
@mixin flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
}

.centered {
  @include flex-center;
}
```

### 4. Keep Nesting Shallow
```scss
// Good (max 3 levels)
.container {
  .header {
    .title {
      color: $primary;
    }
  }
}

// Bad (too deep)
.container {
  .header {
    .nav {
      .menu {
        .item {
          .link {
            color: $primary;
          }
        }
      }
    }
  }
}
```

### 5. Use Functions for Dynamic Values
```scss
// Good
.element {
  color: lighten($primary, 20%);
  border-color: darken($primary, 10%);
}

// Bad (hard to maintain)
.element {
  color: #f39c12; // Manually calculated
  border-color: #d35400; // Manually calculated
}
```

---

## 🎯 Practice Exercises

### Exercise 1: Create a Button System
```scss
// Create variables for your design system
$primary: #e67e22;
$secondary: #f39c12;
$success: #27ae60;
$danger: #e74c3c;

// Create a button mixin
@mixin button($bg-color, $text-color: white) {
  padding: 0.75rem 1.5rem;
  background: $bg-color;
  color: $text-color;
  border: none;
  border-radius: 0.5rem;
  cursor: pointer;
  transition: all 0.3s ease;
  
  &:hover {
    background: darken($bg-color, 10%);
  }
}

// Create button classes
.btn-primary { @include button($primary); }
.btn-secondary { @include button($secondary); }
.btn-success { @include button($success); }
.btn-danger { @include button($danger); }
```

### Exercise 2: Create a Card Component
```scss
@mixin card($bg-color: white, $shadow: 0 2px 4px rgba(0,0,0,0.1)) {
  background: $bg-color;
  border-radius: 0.5rem;
  box-shadow: $shadow;
  padding: 1.5rem;
  margin: 1rem 0;
}

.card {
  @include card();
}

.card-elevated {
  @include card(white, 0 8px 16px rgba(0,0,0,0.2));
}
```

---

## 🎉 You're Ready!

Now you have a solid foundation in SCSS! You understand:

- ✅ Variables for reusable values
- ✅ Nesting for cleaner code structure
- ✅ Mixins for reusable code blocks
- ✅ Functions for dynamic styling
- ✅ Partials for code organization
- ✅ Best practices for maintainable code

You're ready to tackle the Weather App lab and create beautiful, maintainable styles with SCSS! 🌦️ 