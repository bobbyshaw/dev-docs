# Add to Cart URLs

<div class="otp" id="no-index">

### On this page
- [Parameters](#parameters)
- [Common usage](#common-usage)
- [Adding multiple products](#adding-multiple-products)

</div>

Query string parameters can be appended to Bigcommerce product and `/cart.php` urls in order to pre-select an SKU or add a product to cart. These parameters make it possible to build custom add to cart links and forms for use on BigCommerce storefronts and remote sites (such as WordPress, blog posts, and social media).

URLs constructed with these parameters allow you to:
* Pre-select a specific SKU on a product detail page
* Add a specific product or SKU to the cart
* Add a specific SKU to the cart and go directly to checkout.
* Attach a `source` for marketing and analytics purposes

## Parameters

| **Type**| **Parameter** | **Description**                                     | **Example**                                                 |
|-- |-|--|-|
| string  | `action=`     | `add` or  `buy`; `buy` goes directly to checkout    | `/cart.php?action=add&product_id=123`                       |
| string  | `couponcode=` | coupon code to apply to the cart                    | `/cart.php?action=add&product_id=123&couponcode=10off100`   |
| int     | `product_id=` | product id to add to the cart                       | `/cart.php?action=add&product_id=123`                       |
| int     | `qty=`        | quantity to add to the cart                         | `/cart.php?action=add&product_id=123&qty=3`                 |
| string  | `sku=`        | SKU to add to the cart (or select on product page)  | `/cart.php?action=add&sku=xlredtshirt`                      |
| string  | `source=`     | source of the sale for analytics; can be any string | `/cart.php?action=buy&sku=xlredtshirt&source=emailcampaign` |

## Common usage

Below is a table of common scenarios and example URLs.

| **Scenario**                                                 | **URL**                                                              |
|--|-|
| Select a specific SKU on Product Detail page                 |`https://{{domain}}/{{page}}?sku={{sku}}`                             |
| Add specific SKU to cart                                     |`https://{{domain}}/cart.php?action=add&sku={{sku}}`                  |
| Add specific SKU to cart, go directly to checkout            |`https://{{domain}}/cart.php?action=buy&sku={{sku}}`                  |
| Add specific SKU to cart, go to checkout, and include source |`https://{{domain}}/cart.php?action=buy&sku={{sku}}&source={{src}}`   |
| Add product to cart by product id and set quantity           |`https://{{domain}}/cart.php?action=add&product_id={{id}}&qty={{qty}}`|
| Add product to cart and set coupon code                      |`https://{{domain}}/cart.php?action=add&product_id={{id}}&couponcode={{code}}`          |

Once constructed, a URL can be inserted directly as text or as an HTML link:

```html
<a href="https://example.com/cart.php?action=buy&product_id=123&source=blogpost">Purchase Our New Product Now!</a>
```

## Adding multiple products

The `sku` and `product_id` parameters accept a single value; you can only use the first value of a comma-separated list of values. In other words, only one product can be added for each request made to an add to cart URL. However, it's possible to combine several HTTP requests into a single button click using front-end JavaScript, as long as your code waits to receive the response of your first request before it makes a second.

The following gives a very basic example using jQuery.  You can also use async/await syntax to make a series of calls from within a `for` loop.

```html

<button type="button" id="addToCart">Add Bundle to Cart</button>

<script>
// when #addToCart is clicked...
$("button#addToCart").click(function() {

	// add product id 123
    return $.get("/cart.php?action=add&product_id=123")
	.done(function(data, status, xhr) {
		console.log('first item complete with status ' + status);
	})
	.then(function() {
		// add product id 456
		return $.get("/cart.php?action=add&product_id=456");
	})
	.done(function(data, status, xhr) {
		console.log('second item complete with status ' + status);
	})
	// chain more async GET requests using .then & .done
	.fail(function(xhr, status, error) {
		console.log('oh noes, error with status ' + status + ' and error: ');
		console.error(error);
		return xhr.done();
	})
	.always(function() {
		// go to cart
		return window.location = "/cart.php";
	});

});
</script>
```

<div class="HubBlock--callout">
<div class="CalloutBlock--warning">
<div class="HubBlock-content">

<!-- theme: warning -->

> Due to CORS (Cross Origin Resource Sharing), using JavaScript to make multiple carting requests only works in the BigCommerce storefont and only on the storefront with the domain the request is being made to.

Alternatively, the [Storefront Cart APIs](https://developer.bigcommerce.com/api-docs/cart-and-checkout/working-sf-apis#working-sf-apis_storefront-cart) `/api/storefront/cart` endpoint accepts an array of `lineItems` -- depending on the complexities and specifics of the use case, using Storefront Cart APIs may be a better solution than adding to cart URLs.

</div>
</div>
</div>

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyNjk3NjY0NTJdfQ==
-->
