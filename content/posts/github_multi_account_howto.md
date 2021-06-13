---
title: "How to Work with Multiple Github Account with a Single Computer"
date: 2021-06-12
# weight: 1
# aliases: ["/first"]
tags: ["github", "git"]
author: "Yibin Lin"
# author: ["Me", "You"] # multiple authors
showToc: False
TocOpen: false
draft: False
hidemeta: false
hideSummary: true
comments: false
# description: ""
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
searchHidden: true
cover:
    image: "<image path/url>" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page

---

## Steps to Set-Up Per-directory Github Information

- [StackOverflow Answer to "Multiple github accounts on the same computer?"](https://stackoverflow.com/questions/3860112/multiple-github-accounts-on-the-same-computer)
  - `Pavan`'s answer is very helpful;
  - The key is that you can use `~/.ssh/config` to set up an alias of github, such as `github-my-org` (using your new account and new key to connect) and then you will need to replace the git remote string:
    - from `git@github.com:username/repo.git`
    - to: `git@github-my-org:username/repo.git`
    - So that a particular repo will use your new key to push to Github.
  - If `ssh` keeps trying different private keys than the one you specified in `~/.ssh/config`, then you may need:
    - `IdentitiesOnly yes` in the config to only try the one key file you mentioned.
    - [Details](https://superuser.com/questions/268776/how-do-i-configure-ssh-so-it-doesnt-try-all-the-identity-files-automatically)
  - But the `.gitconfig` part is not working for me (I have `git 2.30.x`)
    - Still in the local directory git will still use the settings from `git config` command line, not local `./.gitconfig`'s settings.
- Configure right username and email:
  - (At the repo directory):
  - `git config user.name USERNAME`
  - `git config user.email useremail@example.com`
  - Explanation: running `git config` locally will actually change local default config file: `./.git/config` so that the command line setting is preserved.
    - [More explanation from Bitbucket](https://www.atlassian.com/git/tutorials/setting-up-a-repository/git-config)
