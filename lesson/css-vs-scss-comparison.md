# CSS vs SCSS Comparison

This document shows the key differences between writing styles in regular CSS vs SCSS.

## 🎯 Variables

### CSS Approach (Repetitive)
```css
.container {
  background: white;
  border-radius: 0.5rem;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
}

.weather {
  background: white;
  border-radius: 0.5rem;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
}

button {
  background-color: #e67e22;
  border-radius: 0.5rem;
}
```

### SCSS Approach (DRY - Don't Repeat Yourself)
```scss
$border-radius: 0.5rem;
$box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
$primary-color: #e67e22;

.container {
  background: white;
  border-radius: $border-radius;
  box-shadow: $box-shadow;
}

.weather {
  background: white;
  border-radius: $border-radius;
  box-shadow: $box-shadow;
}

button {
  background-color: $primary-color;
  border-radius: $border-radius;
}
```

## 🏗️ Nesting

### CSS Approach (Flat Structure)
```css
.container {
  background: white;
  padding: 2rem;
}

.container h1 {
  margin-bottom: 1rem;
  color: #e67e22;
}

.container .input-group {
  margin-bottom: 1rem;
}

.container button {
  background-color: #e67e22;
}
```

### SCSS Approach (Hierarchical)
```scss
.container {
  background: white;
  padding: 2rem;
  
  h1 {
    margin-bottom: 1rem;
    color: $primary-color;
  }
  
  .input-group {
    margin-bottom: 1rem;
  }
  
  button {
    background-color: $primary-color;
  }
}
```

## 🔧 Mixins

### CSS Approach (Copy-Paste)
```css
.primary-button {
  padding: 0.75rem 1.5rem;
  background-color: #e67e22;
  color: white;
  border: none;
  border-radius: 0.5rem;
  cursor: pointer;
  transition: all 0.3s ease;
}

.secondary-button {
  padding: 0.75rem 1.5rem;
  background-color: #f39c12;
  color: white;
  border: none;
  border-radius: 0.5rem;
  cursor: pointer;
  transition: all 0.3s ease;
}
```

### SCSS Approach (Reusable)
```scss
@mixin button-style($bg-color: $primary-color, $text-color: white) {
  padding: 0.75rem 1.5rem;
  background-color: $bg-color;
  color: $text-color;
  border: none;
  border-radius: $border-radius;
  cursor: pointer;
  transition: all 0.3s ease;
}

.primary-button {
  @include button-style();
}

.secondary-button {
  @include button-style($secondary-color);
}
```

## 🎨 Functions

### CSS Approach (Manual Calculations)
```css
.weather {
  border-left: 4px solid #e67e22;
}

.weather .description {
  color: #f39c12; /* Manually calculated lighter color */
}

.weather .location {
  color: #d35400; /* Manually calculated darker color */
}
```

### SCSS Approach (Dynamic)
```scss
.weather {
  border-left: 4px solid $primary-color;
  
  .description {
    color: lighten($primary-color, 20%);
  }
  
  .location {
    color: darken($primary-color, 10%);
  }
}
```

## 📱 Media Queries

### CSS Approach (Separate Rules)
```css
.container {
  width: 320px;
}

@media (max-width: 480px) {
  .container {
    width: 90%;
  }
}

.weather {
  padding: 1.5rem;
}

@media (max-width: 480px) {
  .weather {
    padding: 1rem;
  }
}
```

### SCSS Approach (Nested)
```scss
.container {
  width: 320px;
  
  @media (max-width: 480px) {
    width: 90%;
  }
}

.weather {
  padding: 1.5rem;
  
  @media (max-width: 480px) {
    padding: 1rem;
  }
}
```

## 🎯 Benefits of SCSS

1. **Maintainability**: Change variables once, affects everywhere
2. **Readability**: Nested structure matches HTML hierarchy
3. **Reusability**: Mixins reduce code duplication
4. **Dynamic**: Functions calculate colors and values automatically
5. **Organization**: Partials split code into logical files

## 🚀 Getting Started

1. Install SCSS: `npm install sass`
2. Compile: `sass style.scss style.css`
3. Watch for changes: `sass --watch style.scss style.css`

## 💡 Pro Tips

- Use variables for colors, spacing, and typography
- Create mixins for common patterns (buttons, cards, forms)
- Nest related styles together
- Use SCSS functions for dynamic styling
- Split large files into partials with `@import` 