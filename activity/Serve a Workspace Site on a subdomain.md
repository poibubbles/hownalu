This method assumes the [Site](https://sites.google.com/) resides in a Google Workspace account and therefore requires [Google Workspace admin](https://admin.google.com/) access.

The (easier to find) method at "[Use a custom domain for your site](https://support.google.com/sites/answer/9068867)" assumes you are the owner of the Site and can manage domain customization on your own; this solution is not for Workspace accounts.

Ensure that the Site itself is viewable by the public by checking the `Publish` settings or first `Unpublish`-ing the Site and checking its viewability. Make sure the Site is both publicly viewable and published before proceeding.

Go to [`Admin > Apps > Google Workspace > Sites > Custom URL`](https://admin.google.com/ac/apps/sites/address).

Click the `+` to the right of the `Sites` listing.

Add a custom URL for a "New Site" (only option available).

Enter the new site's URL without a protocol prefix (no `https://`) so that it resembles the resource path in the Site's publishing settings.

For example, if the web address for the Site itself (accessed within the Site's `Publish` settings) is `https://sites.google.com/aonalu.net/mysite`, then in the new site's URL (accessed within the Workspace admin console) should be:

  `sites.google.com/aonalu.net/mysite`

Choose the custom subdomain.

Follow the instructions to update DNS..

To use **mypage.aonalu.net**, follow these steps:
1. Sign into your domain hosting service (eg. Google Domains)
2. Navigate to your DNS management page for **aonalu.net**
3. Find the CNAME settings and enter **mysite** as the CNAME value or alias
4. Set the CNAME destination to **ghs.googlehosted.com**
5. Save changes and click **Add Custom URL** below

For Dotster's DNS records, the subdomain `mysite` is the `Name`, `CNAME` is the `Type`, and `ghs.googlehosted.com` is the `Content`.

Many online solutions point to:
https://www.steegle.com/google-sites/how-to/map-domain-web-address-g-suite

#gsite #dns #gwork 