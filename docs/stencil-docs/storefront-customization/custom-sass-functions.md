# Custom Sass Functions

<div class="otp" id="no-index">

### On this page
- [Custom Sass functions](#custom-sass-functions)
- [Compiling custom Sass files](#compiling-custom-sass-files)

</div>

## Custom Sass functions

| Custom Sass Function  | Description  |
|-|-|
| stencilColor  | `stencilColor` accepts (as a string) the key name of a color that you have defined in <span class="fn">config.json</span> as editable. It returns the color’s hexadecimal value.|
| stencilFontFamily  | `stencilFontFamily` accepts (as a string) the name of a font key that you have defined in config.json. It returns the corresponding font-family value, also as a string. For a key named "headings-font" and defined as Google Open Sans, `stencilFontFamily` would return a value like this to Sass variables: `$headings-‐font-‐family: 'Open Sans';` (the example's name and definition in config.json are both arbitrary). Your Sass stylesheet must call stencilFontFamily for each <span class="fn">config.json</span> font key whose font-family value you want to provide to Sass variables. You would call the function in the following format (again assuming a key arbitrarily named "headings-font"): `$headings-font-family: stencilFontFamily("headings-font");`. |
| stencilFontWeight  | `stencilFontWeight` accepts (as a string) the key name of a font that you have defined in config.json. It returns (as an integer) the corresponding font-weight value. For a key arbitrarily named "headings-font" and defined as 700, it would return a value like this to Sass variables: `$headings-‐font-‐weight: 700;` Your Sass stylesheet may optionally call stencilFontWeight for each <span class="fn">config.json</span> font key whose weight value you want to provide to Sass variables. You would call the function in the following format: `$headings-font-weight: stencilFontWeight("headings-font");`.  |
| stencilNumber  | `stencilNumber` accepts (as a string) a key name that you have defined in config.json as editable. It also accepts (also as a string) an optional second parameter to define the unit. (This second parameter’s value defaults to `px`.) It returns the corresponding numeric value, postfixed with the defined unit. You can use this function with arithmetical operators. For example, assume that your config.json contains a `font-size` value of `3`. The following statement would evaluate to `9rem`. `stencilNumber("font-size", "rem") * 3`. |
| stencilString  | `stencilString` accepts (as a string) a key name that you have defined in <span class="fn">config.json</span> as editable. It returns (also as a string) the key’s value. This function is used for purposes like defining font family names, or defining paths to images.  |
| stencilImage  | `stencilImage` accepts (as a string) a key name for an image url that you have defined in <span class="fn">config.json</span>. It also accepts (as a string) the key name for the image size that you have defined in <span class="fn">config.json</span>. It returns the string value of the image URL and the size.  |

<div class="HubBlock--callout">
<div class="CalloutBlock--info">
<div class="HubBlock-content">
  
<!-- theme: info -->

### NOTE
> The [config.json](https://developer.bigcommerce.com/stencil-docs/storefront-customization/directory-structure#configjson) file is the main configuration file for Stencil themes and exists in the theme root directory. Use Stencil CLI to edit this file.

</div>
</div>
</div>


## Compiling custom Sass files

If you want to add your own custom Sass files to a theme, initiate auto-compilation of those files by including the associated tag in your HTML markup. Doing this is useful for isolating your custom styles. Cornerstone's Sass file is named <span class="fp">/assets/scss/theme.scss</span>.

To add a custom Sass file, place it at this path location, using an arbitrary filename prefix as shown:

<span class="fp">/assets/scss/foobar.scss</span>

Next, import the custom file into `theme.scss`.

```scss
@import "foobar";
```

Finally, ensure `{{stylesheet '/assets/css/theme.scss'}}` is located in `templates/layout/base.html/`.

```handlebars
<head>
<!-- ... -->
{{stylesheet '/assets/css/theme.scss'}}
<!-- ... -->
</head>
```

While `stencil start` is running, it will recompile your custom Sass files to the specified <span class="fp">`{theme-name}/assets/css/theme.scss`</span> file (note that this object file’s name is always the same, and is independent of your custom Sass file's names).

<div class="HubBlock--callout">
<div class="CalloutBlock--warning">
<div class="HubBlock-content">

<!-- theme: warning -->

### Before you customize
> The Stencil framework is designed to support your incorporation of custom Sass files/frameworks. However, BigCommerce does not offer technical assistance on substitutions for, or customized versions of, Stencil’s default dependencies.

</div>
</div>
</div>
