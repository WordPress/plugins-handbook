# Security and Guideline Violation Reports

Users, security firms, and developers all send in security reports. Each one must be read, reviewed, and replied to without exception. The goal is to ensure accuracy in reporting and communicate clearly to the developers what must be corrected and why.

While all plugins in the WordPress.org Plugin Directory are required to be compatible with the GPLv2 or later, the same is not true of code hosted outside WordPress.org, which can lead to confusion when someone reports that a plugin hosted elsewhere is violating guidelines. If you are at all confused as to which plugin they mean, just ask for a link to the plugin page.

## Verification

All reports must be checked by a human being to ensure they are valid. If someone reports a vulnerability it must be tested. If someone reports behavior in the forums, and you don’t have forum admin access to see what people have been doing, speak with a senior reviewer.

### Copyright/Trademark Violations

As of 2016, we no longer permit plugins to use someone else’s trademark/product name as their plugin slug, or the first term(s) of their plugin. The summary can be as simple as “If you don’t work for Burt’s Bees, you cannot use `burts-bees-in-stock` or `burts-bees` as your plugin slug.”

That said, all plugins submitted _prior_ to 2015 are ‘grandfathered’ in, and we will not close them unless there is a pressing need to do so. All non-official plugins with names that no longer are approved should state in their name and/or description that they are not the official plugin.

Every attempt is made to ensure only the authorized user of a name can use a name. If a mistake is made and it is critical enough, plugins _may_ be closed.

### Security Reports

All reports must be reviewed for accuracy and validity. If you can’t reproduce it, reply to the reporter and tell them so. Similarly, if the issue is not the plugin but a decision made in WordPress, we do not close the plugin. For example, administrators can post JavaScript to post titles. Some people fail to recognize that this is a _known_ aspect of WordPress, and not a security issue.

### Behavioral Violations

Everyone who officially represents a plugin is required to abide by the guidelines. If someone working for a plugin’s company makes sock puppets, report it to the plugin owner with a stern warning. Their actions reflect on those of the developer, and if they are severe enough, the plugin will be removed. If, following a warning, a developer escalates the behavior, all their plugins will be closed. Abusing moderators and reviewers is not permitted.

### Sockpuppets

In general, the review of a sockpuppet complaint will be to read the suspected posts and verify the proof from the forum administrator. Very rarely do the forum admins get those wrong, however always double check in case you know that the developer asked people at a meetup to please review. Under no circumstances should you divulge _exactly_ how the fake accounts were spotted. If the developer is insistent, please get a senior reviewer to help, but we do not disclose our methods as they would then be abused.

### Review Compensation

Rewarded users for leaving reviews is not permitted. Period. Developers cannot pay, offer discounts, or otherwise ‘give back’ to users who leave reviews. Any time a developer does this, all reviews from the time the offer was made until it was removed will be archived in the WordPress forums. They will not be restored as there is no way for us to be sure that they were innocent or not. The legal term for this is “Fruit from the poisoned tree.” By offering compensation, the developer has put all reviews made in that time period in jeopardy.

## Reply to the Reporter

We currently use a standard reply to inform reporters that the email has been read by a human and will be followed up on. Always send this. If the email came into Help Scout without a reply address, try to find their email (and let them know we had an issue, and ask them to check their email client).

No matter what, if the review is valid or not, you must reply to their email. They need to know humans are here, reading emails, and validating reports.

## Close the Plugin

With few exceptions, plugins are closed immediately when a security issue is confirmed. We have no system to allow a plugin to be flagged as ‘update and fix issues in 7 days or it will be automatically closed.’ Furthermore, such a system would require a large amount of manual monitoring, and people would still be able to download the plugin. Therefore the plugin is closed and the onus is on the developer to fix the plugin.

The other reason we close plugins is to prevent new users from making themselves more at risk. This means we must weigh the reality of the usage of the plugin, the responsiveness of the developers, and the risk of the vulnerability before we close a plugin. If it would cause more users to be at risk (and create FUD) to close a plugin, do NOT close the plugin. If the plugin developer has notably argued and been reluctant to fix issues, DO close the plugin.

Examples of plugins that should not be closed without due consideration are: Jetpack, Akismet, NetGen Gallery, Yoast SEO.

Those plugins have all proven, over years, that they are responsive to fixes. In addition, closing them would send up a signal that there’s a major security issue on tens of thousands of sites, putting the majority of WordPress sites at risk.

Please check with a Plugin Review Admin if you’re unsure. In general, most plugins will be closed.

### Disable vs Close

Disabling a plugin allows it to still push updates while closed. Closed plugins push no updates. Most of the time, plugins should be CLOSED and not DISABLED. The use of DISABLED is for when a plugin is being retired, but information needs to be sent to existing users. It should be very rare, and reserved for things like Feature Plugins or extreme security related situations.

## Contact the Developer

Email the developer through Help Scout. We have a standard reply for most guideline issues that explains why their plugin was closed and has sections for you to add in a link to the plugin and the description of the issue. If the submitted issue wasn’t clear, make it clear. Link the developer to places where they can learn more about the issues.

## Post in the Plugin Admins Blog

If there’s already a daily post, leave a comment with a link to the plugin and why you closed it. Otherwise make a post and include it.

## Review the Fix

When the developer replies, perform the following checks:

*   Did they fix the change in SVN?
*   Did they increment their version number?
*   Are there any other guideline violations or security issues you noted?
*   Would they pass a review today?

If the answer to any of those is ‘no,’ send the developer a new email and detail what needs to be changed. When they reply, review the changes again until everything’s good.

Remember: All changes must be tracked in SVN, the version number must be increased, and the plugin must pass a review ‘today.’

## Reopen the plugin

If everything is good, reopen the plugin. Use the standard reply that explains their plugin is open, but the stats may take a few days to catch back up.
