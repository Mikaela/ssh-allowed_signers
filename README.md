# allowed_signers file for SSH/git

Git 2.34 brings support for signing commits with SSH key and having a SSH-compatible
smartcard, I have to try this. It likely getting more common in the future doesn't
hurt either and I have [pgp-alt-wot](https://gitea.blesmrt.net/Mikaela/pgp-alt-wot)
which does about the same for PGP.

## Where to find keys

* GitHub, Giteas and GitLabs expose user public keys when you append a .keys after their profile page
* Good ideas are made to be copied, so maybe there will be more repositories like this ;)

## Further reading

* [Caleb Hearth: Signing Git Commits with Your SSH Key](https://calebhearth.com/sign-git-with-ssh), [web.archive.org](https://web.archive.org/web/20211117182628/https://calebhearth.com/sign-git-with-ssh), inspired me to try this
* [GitHub feedback: Allow using SSH keys to sign commits](https://github.com/github/feedback/discussions/7744)
  * TODO: notify here when it actually works, link to their guide or maybe remove the section?
* [Merged Gitea PR for add support for ssh commit signing](https://github.com/go-gitea/gitea/pull/17743)
  * TODO: link to their blog once it's released
* [Fedora update request for git](https://bugzilla.redhat.com/show_bug.cgi?id=2029604)
  * TODO: remove this mention when it happens? It does have the test instructions I took
