# nft completion for zsh


This is an attempt to create zsh command completion for nft (the nftables user space utility). As I'm neither an expert in nft nor an expert in zsh, this simply works but may seem awful to experts of these domains. So please help me make this a better utility by making constructive criticism ;) .

Currently implemented subcommands: all commands listed in the man page, except the content of the add commands (eg. add rule, add set, add map, etcpp) and delete element. I'm currently working on add rule.

### how to install:

Generally you have to enable command completion first:
- [Without OhMyZsh](https://wiki.archlinux.org/index.php/Zsh#Command_completion)
- In OhMyZsh, this is done automatically.

Then you have to copy `_nft` in a directory of you choice, for this example we choose `~/.zsh`

And enable loading that completion function by adding `~/.zsh` to fpath. This must happen before `compinit` or sourcing ohmyzsh.sh
```
fpath+=$HOME/.zsh

# source ohmyzsh.sh or autoload -Uz compinit
```

### tips:

If you want to have your tables/chains/... completed when you are not a root user but using sudo, you have to add the following to your .zshrc :
```
zstyle ':completion::complete:*' gain-privileges 1
```
This will allow all completion scripts to search for completions with `sudo` if your command starts with `sudo` as well.

**BUT: this also means that will allow (unchecked) scripts to run commands as sudo, so beware of the dangers!**
