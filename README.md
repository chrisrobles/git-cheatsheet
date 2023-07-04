# Git

## Clone a repository with HTTPS

`git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY`

## Clone a Repository with SSH in Linux

1) [Generate ssh key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#adding-your-ssh-key-to-the-ssh-agent) (if none exists)
  `ssh-keygen -t ed25519 -C "your_email@example.com"`
  or for rsa / legacy system
  `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
   1) Add [passphrase](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/working-with-ssh-key-passphrases) (recommended)
2) Start the ssh-agent
   1) `eval "$(ssh-agent -s)"`
      [May need to use different command](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent?platform=linux#adding-your-ssh-key-to-the-ssh-agent)
3) Add ssh key to ssh-agent
  `ssh-add ~/.ssh/id_ed25519`
  or whatever the name of your ssh key is
4) Copy ssh key
  Linux: `clip < ~/.ssh/id_ed25519.pub`
  WSL: `cat ~/.ssh/id_ed25519.pub | clip.exe`
5) Add ssh key to remote repository
   - GitHub
      1. [Go to SSH and GPG keys under "Access" in profile settings](https://github.com/settings/profile)
      2. Paste in ssh key
      3. Add SSH key

## Branch

- With a -m or -M option, the branch will be renamed to the argument after the option
  - `git branch -m main`

## Push

- -u option: after pushing your local branch with the -u option, this local branch will be automatically linked with the remote branch, and you can use git pull / push without any arguments
  - `git push -u origin main`

## Check origin

`git remote -v`

## Change a remote repository's URL

`git remote set-url origin [url]`

- origin is just a local name for the remote repository, it can be changed

## Rebasing
