Note: **The second `ssh-keygen` command below was taken from** [Atlassian: Git+SSH](https://www.atlassian.com/git/tutorials/git-ssh) **and doesn't work because it has non-breaking spaces.** ; preserved as-is for the benefit of issue [[2023-10-01 Copied and pasted non-breaking space]]. 

Create SSH key:
```
ssh-keygen -t ed25519 -C "your_email@example.com"
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
Edit `.ssh/config` to auto-load keys into `ssh-agent`:
```
Host github.com-<gitusername>
  HostName github.com
  User git
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/<keyname>
```
Start `ssh-agent`:
```
eval "$(ssh-agent -s)"
```
Add a key to `ssh-agent`:
```
ssh-add --apple-use-keychain ~/.ssh/<keyname>
```
Log into Github and add the SSH key (`.ssh/<keyname>.pub`) to [Settings > SSH and GPG keys](https://github.com/settings/keys):
```
pbcopy < ~/.ssh/<keyname>.pub
```
Verify the new key's SHA256 fingerprint against the key added to Github above:
```
ssh-keygen -lf ~/.ssh/<keyname>
```
Test authentication (expect a friendly response rather than an actual login):
```
ssh -T git@github.com
```
Try cloning a repository using the key:
```
git clone git@github.com:<account>/<repository>.git
```
Verify Github's public key against [Github's SSH keys](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/githubs-ssh-key-fingerprints). Also here: https://docs.github.com/en/rest/meta/meta

In the new, cloned repository, note the `url` value in the `[remote "origin"]` section of `.git/config`, which determines the method of access:
```
[remote "origin"]
  url = git@github.com:<account>/<repository>.git
```
If you're working with an older repository, a different method may be used, like `https`:
```
[remote "origin"]
  url = https://github.com/<account>/<repository>.git
```

Git repo identification...
git config --global --edit
fix, maybe commit git to stowage
git commit --amend --reset-author



Also: changing the SSH passphrase:
```
ssh-keygen -p -f ~/.ssh/<keyname>
```


* [Github: About SSH (overview)](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/about-ssh)
* [Github: Generate a new SSH key and adding it to the ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
* [Github: Adding a new SSH key to your GitHub account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
* [Github: Working with SSH key passphrases](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/working-with-ssh-key-passphrases)
* [Atlassian: Git+SSH](https://www.atlassian.com/git/tutorials/git-ssh)



See https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent.