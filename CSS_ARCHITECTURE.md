# CSS Architecture Documentation

## Overview
This project uses a modern, maintainable CSS architecture based on industry best practices.

## File Structure

```
styles/
├── main.css          # Base styles, layout, and page sections
└── components.css    # Reusable UI components
```

## Naming Convention: BEM

We use **BEM (Block Element Modifier)** methodology for all CSS classes:

### Block
A standalone component that is meaningful on its own.
```css
.header { }
.card { }
.modal { }
```

### Element
A part of a block that has no standalone meaning.
```css
.header__title { }
.card__description { }
.modal__content { }
```

### Modifier
A flag on a block or element that changes appearance or behavior.
```css
.btn--secondary { }
.btn--success { }
.modal--active { }
```

## CSS Variables (Custom Properties)

All theme values are defined as CSS variables in `:root`:

### Colors
```css
--color-primary: #007bff;
--color-primary-dark: #0056b3;
--color-secondary: #6c757d;
--color-success: #28a745;
--color-danger: #dc3545;
--color-text: #333333;
--color-text-light: #666666;
--color-bg: #ffffff;
--color-bg-light: #f5f5f5;
--color-border: #dddddd;
```

### Typography
```css
--font-family-base: Arial, Helvetica, sans-serif;
--font-size-base: 16px;
--font-size-sm: 14px;
--font-size-lg: 18px;
--font-size-xl: 24px;
--font-size-xxl: 32px;
--line-height-base: 1.6;
```

### Spacing Scale
```css
--spacing-xs: 8px;   /* Extra small */
--spacing-sm: 16px;  /* Small */
--spacing-md: 24px;  /* Medium */
--spacing-lg: 32px;  /* Large */
--spacing-xl: 48px;  /* Extra large */
```

### Layout
```css
--container-max-width: 1200px;
--border-radius: 4px;
--box-shadow: 0 2px 8px var(--color-shadow);
--transition: all 0.3s ease;
```

## Responsive Breakpoints

We use a mobile-first approach with three breakpoints:

```css
/* Base styles: Mobile (0-480px) */

@media (max-width: 768px) {
    /* Tablet adjustments */
}

@media (max-width: 480px) {
    /* Small mobile adjustments */
}
```

## Component Structure

### main.css
1. **CSS Variables** - Theme configuration
2. **Base Styles** - Reset and typography
3. **Layout Components** - Container, header, footer
4. **Section Components** - Hero, features, etc.
5. **Responsive Design** - Media queries

### components.css
1. **Button Component** - Primary interactive elements
2. **Card Component** - Content containers
3. **Modal Component** - Overlay dialogs
4. **Form Components** - Input elements
5. **Typography Components** - Headings
6. **Animations** - Keyframes
7. **Responsive Design** - Component-specific media queries

## How to Use

### Adding a New Component

1. **Choose a block name** (noun describing the component)
   ```css
   .sidebar { }
   ```

2. **Add elements** (with double underscore)
   ```css
   .sidebar__title { }
   .sidebar__content { }
   .sidebar__footer { }
   ```

3. **Add modifiers** if needed (with double dash)
   ```css
   .sidebar--dark { }
   .sidebar--collapsed { }
   ```

4. **Use CSS variables** for all theme values
   ```css
   .sidebar {
       background-color: var(--color-bg);
       padding: var(--spacing-md);
       border-radius: var(--border-radius);
   }
   ```

### Example: Creating a New Alert Component

```css
/* Block */
.alert {
    padding: var(--spacing-sm);
    border-radius: var(--border-radius);
    border: 1px solid var(--color-border);
}

/* Modifiers */
.alert--success {
    background-color: var(--color-success);
    color: var(--color-bg);
}

.alert--danger {
    background-color: var(--color-danger);
    color: var(--color-bg);
}

/* Elements */
.alert__title {
    font-size: var(--font-size-lg);
    margin-bottom: var(--spacing-xs);
}

.alert__message {
    font-size: var(--font-size-base);
}
```

HTML usage:
```html
<div class="alert alert--success">
    <h3 class="alert__title">Success!</h3>
    <p class="alert__message">Your changes have been saved.</p>
</div>
```

## Accessibility Guidelines

All interactive components must include:

1. **Focus states**
   ```css
   .btn:focus {
       outline: 2px solid var(--color-primary);
       outline-offset: 2px;
   }
   ```

2. **Hover states**
   ```css
   .btn:hover {
       background-color: var(--color-primary-dark);
   }
   ```

3. **Sufficient color contrast** (WCAG AA minimum)
   - Text on light background: Use `--color-text` (#333)
   - Text on dark background: Use `--color-bg` (#fff)

4. **Keyboard navigation support**
   - Always include `:focus` styles
   - Don't remove default focus indicators without replacement

## Best Practices

### DO ✅
- Use CSS variables for all theme values
- Follow BEM naming strictly
- Add comments for complex styles
- Use semantic HTML
- Include hover and focus states
- Test on multiple screen sizes
- Keep specificity low (single class)
- Group related styles together

### DON'T ❌
- Use inline styles
- Use !important (except for utilities)
- Use deep nesting (max 2 levels)
- Use IDs for styling
- Hardcode colors/spacing
- Use pixel values for fonts (use rem/em)
- Mix naming conventions
- Leave unused styles

## Theming

To change the site theme, simply update CSS variables:

```css
:root {
    /* Change primary color */
    --color-primary: #ff6600;
    --color-primary-dark: #cc5200;
    
    /* Change spacing scale */
    --spacing-xs: 4px;
    --spacing-sm: 8px;
    /* ... etc */
}
```

All components will automatically update!

## Browser Support

- Chrome (latest 2 versions)
- Firefox (latest 2 versions)
- Safari (latest 2 versions)
- Edge (latest 2 versions)

### Modern CSS Features Used
- CSS Grid (excellent support)
- Flexbox (excellent support)
- CSS Variables (IE11+ support)
- CSS Animations (excellent support)

## Performance Tips

1. **CSS is cacheable** - External stylesheets are cached by browsers
2. **No inline styles** - Reduces HTML size
3. **No duplicates** - Smaller file size
4. **Organized** - Easier compression
5. **Variables** - No duplication of values

## Maintenance Checklist

When adding new styles:
- [ ] Follow BEM naming convention
- [ ] Use CSS variables for theme values
- [ ] Add responsive styles if needed
- [ ] Include focus states for interactive elements
- [ ] Add comments for complex logic
- [ ] Test on mobile, tablet, desktop
- [ ] Verify keyboard navigation
- [ ] Check color contrast
- [ ] Remove any unused styles
- [ ] Update this documentation if needed

## Resources

- [BEM Methodology](http://getbem.com/)
- [CSS Variables (MDN)](https://developer.mozilla.org/en-US/docs/Web/CSS/--*)
- [CSS Grid Guide](https://css-tricks.com/snippets/css/complete-guide-grid/)
- [Flexbox Guide](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [WCAG Contrast Checker](https://webaim.org/resources/contrastchecker/)
