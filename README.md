# LayoutPreview assets bootstrap

This is a collection of styles and options to help get you started.

### Documentation

[LayoutPreview documentation](https://docs.aptoma.com/dredition/setup-print/layoutpreview-setup).

["Getting started"-guide](https://docs.aptoma.com/dredition/setup-print/layoutpreview-setup/getting-started).

## CSS Specificity

CSS specificity determines which styles are applied when multiple rules target the same element. Understanding this concept is crucial for writing maintainable CSS. Learn more in the [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity).

## Fonts

LayoutPreview uses web fonts for accurate text rendering. Fonts must be:
- Properly licensed for web use
- Have correct weight class properties in the font file
- Converted to web formats (OTF)
- Defined using @font-face rules
- `normalizeFonts` must be set to `true` in `config.yml`

See the ["Fonts documentation"](https://docs.aptoma.com/dredition/setup/layoutpreview-setup/development-manual/7.-fonts) for detailed setup instructions.


## Overview

Base styles and settings reside in the `layout`, `themes`, and `utils` folders. These apply globally to all components and templates, and should maintain low selector specificity to avoid overriding component-specific styles.

## Tools

The `tools` directory contains reusable style packages that components can include as needed. Each package provides:

- Default styles
- Component options (defined in `options.yml`)
- Configurable CSS custom properties (namespaced as `--{module-name}--property`)
- A mixin matching the tool name for component application

## Style Hierarchy (from least to most specific)

### 1. Base styles

These use minimal class names to maintain low specificity, making them easy to override in component CSS.

### 2. Included styles from tools

**Found at the top of component CSS files.**

Each included tool applies default styles and provides configuration options through CSS custom properties.

### 3. Component-specific styles

**Located after @include statements.**

Components can define unique styles and override defaults using the scope `.alf-component.{component-name}`. This ensures component styles take precedence over base and included styles.

### 4. Component options from tools

Defined in `options.yml` in each of the tool folders, these options allow runtime style modifications through predefined class names (e.g., `.text-align-left`, `.text-align-center`).

These options have the highest specificity since they're included within the component's main selector (`.alf-component.{component-name}`), ensuring they override component-specific styles.
