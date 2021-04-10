---
title: "Mac OS Setup"
date: 2021-04-10
# weight: 1
# aliases: ["/first"]
tags: ["setup", "configuration", "mac os x"]
author: "Yibin Lin"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
hideSummary: true
comments: false
description: "Desc Text."
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

## Setting up vim

```vimrc
" You need to import default vim settings first, e.g. syntax highlighting, etc.
source $VIMRUNTIME/defaults.vi

" Set non visual mode when mouse is dragging on vim
set mouse-=a

" set 1 tab == 4 spaces..
filetype plugin indent on
" show existing tab with 4 spaces width
set tabstop=4
" when indenting with '>', use 4 spaces width
set shiftwidth=4
" On pressing tab, insert 4 spaces
set expandtab
```

## run .bashrc at .bash_profile time

```bash
if [ -f $HOME/.bashrc ]; then
        source $HOME/.bashrc
fi
```

- [Difference between .bashrc and .bash_profile](https://apple.stackexchange.com/questions/51036/what-is-the-difference-between-bash-profile-and-bashrc)
  - Basically `.bash_profile` runs at log-in, `.bashrc` runs when you run an interactive shell
  - But in Mac OS X, it runs login shell every time (even for starting an interactive shell).

## Highlight for git branch name

- Find git-prompt.sh from official git repo
- Setup code example

```bash
source ~/.git-prompt.sh
PS1='[\u@\h \W$(__git_ps1 " \[\033[32m\](%s)\[\033[00m\]")]\$ '
```

## Double Pinyin (双拼)

1. 使用Ctrl + space来改变输入法。 Use Ctrl + space to change input source..
2. 使用Karabiner来把`Shift`键映射为`Ctrl + space`。Use [Karabiner](https://karabiner-elements.pqrs.org/) to support using `Shift` to switch between input sources.
    - 以下为映射代码 （需要放在`~/.config/karabiner/karabiner.json`，可能需要先做`Karabiner` UI里面先映射一个`simple modification`，然后`karabiner.json`文件才会被创建。）Code to do that (to be put in `~/.config/karabiner/karabiner.json`, you may need to set a `simple modification` first in `Karabiner` UI, then do this).
    - 更改文件中 `complex_modifications` => `rules` 的内容。You need to change the `complex_modifications` => `rules` as follows:

    ```json
                      "rules": [
                       {
                        "manipulators": [
                            {
                                "description": "Change left_shift to control+space when used alone",
                                "from": {
                                    "key_code": "left_shift",
                                    "modifiers": {
                                        "optional": [
                                            "any"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "left_shift"
                                    }
                                ],
                                "to_if_alone": [
                                    {
                                        "key_code": "spacebar",
                                        "modifiers": [
                                            "left_control"
                                        ]
                                    }
                                ],
                                "type": "basic"
                            }
                        ]
                    }
                ]
    ```

    - 引用 Credit: [Armin's Blog](https://arminli.com/custom-karabiner-elements-shift/)
