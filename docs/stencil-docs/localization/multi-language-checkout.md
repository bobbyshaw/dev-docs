# Multi-Language Checkout


<div class="otp" id="no-index">

### On this page
- [Multi-language setup](#multi-language-setup)
- [Browsing hidden translation keys](#browsing-hidden-translation-keys)
- [Adding your own translation values](#adding-your-own-translation-values)
- [Localized country and state names](#localized-country-and-state-names)
- [Limits on translation](#limits-on-translation)
- [Resources](#resources)

</div>

## Multi-language setup

Cornerstone's [Optimized Checkout](https://github.com/bigcommerce/cornerstone/blob/master/assets/scss/optimized-checkout.scss) SCSS file and [Order Confirmation](https://github.com/bigcommerce/cornerstone/blob/master/templates/pages/order-confirmation.html) HTML file both contain Handlebars `{{lang}}` statements. These `{{lang}}` statements facilitate translation by enabling automatic rendering of their parameters into the default storefront language defined in the control panel. Checkout has been pre-translated into English, French, German, Italian, Portugese, Spanish, Swedish, and Dutch. See [Resources](https://developer.bigcommerce.com/stencil-docs/localization/localizing-stores#resources) to download the supported language files. You can override the pre-translations by providing the xx.json file for the language you want to override.

The following example shows how to use the `{{lang}}` statement in the header of the [default checkout page](https://github.com/bigcommerce/cornerstone/blob/master/templates/pages/checkout.html): 

```html
{{#partial "head"}}

{{{ checkout.checkout_head }}}
{{{ stylesheet '/assets/css/optimized-checkout.scss' }}}
{{ getFontsCollection }}

<script type="text/javascript">
    window.language = {{{langJson 'optimized_checkout'}}};
</script>

{{{head.scripts}}}

{{/partial}}

{{#partial "page"}}
<header class="checkoutHeader optimizedCheckout-header">
    <div class="checkoutHeader-content">
        <h1 class="is-srOnly">{{lang 'checkout.title'}}</h1>
        <h2 class="checkoutHeader-heading">
            <a class="checkoutHeader-link" href="{{urls.home}}">
                {{#if checkout.header_image}}
                    <img alt="{{settings.store_logo.title}}" class="checkoutHeader-logo" id="logoImage" src="{{ checkout.header_image }}"/>
                {{ else }}
                    <span class="header-logo-text">{{settings.store_logo.title}}</span>
                {{/if}}
            </a>
        </h2>
    </div>
</header>

{{{ checkout.checkout_content }}}

{{{ footer.scripts }}}

{{/partial}}

{{> layout/empty}}
```

## Browsing hidden translation keys
BigCommerce exposes only part of the checkout page's structure through the local checkout template. For security purposes, and to offer all stores new checkout features simultaneously, most checkout content is hidden.

This hidden content includes additional key-value pairs that support translation. You can see all the available keys with their default English-language values in the [Optimized Checkout](https://github.com/bigcommerce/checkout-js/blob/master/src/app/locale/translations/en.json) JSON file.

## Adding your own translation values

You can provide values for all of the checkout's supported translation keys even without direct access to the hidden parts of the checkout template. Here is how:

1. Download checkout's [en.json](https://github.com/bigcommerce/checkout-js/blob/master/src/app/locale/translations/en.json) file (GitHub).
2. Copy and paste the file's contents into your theme's `en.json` file.
3. Copy and paste the file's contents into each of the corresponding `json` files for the other languages you support. For naming requirements, see [Translation Keys](https://developer.bigcommerce.com/stencil-docs/localization/translation-keys#the-schema).

| Supported Language | Required Translation File Name |
|-|-|
| German | `de.json` |
| Spanish (Mexico) | `es-MX.json` |
| Spanish | `es.json` |
| French | `fr.json` |
| Italian | `it.json` |
| Dutch | `nl.json` |
| Portuguese (Brazil)| `pt-BR.json`|
| Portuguese (Portugal) | `pt.json`|
| Swedish | `sv.json`|

4. Replace the values with appropriate phrases in each file's target language.

## Localized country and state names

BigCommerce's Optimized One-Page Checkout will translate displayed **Country/State** names into supported languages. To take advantage of this functionality, enable Optimized One-Page Checkout on your store. You do not need to provide any keys-values for the **Country/State** names already translated within the BigCommerce platform. As with the translation options described above, the storefront will automatically display the translated **Country/State** names based on the default storefront language defined in the control panel.

## Limits on translation

* The translation of your theme's content consists of the language JSON files in your `lang` subdirectory and the key-value pairs for the parameters (beyond **Country/State**) that you choose to translate. 


* Stencil's multi-language capabilities are limited to the strings that you specify within the theme. The Stencil framework does not currently translate content rendered from a store's database; for example, products' names.

* Within these limitations, if you intend to do business internationally, we recommend that you specify appropriate alternate-language strings for key parts of your storefront, product catalog, and checkout. Doing so will make browsing, purchasing, and payment easier for users in your target market(s). For an overview of all localization options, see [Localizing Stores](https://developer.bigcommerce.com/stencil-docs/localization/localizing-stores).

## Resources

### Additional resources

* [Cornerstone Repository](https://github.com/bigcommerce/cornerstone) (Bigcommerce GitHub)
