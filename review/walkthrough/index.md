# Review Walkthrough

The following is a walkthrough of reviewing a plugin.

**Warning**: This page does not include every aspect of a review yet and should be considered highly work in progress.

## The User

Before reviewing the plugin itself, ensure the user is not currently prohibited from submitting new plugins, or attempting to evade restrictions due to a previous infraction. Often, when a user is told 'no' or their plugins are removed for repeat offenses, they will attempt to circumvent their situation by creating new accounts and pretending to be other people. This should be considered a 'bad faith' action, and should be reported to a plugin review administrator immediately.

Use the Author Card to review the user and their standing:

![Author Card](https://make.wordpress.org/plugins/files/2022/08/Screen-Shot-2022-08-03-at-1.00.21-PM.jpg)

If the plugin has been rejected before, or if the user has a large number of closed plugins, search for their email in HelpScout and the [Reviewer P2](https://make.wordpress.org/pluginrepo/) to see why. Sometimes there are perfectly normal reasons for this like retired API, often it's for behavioral issues. Always check.

If the user is marked as being moderated in the forums, be aware that there may be extenuating circumstances. This, in and of itself, is _not_ a reason to reject the plugin, but it must be considered.

## The Subject Matter

We do not accept _all_ plugins. We are _not_ required to accept and host all plugins. Regardless of what people feel, some plugins are inappropriate to be hosted on WordPress.org.

In general this is explained in our guidelines, however a decent overview of plugin concepts that will not be accepted are as follows:

- Reproduction of features included in WordPress, without any perceivable additions, such as (but not limited to) duplication of existing shortcodes (`[embed]` and `[gallery]`), widgets (RSS feed display), or functionality (adding users).
- Duplication of work being done in feature projects, such as the JSON API.
- Storefronts.
- Intentionally unethical purposes, such as black or grey hat SEO (including auto posting or 'spinning' content).
- Impossible promises such as 'Our plugin will help you earn thousands of dollars'.
- Spamming (not spam blocking, actual spamming).
- Creation of an unsafe Internet via spreading viruses or intentional security holes in WordPress.
- Inspiration of serious threats of harm (if a plugin seems to only be created to harm people, it's probably not a good fit).
- Plugin subjects that are illegal or incite violence/hate.

We also do not accept plugins that are 100% copies of other plugins _unless_ the intent is to takeover and enhance an existing but abandoned plugin that they were **unable** to adopt. If there has been no attempt to adopt, the submission should be rejected and redirected.

Remember that while the repository is open for all secure, GPLv2 (or later) compatible plugins, we reserve the right to reject any plugin on any grounds we feel are reasonable, whether or not they are explicitly noted in the guidelines.

## The Name

Since plugin _permalinks_ **cannot** be changed after approval you must make sure the defined permalink is as appropriate as possible before going further. While the _Display Name_ can be changed at any time, we still check early to see if the name has any conflicts with existing trademarks.

### Trademarks and Project Names

Make sure the _first_ term (or terms) isn't someone else's product. This includes open-source products (WordPress, Drupal, Bootstrap, Font Awesome) as well as trademarks (Twitter, Band-Aid, Kleenex). Obviously you can't be expected to know everything, but pay attention to that. If they represent the project (like someone from WooCommerce submits `woocommerce-tap-dancing`), then that's okay. You may need to read the code and check submitted URLs to make sure of ownership.

Keep in mind we **do not** accept 'permission' or 'authorization' at this time. The reason is that permission is revoked, or if a consultant's contract with a company is not renewed, then the ownership of the plugin comes into question. Plugins **must** be submitted under an account overtly and directly related to the representative of the project.

If they're not working for Wells Fargo, with a Wells Fargo email address, they can't use `wells-fargo-for-woocommerce` as the plugin slug. However! If you contact them and Wells Fargo emails back saying it's really them, have the company create an official user ID. You can change the owner by editing the plugin and changing the value of the author:

![Author](https://i3.wp.com/make.wordpress.org/plugins/files/2016/11/autor.png)

### Typos and Long (or Short) Names

Check the name for typos. People don't want `fraquently-asked-questions` as their plugin name most of the time. You can correct this for them and in the review let them know.

Check the name for foul language, version numbers, and length. We shouldn't allow a plugin named `cars` for example, as that's incredibly short. At the same time, `mike-turners-super-car-code-for-woocommerce-and-easy-digital-downloads` is a really long slug and probably not what they wanted.

### Restricted Terms

Beyond the trademark issue, we don't permit plugins to use `wordpress`, `theme`, or `plugin` in them except for extreme cases. Check the name for `plugin` – very few plugins need their slug to have `plugin` in there. There are exceptions like `multisite-plugin-manager` but they're rare.

To correct these, you can rename the slug. For example, if someone outside the Contact Form 7 project submits a plugin named `contact-form-7-my-cool-puppy` rename the slug to `cf7-my-cool-puppy` and continue on. If they've used `plugin` in the name and it's not a plugin that manages/handles plugins, remove the term. If they've used `wordpress` change it to `wp` and so on. Use your best judgement, and remember not to replace the first term(s) with other trademarked ones.

## The Readme

This is only required on submission _**IF**_ a plugin is a service or makes remote calls. If at any time in the review, it is determined the plugin requires documentation to be usable, a readme may be required even if not a service.

While it's obvious that a Facebook connection plugin will contact Facebook, it's less clear with some APIs and services. A service must explain that it's a service, how to join it, how to register, and preferably why. Read it. If **you're** confused by the plugin `readme` and directions, a user will be. Push back and strive for clarity.

## The Code

Open the plugin and review _all_ the code. Line by line. You can use searches to help.

Some good greps:

- `wp-(con|blog|load)`: Few plugins should call those terms.
- `$_(POST|GET|REQUEST)`: This will help you check for sanitization.
- `'function '`: Notice the space there. This can help you spot badly named functions.

**Remember**: trust your eyes more than the tool.

### Security

If, in your review, you determine there is no way possible for the plugin to be secure, it should be rejected. This primarily happens with plugins that attempt to embed PHP in posts. There's no way to really handle true sanitization, and worse, the plugins often neglect to restrict use to admins and editors, making it a huge danger on a multisite.

### Uninstall and Deactivation

Make sure they have this at the top of the uninstall file:

```
if( ! defined( 'WP\_UNINSTALL\_PLUGIN' ) )
exit ();
```

And make sure the process is sane. If a deactivation is used, encourage them _not_ to delete everything on deactivation, otherwise debugging users may find their data erased.

### Function/Class/Define Names

All should be unique. Examples of bad names:

- `function tags()`
- `class Plugin{}`
- `define( MY_PLUGIN, true)`

In the case of shared libraries, like SimpleDOM or phpQuery, which use standard defines in PHP, the developer is required to check _if_ the library already exists and not include it if so.

### Sanitization, Validation, Escaping

It's important to sanitize, validate, and escape all POST/GET/REQUEST calls. The goal here is to prevent a user from accidentally sending trash data through the system, as well as protecting them from potential security issues.

Using `stripslashes` or `strip_tags` is rarely enough. The ultimate goal is that invalid and unsafe data is **never** processed, saved, or displayed. Clean everything, check everything, escape everything, and never trust the users to always have input sane data.

Examples of unsafe usage of POST data:

```
update_option( 'my_plugin_data', $_POST['my-data'] );
```

### Nonces

All actions that accept POST data should be secured with a [nonce](https://developer.wordpress.org/apis/security/nonces/) to prevent unauthorized access.

Remember, `check_admin_referer` alone is **not** bulletproof security. Do not rely on `nonces` for authorization purposes. Use `current_user_can()` in order to prevent users without the right permissions from accessing things.

### Javascript

Make sure none of the default JS libraries are included in the plugin or called remotely like from `https://ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js` — WordPress includes its own version of jQuery and many other similar JS files. No one needs to include them.

### Offloading Content

Offloading images, JS, CSS, CGI, and other scripts to Google (or jquery.com, or anywhere else, frankly) is disallowed because it introduces an unnecessary dependency on another site. If the file is a part of WordPress Core then it should be used, otherwise it must be included _locally_ in the plugin, not remotely.

The one exception to this rule is if a plugin is performing a service. We will permit this on a case by case basis, however since this can be confusing, we have some examples of what are not permitted:

- Offloading jQuery CSS files to Google or a CDN. All files should be locally included.
- Inserting an iframe with a help doc. A link, or including the docs is preferred.
- Calling images from the author's own domain. They should be included in the plugin.

Here are some examples of what we do permit:

- Calling font families from Google or their approved CDN (if GPL compatible).
- API calls back to your server to process possible spam comments (like Akismet).
- Offloading comments to your own servers (like Disqus).
- oEmbed calls to a service provider (like Twitter or YouTube).

### Saving Files

Plugins are permitted to save files, however they cannot save them to the `plugins` folder, as that gets deleted on plugin upgrade. We recommend files be saved to `wp-content/uploads/pluginname` as that can easily be made multisite compatible (via `wp_upload_dir`) and it will always be writable. Saving 'temp' files to a plugin folder can be permitted, however make sure they're deleted properly.

### 3rd Party Libraries

At this time, we permit the use of 3rd party libraries, however they **must** be the latest stable version. The library also must be actively maintained, as the unmaintained are prone to security issues.

Examples of unmaintained libraries include:

- TimThumb
- MVC2
- CSS Tidy
- Titan Framework
- Magnificent Popup

There are some cases where it is difficult or impossible to update a library. This commonly happens with libraries like Bootstrap. In those cases, we permit the most recent versions, however we encourage developers to update as older versions that **do not** receive security updates will not be permitted.