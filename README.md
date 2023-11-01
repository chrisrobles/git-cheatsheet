# Git

## Clone a repository with HTTPS

`git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY`

## Clone a Repository with SSH

### in Linux

1) [Generate ssh key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#adding-your-ssh-key-to-the-ssh-agent) (if none exists)

   `ssh-keygen -t ed25519 -C "your_email@example.com"`
   
   or for rsa / legacy system

   `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
   1) Add [passphrase](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/working-with-ssh-key-passphrases) when prompted (recommended)

2) Start the ssh-agent

   `eval "$(ssh-agent -s)"`
   [May need to use different command](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent?platform=linux#adding-your-ssh-key-to-the-ssh-agent)

3) Add ssh key to ssh-agent

   `ssh-add ~/.ssh/id_ed25519`
   or whatever the name of your ssh key is

4) Copy ssh key

    Linux: `cat ~/.ssh/id_ed25519.pub | xclip -selection clipboard`

    WSL: `cat ~/.ssh/id_ed25519.pub | clip.exe`

5) Add ssh key to remote repository

   - GitHub
      1. [Go to SSH and GPG keys under "Access" in profile settings](https://github.com/settings/profile)
      2. Paste in ssh key
      3. Add SSH key

### in Mac

1) [Generate ssh key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#adding-your-ssh-key-to-the-ssh-agent) (if none exists)

   `ssh-keygen -t ed25519 -C "your_email@example.com"`
  
   or for rsa / legacy system
  
   `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
   1) Add [passphrase](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/working-with-ssh-key-passphrases) when prompted (recommended)

2) Start the ssh-agent

   `eval "$(ssh-agent -s)"`
      [May need to use different command](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent?platform=linux#adding-your-ssh-key-to-the-ssh-agent)

4) If using Sierra 10.12.2 or later, setup ssh config
   1) Check config exists `open ~/.ssh/config`
   2) If the file doesn't exist `touch ~/.ssh/config`
   3) Add to config:
  
      ```bash
      Host github.com
      AddKeysToAgent yes
      UseKeychain yes
      IdentityFile ~/.ssh/id_ed25519
      ```

   - If no passphrase for key, you should omit the UseKeychain line
   - If you see usekeychain error, add an additional line to the configuration

      ```bash
      IgnoreUnknown UseKeychain
      ```
  
5) Add ssh key to ssh-agent

   `ssh-add --apple-use-keychain ~/.ssh/id_ed25519`
     - or whatever the name of your ssh key is
     - If no passphrase for key, run without `--apple-use-keychain`

7) Copy ssh key

   `pbcopy < ~/.ssh/id_ed25519.pub`

9) Add ssh key to remote repository

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

- origin is just the default local name for the remote repository, it can be changed

## Rebasing

You can get the best of both worlds: rebase local changes before pushing to clean up your work, but never rebase anything that you’ve pushed somewhere.

## Stash

git stash

git stash pop