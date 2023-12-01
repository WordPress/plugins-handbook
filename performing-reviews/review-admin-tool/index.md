# Using the Review Admin Tool

Reviews are done via the [Dashboard on the directory](https://wordpress.org/plugins/wp-admin/). Only reviewers and admins have access to this.

**Important Links**

- [Review Checklist](https://make.wordpress.org/plugins/handbook/performing-reviews/review-checklist/)
- [Review Walkthrough](https://make.wordpress.org/plugins/handbook/performing-reviews/review-walkthrough/)

All new plugins have a status of 'draft'. This means they have not yet been reviewed. To view all newly submitted plugins, go to **My Plugins** and click on **Pending Initial Review**:

![Pending Initial Review](https://i3.wp.com/make.wordpress.org/plugins/files/2016/11/Screen-Shot-2017-04-13-at-8.51.28-AM.png)

Click on the post to edit it. You should chose to open in a new window.

![Edit plugin](https://i3.wp.com/make.wordpress.org/plugins/files/2016/11/Screen-Shot-2017-04-13-at-9.01.35-AM.png)

On the post edit page, you will see the **Plugin Review Tools**. Most important at this stage is the ZIP file. Use that to download the new ZIP for your review.

Perform the steps on the [Review Walkthrough](https://make.wordpress.org/plugins/handbook/performing-reviews/review-walkthrough/) and [Review Checklist](https://make.wordpress.org/plugins/handbook/performing-reviews/review-checklist/).

If a plugin shows that it has comments, that means a non-admin has performed a review, but does not have permissions to email the developer and move the post into pending status.

If you do not have the ability to approve plugins, once you've reviewed a plugin please leave an internal note:

![Internal Note](https://i3.wp.com/make.wordpress.org/plugins/files/2016/11/internal-notes.png)

Document the issues found. For example, a good note would be as follows:

- Calls `wp-load.php` on multiple pages.
- Saves files to plugin directory.
- Includes own jQuery.
- Calls bootstrap CSS externally from a CDN.
- Author has `wordpress` in their domain name.

An administrator will then take this information and send an email to the plugin author, explaining what to fix and why.

If there are no issues found, leave a note stating that.

If, following a review, a plugin cannot be approved yet, a plugin administrator will change the status in **Plugin Controls** to _Pending_ and press **Save Changes**.

Then they will use the **Contact plugin author** button to email them an explanation why, using the predefined replies within Help Scout if possible.

Setting a plugin to pending _will not_ email the developer automatically. You _must_ remember to use the contact button.

When a plugin is ready for approval, use the automated workflow "Approve Plugin" in HelpScout.

![Approve Plugin](https://make.wordpress.org/plugins/files/2023/06/approve.png)

Then, edit the page of the plugin and click on 'edit' for the status. Change the status to Approved and click **Save Changes**.

![Save Changes](https://make.wordpress.org/plugins/files/2016/11/approve.png)

This will **automatically** email the developer. You need do nothing more.

Most plugins will not be rejected. If a plugin must be rejected, leave an internal note explaining why. Example entries:

- Rejected per author request.
- Duplicate submission.
- Author banned from directory.

Very rarely will those cases occur. Once the plugin is rejected, use the **Contact plugin author** button to email them and explain why it was rejected.

Once a plugin has had its initial review, it moves into 'pending. To view all pending plugins, go to **My Plugins** and click on **Pending**:

![Pending plugins](https://i3.wp.com/make.wordpress.org/plugins/files/2016/11/pending-plugins.png)

All pending plugins will remain in this state until they can be approved.