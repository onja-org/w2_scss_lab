# SCSS Lab: Weather App Styling

Learn SCSS fundamentals by building and styling a weather application. You'll practice variables, nesting, mixins, functions, and partials while creating a beautiful, responsive interface.

![Weather App Preview](assets/Weatherapp_01.PNG)

## What You'll Learn

- **SCSS Variables**: Reusable design tokens for colors, spacing, and typography
- **Nesting**: Cleaner, organized CSS that matches HTML structure
- **Mixins**: Reusable code blocks to eliminate repetition
- **Functions**: Dynamic color manipulation and calculations
- **Partials**: Split styles into maintainable, modular files

## Repository Structure

```
w2_scss_lab/
├── README.md                    # This overview file
├── assets/
│   └── Weatherapp_01.PNG       # Weather app design reference
├── lab/                        # Lab workspace
│   ├── _mixins.scss            # Reusable SCSS mixins
│   ├── _variables.scss         # Design system variables
│   ├── app.js                  # Weather app functionality (provided)
│   ├── index.html              # HTML structure (to be created)
│   ├── package.json            # npm configuration with SCSS tools
│   ├── readme.md               # Detailed lab instructions
│   ├── style.css               # Compiled CSS output
│   ├── style.scss              # Main SCSS file (your focus)
│   ├── test-weather-lab.js     # Automated testing
│   └── weatherData.js          # Weather data handler (provided)
└── lesson/                     # Educational materials
    ├── css-vs-scss-comparison.md  # Side-by-side comparisons
    └── scss-lesson.md             # Complete SCSS tutorial
```

## Quick Start

### Setup Instructions

1. **Navigate to the lab directory:**
   ```bash
   cd lab/
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Start SCSS compilation in watch mode:**
   ```bash
   npm run sass:watch
   ```

4. **Open `index.html` in your browser to see your changes live**

### Available npm Scripts

- `npm run sass` - Compile SCSS to CSS once
- `npm run sass:watch` - Watch for changes and auto-compile
- `npm run sass:build` - Create compressed CSS for production
- `npm test` - Run the automated tests

## What You'll Build

You'll create a modern weather application interface featuring:

- **Responsive Design**: Mobile-first approach with SCSS media queries
- **Interactive Elements**: Styled input fields, buttons, and dropdowns
- **Dynamic Weather Display**: Beautiful weather information cards
- **Smooth Animations**: CSS transitions and keyframe animations
- **Modern UI**: Clean design using SCSS variables and mixins

## Learning Path

### 1. Start with Theory
- Read `lesson/scss-lesson.md` for comprehensive SCSS fundamentals
- Review `lesson/css-vs-scss-comparison.md` to see practical differences

### 2. Complete the Lab
- Follow the step-by-step instructions in `lab/readme.md`
- Build the HTML structure in `lab/index.html`
- Style with SCSS in `lab/style.scss`
- Organize code using `lab/_variables.scss` and `lab/_mixins.scss`

### 3. Test Your Knowledge
- Run `npm test` to validate your implementation
- Compare your CSS output with best practices

## Key SCSS Features Covered

### Variables
```scss
$primary-color: #e67e22;
$border-radius: 0.5rem;
$font-family: 'Segoe UI', sans-serif;
```

### Nesting
```scss
.container {
  background: white;
  
  h1 {
    color: $primary-color;
    
    span {
      font-weight: bold;
    }
  }
}
```

### Mixins
```scss
@mixin button-style($bg-color: $primary-color) {
  padding: 0.75rem 1.5rem;
  background: $bg-color;
  border: none;
  border-radius: $border-radius;
}
```

### Functions
```scss
.element {
  color: lighten($primary-color, 20%);
  background: darken($primary-color, 10%);
}
```

## Prerequisites Knowledge

- HTML5 semantic elements
- CSS fundamentals (selectors, properties, box model)
- Basic understanding of responsive design
- Command line basics

## Learning Outcomes

After completing this lab, you'll be able to:

- Convert existing CSS to SCSS for better maintainability
- Create a scalable design system using SCSS variables
- Write cleaner, more organized stylesheets with nesting
- Build reusable components with mixins
- Implement dynamic styling with SCSS functions
- Structure large stylesheets using partials and imports


## Ready to Start?

Head over to `lab/readme.md` for detailed step-by-step instructions, or dive into `lesson/scss-lesson.md` to master SCSS fundamentals first!

Happy coding! 🚀