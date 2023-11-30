# Review Checklist

## Reviewer Workflow

*   Verify the submitted name and subject matter are acceptable
*   Download the zip
*   Check all files for guideline violations
*   Ensure the readme is clear ([only a requirement for services](https://make.wordpress.org/plugins/handbook/performing-reviews/review-checklist/#readme))
*   Test in a secure environment
*   Detail any issues found and email the developer from Help Scout
*   If no issues are found, approve the plugin

## Required

All plugins and developers are required to comply with all Plugin Directory Guidelines as well as the [Forum Guidelines](https://wordpress.org/support/guidelines/) and [WordCamp Code of Conducts](https://make.wordpress.org/handbook/community-code-of-conduct/) (when applicable).

*   100% adherence to the [Detailed Plugin Guidelines](https://developer.wordpress.org/plugins/wordpress-org/detailed-plugin-guidelines/)
*   Full support of the current version of WordPress
*   The plugin cannot be a 100% copy of another plugin. Forks are permitted, however they must show significant improvements or changes to the original.
*   The plugin must be the developer’s own work. Submission of another person’s plugin is not permitted.
*   If included in the review, the plugin header image and logos must be family friendly and not be offensive.

### Subject Matter

The following plugin types are generally not permitted however exceptions can and will be made (for example, plugins that are a part of a featured project for core, such as the Rest API):

*   Black or grey hat SEO (including plugins that auto post content and content spinners)
*   Plugins that state to ‘help you earn thousands of dollars’ or other improbable claims
*   Frameworks, boilerplates, and libraries plugins
*   Plugins that require themes or plugins to be edited for use
*   Marketplace or storefront only plugins
*   Plugins that reproduce core WordPress functions or features without perceivable improvements (example: a plugin that allows embedding youtube videos)
*   Plugins that allow users to paste in raw JS/CSS/HTML/PHP without sanitization or security

Please note: All existing plugins in the directory are permitted to remain, and will not be deleted unless there are extreme circumstances.

### Licensing

*   Be 100% GPLv2 or later and/or 100% GPL\-compatible licensed
*   Copyright and licenses must be explicitly declared using the license and license uri header slugs in the readme
*   Licenses of any resources included such as fonts or images must be declared in the plugin header
*   Code and design should be original _or_ legally permitted for use
*   Forks must be appropriately credited; no copyright information may be removed

### Readme

*   Information on how to configure the plugin is recommended
*   If 3rd party services are used, the readme must
    *   clearly disclose as to what is used, when, and why
    *   include links to the service’s terms of use and/or privacy policy
*   If no support is provided, the readme must indicate such in clear terms

### Code

*   No PHP or JS errors
*   No errors when run with `WP_DEBUG` set to true
    *   Recommended plugins: [Developer](https://wordpress.org/plugins/developer/), [Debug Bar](https://wordpress.org/plugins/debug-bar/), [Query Monitor](https://wordpress.org/plugins/query-monitor/)
*   Validation, sanitization, and escaping of all processed or saved data
*   Use of a unique prefix for everything the plugin defines in the public namespace (ex. options, functions, global variables, constants, post meta, etc.)
*   Valid readmes
*   No saving content locally to the plugin folder, as it is deleted on upgrades

### Core Functionality and Features

*   Using WordPress functionality and features first
*   Using WordPress [content directory functions](https://codex.wordpress.org/Determining_Plugin_and_Content_Directories) to determine locations of folders and files
*   Avoiding hard coding to modify content (using function parameters, filters and action hooks where appropriate)
*   Avoiding duplication of existing WordPress core features (i.e. embedding YouTube)
*   Tags and descriptions matching what the plugin does and what it connects with
*   Requirement checks fail gracefully when not present

### Documentation

*   Custom features, options or any limitations (for example menu restrictions), should be explained contextually and within the readme
*   Any remote calls (such as serviceware calling it’s own servers to process spam) must be disclosed in the readme
*   Any external requirements such as registration with a service must be documented in the readme and the settings page

### Themes and other Plugins

*   Don’t include any themes. A theme can be required but not included or auto-installed
*   Don’t include other plugins wholesale. A plugin can be required but not included or auto-installed
*   Don’t do things in a plugin considered theme territory (exception: mobile plugins may include mobile themes)
*   Do not require other themes or plugins be edited for use as those changes would be erased on updates

### Security and Privacy

*   Don’t phone home without informed user consent
*   Collection of user data must be “opt-in” only and have the relevant option set to disabled by default
*   Validate and sanitize untrusted data before processing (See: [Data Validation](https://codex.wordpress.org/Data_Validation))
*   Escape all data before output (See: [Data Validation](https://codex.wordpress.org/Data_Validation))
*   Do not use URL shorteners
*   Use prepare() and $wpdb for SQL calls

### Selling, credits, and links

*   Upselling is permitted from plugin settings screen or a link on their entry on the plugin list page
*   Forward facing links (including credit links, powered by, and ads) must be optional and not active by default
*   Sponsored links are permitted within reason
*   Third Party Ads are not permitted due to tracking
*   Affiliate links should be avoided wherever possible, and unhidden when used — use the real link to the affiliate, not a custom shortened URL
*   UTM links to a developer’s site are allowed anywhere links are permitted

### Stylesheets and Scripts

*   No hard coding of scripts or styles; use `wp_enqueue_*`
*   No analytics or tracking by third parties
*   No minification of scripts or files unless the original files are also provided
*   No minification of scripts that prevents them from being human readable (example: do not use `p,a,c,k,e,r`)
*   Use core-bundled scripts (example: jQuery)
*   Include all scripts and resources locally (exception: fonts are permitted to be remote loaded, services may also remote load on a case by case basis)

## Recommended

*   Accessibility – Plugins should follow the [Accessibility Handbook](https://make.wordpress.org/accessibility/handbook/)
*   Code should be written to support internationalization and automatic translations via [translate.wordpress.org](https://translate.wordpress.org/)
*   Support of PHP 5.2.4 and up, or graceful failure if newer versions are required
*   Proper alerts and errors if any required plugin or theme is not installed and active

## Serviceware Requirements

If a plugin connects to a service, the following additional requirements apply:

*   Data transmission is secure and sanitized
*   Readme description (and FAQ) detail usage and registration
*   Connectivity to the service is **not** performed via an iframe in the dashboard (APIs are recommended)

## Not Permitted

The following items are not permitted in any new plugin. While we have existing plugins in violation, we handle them on a case-by-case basis.

*   Calling `wp-load` directly to gain access to core functions
*   Trademark and/or Copyright violations. (There are certain exceptions for the owners of registered trademarks, [some of which are listed here.](https://meta.trac.wordpress.org/browser/sites/trunk/wordpress.org/public_html/wp-content/plugins/plugin-directory/shortcodes/class-upload-handler.php#L613))
*   Remote loading data when not absolutely necessary
*   Terms of Use violations for 3rd party services (such as Yahoo’s APIs and most finance related ones)
*   Tracking usage without explicit opt-in consent
*   Using PHP Shorttags (ex. `<?=OPTION_NAME?>` )
*   Non-GPLv2 (or later) compatible code
