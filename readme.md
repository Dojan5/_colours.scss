# _colours.scss

This SCSS file, `_colours.scss`, is a configuration file for defining and manipulating theme colors in your SCSS projects. It provides a flexible system for generating color variables and utility classes that can be used throughout your stylesheets.

This project was inspired by [this article](https://developer.mozilla.org/en-US/blog/color-palettes-css-color-mix/) written by Michelle Barker at developer.mozilla.org, where she essentially explains how to do all this manually, goes into detail on how it works, as well as touches on the differences between the different kinds of colour spaces used when mixing colours using the CSS `color-mix` function.

## Features

1. **Theme Colors**: Define your theme colors using the `$theme-colors` map. These colors will be used as the base for generating lighter and darker shades, as well as warm and cool variants.

2. **Shade Generation**: The `$steps` and `$increment` variables control the generation of lighter and darker shades of your theme colors. The `$light` and `$dark` variables define the colors used for generating these shades.

3. **Color Space**: The `$color-space` variable allows you to specify the color space used for blending. Examples include `oklch`, `oklab`, and `srgb`.

4. **Temperature Variants**: The `$warm` and `$cool` variables are used to create warm and cool variants of your theme colors.

5. **Color Variables Generation**: The `generate-color-variables` mixin generates CSS custom properties (variables) for your theme colors, their shades, and temperature variants.

6. **Utility Classes Generation**: The `generate-utility-classes` mixin generates BEM-adherent utility classes for applying these colors and their variants to your elements.

## Usage

To use this file, import it into your main SCSS file and call the `generate-color-variables` and `generate-utility-classes` mixins. You can then use the generated CSS custom properties and utility classes in your stylesheets.

```scss
@import '_colours.scss';

:root {
    @include generate-color-variables;
}

@include generate-utility-classes;
```

Each mixin takes boolean arguments for `lightness` and `temperature`, allowing you to limit the output if you're interested in one but not the other. 

To then make use of the utility classes, you just add the class `bg-{colour}` followed by any modifiers. For example.

```html
<div class="card bg-primary warm"></div>
<h1 class="text-secondary--dark"></div>
<section class="border-tertiary--light cold--20"></section>
```

## Preview
Given default settings, this is the output.

![Preview screenshot](/img/default-preview.png?raw=true)