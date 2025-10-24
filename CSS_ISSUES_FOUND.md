# CSS Issues Found in Demo Project

## 1. Inline Styles (Multiple Violations)
- **Location**: index.html and about.html
- **Issue**: Heavy use of inline styles throughout HTML files
- **Examples**:
  - Header h1: `style="color: #ff0000; font-size: 32px; margin: 10px;"`
  - Navigation links: `style="color: blue; padding: 5px;"`
  - Hero section: `style="background-color: #ccc; padding: 50px; text-align: center;"`
  - Form inputs: Multiple inline styles
- **Impact**: Makes maintenance difficult, violates separation of concerns

## 2. Unused CSS File
- **Location**: styles/unused.css
- **Issue**: Entire stylesheet is unused and should be removed
- **Classes**: old-container, old-grid, legacy-button, deprecated-layout, unused-class-*

## 3. Duplicate and Conflicting Styles
- **Location**: styles/main.css and styles/components.css
- **Issues**:
  - `.btn` defined twice with different padding values
  - `.card` defined twice with different padding
  - `.modal` and `.modal-content` duplicated across files
  - Random unused classes: `.old-class`, `.deprecated`

## 4. Inconsistent Color Schemes
- **Issue**: Multiple color values used inconsistently
  - Red: #ff0000, red
  - Blue: blue, #007bff
  - Green: green
  - Gray: #ccc, #333, #666, #555, #222, #ddd
- **No color variable system**

## 5. Inconsistent Spacing
- **Padding values**: 5px, 8px, 10px, 15px, 20px, 30px, 40px, 50px, 60px (no system)
- **Margin values**: 5px, 10px, 15px, 20px, 25px, 40px, 50px (no system)

## 6. Non-Responsive Layout
- **Issues**:
  - Fixed width container: `width: 1200px` with no responsive breakpoints
  - Cards using `float: left` instead of flexbox/grid
  - No media queries for mobile/tablet
  - Fixed widths on cards and form elements

## 7. Overlapping and Misaligned Elements
- **Issues**:
  - Cards with float layout cause alignment issues
  - Modal content not properly centered
  - Form inputs have inconsistent widths

## 8. No CSS Naming Convention
- **Issue**: Mix of naming styles, no BEM or consistent methodology
- **Examples**: 
  - `.main-content` (kebab-case)
  - `.contact-form` (kebab-case)
  - But no consistent pattern or component naming

## 9. Accessibility Issues
- **Missing focus states** for interactive elements
- **No clear visual hierarchy**
- **Color contrast** may be insufficient in some areas

## 10. Browser Compatibility
- **No vendor prefixes** where needed
- **Float-based layouts** are outdated
- **No fallbacks** for modern CSS features
