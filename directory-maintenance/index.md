# Directory Maintenance

Maintaining the directory can be a full-time job. To achieve this, we rely on multiple tools to constantly scan, review, and monitor check-ins. There are some filters on SVN that prevent dangerous code from being committed to the repositories, the rest of the work is done by scanning.

## Removing Plugins

Plugins are removed for reasons other than security; however, that is the most recognized reason.

Any time a plugin is closed, the developers must be contacted, and the action must be logged on the private P2. If a daily post exists, add a comment with the plugin link and why it was closed. Otherwise, create a new one.

### Immediate Closure

Plugins are closed immediately for the following situations:

- Security issues
- GPL violations
- Flagrant abuse of other community members
- Users being banned from the repository (all plugins are closed when this happens)
- Intentionally disguising themselves to get around previous blocks/bans

Except in extreme cases, make sure the developer(s) has received at least one warning before closing plugins.

Reasons to warn first:

- Sockpuppets (delete all suspect reviews first)
- Self promotion in related plugin support threads or reviews
- Tag abuse
- README scamming
- Frequent commits to game the 'recently updated' list

If a warning has been sent with no response, send a second warning or "FINAL WARNING" and explain the behavior must stop. Provide them with a realistic due date. For example, if a plugin has been warned multiple times to stop making needless commits and tag abuse, allow them 4-5 business days to comply.

### By Request

Verify the request came from either a developer with commit access or someone who works for the company. If so, reply with the Predefined email "Reply: Removal Request Completed".

Otherwise, use "Reply: Removal Request – From email doesn't match that of the plugin owner".

## Scanning the Repository

This requires a local copy of the entire plugin directory, which can be downloaded with the [Plugin Directory Slurper](https://github.com/markjaquith/WordPress-Plugin-Directory-Slurper). Alternatively, you can use the unofficial [WordPress Directory Search](https://wpdirectory.net/).

You can use `grep`, `ack`, or `ag` to scan the plugins repository. `grep` is available by default on Linux and OS X, but isn't as advanced as `ack` / `ag`. `ag` is a drop-in replacement for `ack`; it doesn't have all of `ack`'s advanced features, but is 5-10x faster.

### Examples

The following examples assume that you have a copy of all the plugins checked out into a folder called "plugins" and you wish to save your scans in a folder called "scans".

**Looking for `global $tag` in all PHP files**

```
ack "global[^;]+\$tag" --php ./plugins/ &gt; scans/global-tag.txt
```

**Find everyone using HTTP in an enqueue**

```
find ./plugins -type f -exec grep "wp_enqueue_\(style\|script\)\s*(.*[\"']<a href="http://">http://</a>" {} &gt; scans/http-enq.txt
```
On OS X, add `\;` after the `{}` to avoid the "no terminating..." error.

**Find all instances of a specific file:**

```
find ./plugins -type f -name "*datepicker-*.js" &gt; scans/datepicker.txt
```

Parsing the output can be difficult, since the output often looks like this.

```
.plugins/appmaker-woocommerce-mobile-app-manager/lib/appmaker-wp/endpoints/appmaker/class-appmaker-wc-rest-backend-posts-controller.php:705: $date_data = rest_get_date_with_gmt( $request['date'] );
```

To make life less insane, there's a summarize script.

```
./summarize-scan.php scans/rest\_get\_date\_with\_gmt.txt
```

```
5 matching plugins
Matches Plugin Active installs
======= ====== ===============
4 rest-api 40,000+
4 wptoandroid 30+
5 custom-contact-forms 60,000+
2 appmaker-wp-mobile-app-manager 50+
4 appmaker-woocommerce-mobile-app-manager 200+
```

This _will not_ clean up false positives, so before you assume that's your answer, do review the raw output to make sure you don't have incorrect data.

## Tools and Resources

- [Mark Jaquith's Plugin Directory Slurper](https://github.com/markjaquith/WordPress-Plugin-Directory-Slurper)
- [Otto's Theme Directory Slurper](https://github.com/Otto42/WordPress-Theme-Directory-Slurper/) (Windows)
- [WordPress Directory Search](https://wpdirectory.net/)
- [Ack](https://beyondgrep.com/)
- [ag](https://geoff.greer.fm/ag/)