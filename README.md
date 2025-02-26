# My configuration files
- Fedora Workstation
- Asus VivoBook\_ASUSLaptop X580GD\_N580GD

## Change hostname

```bash
$ sudo hostnamectl set-hostname "fedora-asus"
```

## Speed up dnf

```bash
$ sudo nano /etc/dnf/dnf.conf
```
append to `dnf.conf`: *max_parallel_downloads=10*
```
[main]
...
max_parallel_downloads=10
```

## Setup git default branch name
```bash
$ git config --global init.defaultBranch main
```

## Setup dotfiles repos

based on guide by [Atlassian](https://www.atlassian.com/git/tutorials/dotfiles)

```bash
git init --bare $HOME/.dotfiles
alias config='/usr/bin/git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'
config config --local status.showUntrackedFiles no
echo "alias config='/usr/bin/git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'" >> $HOME/.bashrc.d/alias

config remote add origin git@gitlab.com:majramos/dotfiles_fedora_workstation.git
config remote set-url --add origin git@github.com:Majramos/dotfiles_fedora_workstation.git
```



