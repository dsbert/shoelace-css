---
layout: default.html
title: Customizing
description: Learn how to customize Shoelace.css with CSS variables.
---

## Customizing

You can customize Shoelace without editing core files or using a preprocessor. To add customizations, simply override one or more of the variables found in the `:root` block of [`shoelace.css`](../source/css/shoelace.css).

For example, you can customize the default text color, background color, and the primary color by adding this to your stylesheet:

```css
:root {
  --body-color: white;
  --body-bg-color: black;
  --state-primary: #09d;
}
```

You don’t need to include all of the variables. You only need to override the ones you actually want to customize.

Additional variables can be found in the `:root` block of each component’s stylesheet. For example, to customize alerts, refer to the top of [`alerts.css`](https://github.com/claviska/shoelace-css/blob/master/source/css/alerts.css) for a list of variables.

### Using Variables

You can use any of Shoelace’s variables in your own stylesheet. This makes it easy to reuse values without hardcoding them. It also provides a foundation for extending Shoelace with your own [custom components](#creating-custom-components).

```css
.your-selector {
  color: var(--state-danger);
}
```

If you’re not familiar with CSS variables, [this article](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_variables) will bring you up to speed. There’s also an [interactive demo](https://codepen.io/claviska/pen/NvGVYM?editors=1100) if you want to experiment.

### Creating Custom Components

You can create custom components to extend Shoelace’s functionality. Here’s what a component’s stylesheet looks like.

```css
/* Set default variables here. It's a good idea to base them off
   core variables when possible. This makes it easier to customize
   the library as a whole but still lets users change individual
   components.

   Never change or override core variables in your extension!
*/
:root {
  --accordion-bg-color: var(--component-bg-color);
  --accordion-border-color: var(--component-border-color);
  /* etc. */
}

/* Add your styles here. Create additional rules as needed. */
.accordion {

}

/* Always prefix your modifiers with the component name. */
.accordion-modifier {

}
```

Here are some best practices for creating custom components:

**Familiarize yourself with Shoelace’s naming conventions.** A custom accordion component, for example, would have a class name such as `accordion`, modifier classes such as `accordion-open`, and variable names that look like `--accordion-bg-color`. Try to follow similar patterns as much as possible.

**Define new variables when it makes sense to.** Take a look at how existing components are defined. Many use core variables instead of hardcoded properties as default values. This makes it easy for users to customize things quickly, but still provides enough flexibility to style individual components.

**Semantic markup is strongly encouraged.** Custom components should use the most appropriate elements and the minimal amount of markup required.

**Keep things together.** Each component should be in its own folder along with its stylesheets, scripts, and documentation. Components can use core variables, but they shouldn’t depend on other components’ styles or scripts to work. This makes it easier to add or remove components from your app without worrying about dependencies.
