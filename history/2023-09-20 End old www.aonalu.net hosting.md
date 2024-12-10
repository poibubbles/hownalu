The old http://www.aonalu.net (no SSL) was being served from an [[AppEngine]] `python27` runtime instance in the `aonalu-dev` project (no organization) under the `priamk@gmail.com` account. It was last deployed Aug 15, 2013, 11:33:44 PM by priamk@gmail.com.

By 2023, the `priamk@gmail.com` account required billing to be set up (again?) to access [[AppEngine]] as the card it was under had long since expired (although billing may not have been required at the time the site was created). http://www.aonalu.net continued to be served, since it was created, regardless of the billing status.

However, it didn't look like there was a way to get to the old, uploaded files for the (only) deployed version. A [StackOverflow question](https://stackoverflow.com/q/56064907) suggested that there should be a `Diagnose > Tools > Source` option for versions, but the only option was `Diagnose > Logs`. The version's `Config > View` at least gave a listing of deployed files.

The site was just a bunch of flat files created using http://getpelican.com/. The source repository for the website was probably at Bitbucket in a Mercurial repository that was long since shuttered.

The mapping to `www.aonalu.net` was deleted in `AppEngine > Settings > CUSTOM DOMAINS` to release the `www` prefix for use by the new [[Google Sites]] home. See [[Serve a Google Site]] for more info.

The old site is still available at https://aonalu-dev.appspot.com/.

This history was helpful to [[Serve a Workspace Site on a naked "A" domain]].

#gsite 
