# Install Brew

- Update XCode
  - Run the following command in terminal:
    - `xcode-select —install`
- Install Brew
  - Run the installation [command](https://brew.sh/)
      - `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`
- Install M2 casks
  - `brew install pycharm anki app-cleaner docker dropbox google-chrome github iterm2 jumpcut jupyter-notebook-ql jupyter-notebook-viewer microsoft-office skype sublime-text tor-browser vlc wireshark --cask`

---

# Setup Sublime MarkdownLivePreview

- [Install Package Control](https://packagecontrol.io/installation)
- [Install MarkdownLivePreview](https://packagecontrol.io/packages/MarkdownLivePreview)

---

# Create .zshrc aliases

- Create .zshrc file
  - `touch ~/.zshrc`
- Open the .zshrc file
  - `open ~/.zshrc`
- Copy and Paste into .zshrc file
  - ```
    # -------
    # Aliases
    # -------
    alias ll="ls -al"
    alias clr="clear" # Clear your terminal screen
    alias o="open ." # Open the current directory in Finder
    alias showFiles='defaults write com.apple.Finder AppleShowAllFiles true; killall Finder'
    alias hideFiles='defaults write com.apple.Finder AppleShowAllFiles false; killall Finder'
    alias desktop="cd ~/Desktop"
    alias dbox="cd ~/Dropbox/python\ development"
    alias aliases="cd ~; /Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl .zshrc"
    ```
---

# Show Invisible Files on Mac

- Assuming the aliasses have been added to the .zshrc file, run the following command
  - `showFiles`
- The inverse of this is:
  - `hideFiles`

---

# [Set Up github ssh](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

- Generate an ssh key
  - `ssh-keygen -t ed25519 -C "YOUREMAIL@RANDOM.com"`
- Save the ssh key
  - `/Users/YOUR_USERNAME/.ssh/github_id_ed25519`
- Start ssh-agent
  - `eval "$(ssh-agent -s)"`
- Create .ssh/config
  - `touch ~/.ssh/config`
- Open .ssh/config
  - `nano ~/.ssh/config`
- Copy the below config settings to .ssh/config
  - ```
    Host *.github.com
      AddKeysToAgent yes
      UseKeychain yes
      IdentityFile ~/.ssh/github_id_ed25519
    ```
- Add ssh key to keychain on Mac
  - `ssh-add --apple-use-keychain ~/.ssh/github_id_ed25519`
- [Add the ssh key to github](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
  - Copy key to clipboard and paste into GitHub
    - `pbcopy < ~/.ssh/github_id_ed25519.pub`
- Test Key
  - `ssh -T git@github.com`

---

# Setup Python

- Install [Anaconda](https://www.anaconda.com/products/distribution)
  - Add Conda to path
- Open a terminal and upgrade Conda
  - `conda update --all`
- Disable auto_activate_base
  - `conda config --set auto_activate_base false`
- Open a new terminal and create a new Conda python 3.10 environment
  - `conda activate base`
  - `conda create -n py310 python=3.10.8`
  - `ipython kernel install --user --name py310 --display-name py310`
- Add Conda Forge to channels
  -  ```
     conda config --add channels conda-forge
     conda config --set channel_priority strict
     ```

---

# Install [Poetry](https://python-poetry.org/docs/#installing-with-the-official-installer)
- Run the following commands in a terminal window
  - `conda activate py310`
  - `curl -sSL https://install.python-poetry.org | POETRY_PREVIEW=1 python -`
- Add poetry to PATH
  - `export PATH="/Users/YOUR_USERNAME/.local/bin:$PATH"`
