# allowed_signers file for SSH/git

Git 2.34 brings support for signing commits with SSH key and having a SSH-compatible
smartcard, I have to try this. It likely getting more common in the future doesn't
hurt either and I have [pgp-alt-wot](https://gitea.blesmrt.net/Mikaela/pgp-alt-wot)
which does about the same for PGP.

## Where to find keys

* GitHub, Giteas and GitLabs expose user public keys (without useful names)
  when you append a `.keys` after their profile page
  * For example: https://github.com/Mikaela.keys https://gitea.blesmrt.net/Mikaela.keys https://gitlab.com/Mikaela.keys
* Good ideas are made to be copied, so maybe there will be more repositories like this :wink:

## Quick howto

I don't mean this to be used directly, only to be took inspiration from. See the first
link in further reading.

```bash
mkdir -p ~/src/gitea.blesmrt.net/Mikaela
cd ~/src/gitea.blesmrt.net/Mikaela
git clone https://gitea.blesmrt.net/Mikaela/ssh-allowed_signers.git
git config --global gpg.ssh.allowedSignersFile ~/src/gitea.blesmrt.net/Mikaela/ssh-allowed_signers/allowed_signers
```

Git commands should now recognised commits signed with keys I have allowed.
In the last command it's fine to remove `--global` to only affect the single
repository you are on (while I haven't tested this), should that repository
be something only I am signing in or something I need to verify otherwise
enough to list it here.

On the last command, `git config` turns it into absolute path, while manually
edited `.gitconfig` can literally have the above. I wonder if the command
would understand `--` before the file, but not enough to actually try it :smiley:

## Further reading

* [Caleb Hearth: Signing Git Commits with Your SSH Key](https://calebhearth.com/sign-git-with-ssh) ([web.archive.org](https://web.archive.org/web/20211117182628/https://calebhearth.com/sign-git-with-ssh)) inspired me to try this
* [GitHub feedback: Allow using SSH keys to sign commits](https://github.com/github/feedback/discussions/7744)
  * TODO: notify here when it actually works, link to their guide or maybe remove the section?
* [Merged Gitea PR for add support for ssh commit signing](https://github.com/go-gitea/gitea/pull/17743)
  * TODO: link to their blog once it's released
