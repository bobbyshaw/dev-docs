<div><h3 class="sub-docs-type" id="bigcommerce-for-wordpress">BigCommerce for Wordpress</h3>

# Multisite Setup

<div class="otp" id="no-index">

### On This Page
- [Getting your API credentials](#getting-your-api-credentials)
- [Setting up a WordPress site using API account credentials](#setting-up-a-wordpress-site-using-api-account-credentials)
- [Additional resources](#additional-resources)

</div>

When connecting more than one WordPress site to your BigCommerce store, you need to use an API account to link them. If you try to connect using the 'connect your store' flow, which uses a BigCommerce app to streamline the connection, your first WordPress site will lose its connection to BigCommerce.

### Multi-site and subdirectories
Multiple sites can share the same API credentials, or you can choose to create a new set of credentials for each site.


| **Configuration Method** | **Is Supported** |
|:-------------------------|:-----------------|
| Subdirectories           | No               |
| Subdomains               | Yes              |
| Separate Domains         | Yes*             |
Note that embedded checkout is only supported on a single domain at a time. See the [BigCommerce for WordPress](https://support.bigcommerce.com/s/article/BigCommerce-for-WordPress-Checkout?language=en_US#subdomain-setup) documentation.*



</div>


## Getting your API credentials

1. To get your store’s API credentials, sign in to your BigCommerce store and head to `Advanced Settings` > `API Accounts`. 

<!--
    title: #### Click 'Create API Account' to get credentials

    data: //s3.amazonaws.com/user-content.stoplight.io/6116/1544044020003
-->

#### Click 'Create API Account' to get credentials
![#### Click 'Create API Account' to get credentials](//s3.amazonaws.com/user-content.stoplight.io/6116/1544044020003 "#### Click 'Create API Account' to get credentials")


2. Click the blue `Create API Account` button on the top left-hand side. This opens up a screen that will ask you to enter a name and select scopes for the API account.


#### Fill in the Name and OAuth Scopes.
![#### Fill in the Name and OAuth Scopes.
](//s3.amazonaws.com/user-content.stoplight.io/6116/1544044197137 "#### Fill in the Name and OAuth Scopes.
")

<div class="HubBlock--callout">
<div class="CalloutBlock--info">
<div class="HubBlock-content">
<!-- theme: info -->

>### API account name field
> We suggest 'WordPress' for the name, although you can name it anything you'd like as long as it's unique within your API accounts and is more than three characters.

</div>
</div>
</div>

3. For the OAuth Scopes, select the following default settings:

| **OAuth Scope**                              | **Default Selection** |
|:---------------------------------------------|:----------------------|
| Content                                      | None                  |
| Checkout Content                             | None                  |
| Customers                                    | Modify                |
| Customers Login                              | Login                 |
| Information & Settings                       | Modify                |
| Marketing                                    | Read-Only             |
| Orders                                       | Read-Only             |
| Order Transactions                           | Read-Only             |
| Create Payments                              | None                  |
| Get Payment Methods                          | Read-Only             |
| Products                                     | Read-Only             |
| Themes                                       | None                  |
| Carts                                        | Modify                |
| Checkouts                                    | Modify                |
| Sites & Routes                               | Modify                |
| Channel Settings                             | Modify                |
| Channel Listings                             | Modify                |
| Storefront API Tokens                        | None                  |
| Storefront API Customer Impersonation Tokens | None                  |

<!--
* Checkout Content: `none`
* Customers Login: `login`

Select `modify` for all other scopes.

The screen will also contain your API Path, which you will need for the WordPress Plugin. -->

<!--
    title: #### Fill in the Name and OAuth Scopes.

    data: //s3.amazonaws.com/user-content.stoplight.io/6116/1544044197137
-->
<!--
#### Fill in the Name and OAuth Scopes.
![#### Fill in the Name and OAuth Scopes.
](//s3.amazonaws.com/user-content.stoplight.io/6116/1544044197137 "#### Fill in the Name and OAuth Scopes.
")-->

4. After you have finished setting a name and selecting scopes, click `Save`. You will then see a modal that contains the `Client ID`, `Client Secret` and `Access Token` necessary for the remaining fields in the WordPress API Credentials settings.

<!--
    title: #### API Credentials

    data: //s3.amazonaws.com/user-content.stoplight.io/6116/1544044553372
-->

#### API credentials
![#### API credentials](//s3.amazonaws.com/user-content.stoplight.io/6116/1544044553372 "#### API Credentials")

<div class="HubBlock--callout">
<div class="CalloutBlock--info">
<div class="HubBlock-content">
<!-- theme: info -->

>### .txt file download
> You'll also see a `.txt` file download in your browser that contains the same information in an easy-to-read format, once again including your API Path in case you didn't copy it before.

</div>
</div>
</div>

<!--
    title: #### .txt file download

    data: //s3.amazonaws.com/user-content.stoplight.io/6116/1544044589538
-->

#### .txt file download
![#### .txt file download
](//s3.amazonaws.com/user-content.stoplight.io/6116/1544044589538 "#### .txt file download
")

## Setting up a WordPress site using API account credentials

1. To set up a WordPress site using this method, click `Enter your API credentials` on the welcome screen in the plugin. 

<!--
    title: #### WordPress Plugin Welcome Screen

    data: //s3.amazonaws.com/user-content.stoplight.io/6116/1544043727239
-->


#### WordPress plugin welcome screen
![#### WordPress Plugin Welcome Screen
](//s3.amazonaws.com/user-content.stoplight.io/6116/1544043727239 "#### WordPress Plugin Welcome Screen")

<!--
    title: 
    data: //s3.amazonaws.com/user-content.stoplight.io/6116/1544043952871
-->

![](//s3.amazonaws.com/user-content.stoplight.io/6116/1544043952871 "")


2. Enter your API credentials on your WordPress site. Saving the API credentials on your WordPress site will direct you to name the channel that the plugin will create. This allows you to list product to the channel from within BigCommerce and link orders back to the channel that comes from the WordPress site. You can also link to an existing channel.


_Congratulations, you're done setting up your additional site!_ 

<div class="HubBlock--callout">
<div class="CalloutBlock--info">
<div class="HubBlock-content">

<!-- theme: info -->


>### WordPress currency processing
> The WordPress sites you connect to your BigCommerce store will process in the same currency as the BigCommerce store.

</div>
</div>
</div>

## Additional resources

* [Multisite Ecommerce with WordPress and BigCommerce](https://medium.com/bigcommerce-developer-blog/multi-site-ecommerce-with-wordpress-and-bigcommerce-40dee194f8a) (Developer Blog)
