# My configuration files
- Fedora Workstation
- Asus VivoBook\_ASUSLaptop X580GD\_N580GD


## Setup git default branch name
```bash
$ git config --global init.defaultBranch main
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

