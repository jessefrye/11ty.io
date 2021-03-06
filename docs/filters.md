---
subtitle: Filters
menuSectionName: docs-filters
relatedKey: filters
relatedTitle: Template Filters
tags:
  - docs-config
  - related-shortcodes
  - related-nunjucks
  - related-liquid
  - related-handlebars
---
# Filters

Various template engines can be extended with custom filters to modify content. Here’s an example:

{% raw %}
```html
<!-- Nunjucks and Liquid use the same syntax -->
<h1>{{ name | makeUppercase }}</h1>
```
{% endraw %}

This can be added using the [Configuration API](/docs/config/#using-the-configuration-api). Here are a few examples:

```js
module.exports = function(eleventyConfig) {
  // Liquid Filter
  eleventyConfig.addLiquidFilter("makeUppercase", function(value) { … });
  
  // Nunjucks Filter
  eleventyConfig.addNunjucksFilter("makeUppercase", function(value) { … });
  
  // Handlebars Filter
  eleventyConfig.addHandlebarsHelper("makeUppercase", function(value) { … });
  
  // or, use a Universal filter (an alias for all of the above)
  eleventyConfig.addFilter("makeUppercase", function(value) { … });
};
```

Read more about filters on the individual Template Language documentation pages:

{% templatelangs templatetypes, page, ["njk", "liquid", "hbs"], "#filters" %}

## Universal Filters

Universal filters can be added in a single place and are available to multiple template engines, simultaneously. This is currently supported in Nunjucks, Liquid, and Handlebars.

```js
module.exports = function(eleventyConfig) {
  // Universal filters (Adds to Liquid, Nunjucks, and Handlebars)
  eleventyConfig.addFilter("myFilter", function(value) {
    return value;
  });
};
```

### Eleventy Provided Universal Filters

We also provide a few universal filters, built-in:

* [`url`](/docs/filters/url/): normalize absolute paths in your content, allows easily changing deploy subdirectories for your project. [Read more →](/docs/filters/url/)
* [`slug`](/docs/filters/slug/): `"My string"` to `"my-string"` for permalinks. [Read more →](/docs/filters/slug/)

