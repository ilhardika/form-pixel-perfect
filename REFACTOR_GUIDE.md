# CSS Refactor Guide

## Overview

CSS telah di-refactor untuk mengurangi duplikasi code dan meningkatkan reusability dengan menggunakan utility classes dan CSS custom properties.

## Perubahan Utama

### 1. CSS Custom Properties (CSS Variables)

```css
:root {
  --color-white: #fff;
  --color-black: #000;
  --color-bg-default: #bfbfbf;
  --color-bg-secondary: #c4c4c4;
  --color-bg-tertiary: #e6e6e6;
  --color-bg-light: #f8f8f8;
  --color-border: #000;
}
```

### 2. Background Color Utilities

Menggantikan hardcoded background colors:

```css
.bg-default {
  background-color: var(--color-bg-default);
} /* #bfbfbf */
.bg-secondary {
  background-color: var(--color-bg-secondary);
} /* #c4c4c4 */
.bg-tertiary {
  background-color: var(--color-bg-tertiary);
} /* #e6e6e6 */
.bg-light {
  background-color: var(--color-bg-light);
} /* #f8f8f8 */
.bg-white {
  background-color: var(--color-white);
} /* #fff */
```

### 3. Input Size Utilities

Menggantikan classes yang terlalu spesifik:

```css
.input-sm {
  width: 40px;
} /* Menggantikan .hoa-input */
.input-md {
  width: 110px;
} /* Menggantikan .describe-input */
.input-lg {
  width: 140px;
} /* Default text-input size */
.input-xl {
  width: 95%;
  max-width: 400px;
} /* Menggantikan .full-width */
```

### 4. Section Label Refactor

**Before:**

```css
.vertical-label {
  /* duplikasi definisi */
}
.subject-label {
  background-color: #bfbfbf;
}
.assignment-label {
  background-color: #c4c4c4;
}
.site-label {
  background-color: #e6e6e6;
}
```

**After:**

```css
.section-label {
  /* base styles */
}
/* Gunakan utility classes untuk background */
```

**HTML Before:**

```html
<div class="vertical-label subject-label">
  <div class="vertical-label assignment-label">
    <div class="vertical-label site-label"></div>
  </div>
</div>
```

**HTML After:**

```html
<div class="section-label bg-default">
  <div class="section-label bg-secondary">
    <div class="section-label bg-tertiary"></div>
  </div>
</div>
```

### 5. Label Text Utilities

**Before:**

```css
.market-label-text {
  /* specific untuk market saja */
}
```

**After:**

```css
.label-text {
  /* general untuk semua label text */
}
```

## Migration Guide

### Untuk Developer:

1. **Ganti vertical-label classes:**

   ```html
   <!-- Old -->
   <div class="vertical-label subject-label">
     <!-- New -->
     <div class="section-label bg-default"></div>
   </div>
   ```

2. **Ganti market-label-text:**

   ```html
   <!-- Old -->
   <span class="market-label-text">Location:</span>

   <!-- New -->
   <span class="label-text">Location:</span>
   ```

3. **Gunakan input size utilities:**

   ```html
   <!-- Old -->
   <input class="text-input full-width" />
   <input class="text-input describe-input" />
   <input class="text-input hoa-input" />

   <!-- New -->
   <input class="input-base input-xl" />
   <input class="input-base input-md" />
   <input class="input-base input-sm" />
   ```

## Benefits dari Refactor

### 1. Reduced Code Duplication

- Eliminated duplicate .vertical-label definitions
- Consolidated color values ke CSS variables
- Unified label text styling

### 2. Better Maintainability

- Central color management dengan CSS variables
- Consistent naming conventions
- Easier to update colors globally

### 3. Improved Reusability

- Utility classes dapat digunakan untuk komponen lain
- Input size utilities fleksibel untuk berbagai use cases
- Background utilities dapat dikombinasikan dengan class lain

### 4. Better Developer Experience

- Class names lebih semantic dan mudah dipahami
- Predictable naming patterns
- Self-documenting code dengan utility classes

## Legacy Support

Classes lama masih didukung untuk backward compatibility:

- `.market-label-text` → menggunakan `.label-text`
- `.text-input.full-width` → gunakan `.input-base.input-xl`
- `.subject-label`, `.assignment-label`, `.site-label` → masih berfungsi

## Future Improvements

1. Tambahkan spacing utilities (margin, padding)
2. Font size utilities
3. Border utilities
4. Flexbox utilities
5. Grid utilities

## File Changes

- `style.css`: Main CSS refactor
- `page1.html`: Updated class names untuk menggunakan utilities
- `REFACTOR_GUIDE.md`: Documentation (file ini)
