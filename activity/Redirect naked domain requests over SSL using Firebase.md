Note that it's probably better to do a server side 301 redirection, then use JavaScript, then fallback to a meta http-equiv refresh as a last resort.

Trying to use Firebase to host a simple HTML page at https://base.url that redirects to https://www.base.url (a Google Site).

Examples below for aonalu.net and hookuaaina.org..

Firebase wants to add these DNS records::

	A   aonalu.org 199.36.158.100
	TXT aonalu.org hosting-site=aonalu-21ef1

In Dotster, adding TXT as name=hosting-site, value=aonalu-21ef1.

When doing aonalu.net, Firebase detected existing A records that probably
pointed to the four IPs used for base redirection in Google Workspace.
(Unfortunately Workspace redirection only seems to work with HTTP for base
domains).

Got rid of the four Workspace IPs but still getting the error for all four.

Records not yet detected for aonalu.org (cleaner, nothing going on there).
Hoping this works, and that it provisions an SSL cert for the base domain.
Then will be more confident that the other will too.

Eliminated the four A records for hookuaaina.org in the meantime, hoping to
speed up the process later.

Trying '@' for aonalu.org TXT record with value: hosting-site=aonalu-21ef1

Setting up base hookuaaina.org in Firebase.

https://console.firebase.google.com/?pli=1

project name: hka-org-base-redirect
Kept Google Analytics.
Kept default settings for Benchmarking, Technical Support, etc..
firebase login
Logging in as aloha@hookuaaina.org
firebase init
Hosting only, no Github.
Use an existing project: hka-org-base-redirect
Use 'public' as public directory.
Configure as single-page app.
No auto-builds with Github.
Edit index.html - strip and include redirect.
firebase deploy
Hosting URL: https://hka-org-base-redirect.web.app
Using quick setup for Custom URL.
hookuaaina.org redirecting to www.hookuaaina.org
!RESET TTL for hookuaaina.org @ to 1hr!
TXT record name left empty for base domain.
TXT value: hosting-site=hka-org-base-redirect

aonalu.net
  Expected value hosting-site=aonalu-21ef1
  Discovered value(s) google-site-verification=BOyTvfNUfg2tObZGI0UMFA_ZUUciqV5
aonalu.org
  Expected value hosting-site=aonalu-21ef1
  Discovered value(s)

..waiting for local dig to show new A record for hookuaaina.org.

..seeing if aonalu.org eventually gets a proper discovered value using name=@,
value= what's above.

..then, if feeling like gotta delete or override TXT google-site-verification
for aonalu.net.

So far, aonalu.org not detecting new IP for A record.

MISSING HERE IS THE HTTP-EQUIV META REFRESH HTML CODE..
..that was used in a single index.html in Firebase hosting to do the naked domain "redirection." A better (or at least more comprehensive) approach is at https://serpstat.com/blog/why-meta-refresh-and-javascript-redirects-need-to-be-abandoned/.
