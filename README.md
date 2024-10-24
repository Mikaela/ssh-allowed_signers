# allowed_signers file for SSH/git

Git 2.34 brings support for signing commits with SSH key and having a
SSH-compatible smartcard, I have to try this. It likely getting more common in
the future doesn't hurt either and I have
[pgp-alt-wot](https://gitea.blesmrt.net/Mikaela/pgp-alt-wot) which does about
the same for PGP.

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Where to find keys](#where-to-find-keys)
- [Quick howto](#quick-howto)
- [Mirrors](#mirrors)
- [Further reading](#further-reading)
  - [Forge support](#forge-support)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Where to find keys

- GitHub, Giteas and GitLabs expose user public keys (without useful names) when
  you append a `.keys` after their profile page
  - For example: https://github.com/Mikaela.keys
    https://codeberg.org/Aminda.keys https://gitlab.com/Mikaela.keys
- Good ideas are made to be copied, so maybe there will be more repositories
  like this :wink:

## Quick howto

I don't mean this to be used directly, only to be took inspiration from. See the
first link in further reading.

```bash
mkdir -p ~/src/codeberg.org/Aminda
cd ~/src/codeberg.org/Aminda
git clone https://codeberg.org/Aminda/ssh-allowed_signers.git
git config --global gpg.ssh.allowedSignersFile ~/src/codeberg.org/Aminda/ssh-allowed_signers/allowed_signers
```

Git commands, such as `git verify-commit --raw HEAD` or
`git log --show-signature`, should now recognised commits signed with keys I
have allowed. In the last command it's fine to remove `--global` to only affect
the single repository you are on (while I haven't tested this), should that
repository be something only I am signing in or something I need to verify
otherwise enough to list it here.

On the last command, `git config` turns it into absolute path, while manually
edited `.gitconfig` can literally have the above. I wonder if the command would
understand `--` before the file, but not enough to actually try it :smiley:

## Mirrors

- https://codeberg.org/AMinda/ssh-allowed_signers
- https://gitea.blesmrt.net/mikaela/ssh-allowed_signers
- https://github.com/mikaela/ssh-allowed_signers
- https://gitlab.com/mikaela/ssh-allowed_signers
- https://git.com.de/mikaela/ssh-allowed_signers &
  http://gitea.qzzf2qcfbhievvs5nzkccuwddroipy62qjocqtmgcgh75vd6w57m7yad.onion/Mikaela/ssh-allowed_signers

## Further reading

- [Caleb Hearth: Signing Git Commits with Your SSH Key](https://calebhearth.com/sign-git-with-ssh)
  ([web.archive.org](https://web.archive.org/web/20211117182628/https://calebhearth.com/sign-git-with-ssh))
  inspired me to try this
- [Andrew Ayer: It's Now Possible To Sign Arbitrary Data With Your SSH Keys](https://www.agwa.name/blog/post/ssh_signatures)
  instructs on signing and verifying files outside of git

### Forge support

- 🥇
  [Gitea v1.16.0 brought support for SSH signed commits on 2022-01-30.](https://blog.gitea.io/2022/02/gitea-1.16.0-and-1.16.1-released/)
  ([tag](https://github.com/go-gitea/gitea/releases/tag/v1.16.0))
  - [Their Git hosting comparison also includes SSH Signed Commits](https://docs.gitea.io/en-us/comparison/#code-management).
  - [The first release of Forĝejo was 1.18](https://forgejo.org/2022-12-29-release-v1-18-0/),
    so it had support since the beginning :tada:.
- 🥈
  [GitHub started supporting SSH signed commits on 2022-08-23](https://github.blog/changelog/2022-08-23-ssh-commit-verification-now-supported/).
  - [About commit signature verification](https://docs.github.com/en/authentication/managing-commit-signature-verification/about-commit-signature-verification#ssh-commit-signature-verification).
- 🥉
  [GitLab 15.7 started supporting SSH signatures on 2022-12-22](https://about.gitlab.com/releases/2022/12/22/gitlab-15-7-released/).
  - [Sign commits with SSH keys](https://docs.gitlab.com/ee/user/project/repository/ssh_signed_commits/).
