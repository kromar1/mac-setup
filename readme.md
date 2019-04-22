# New macOS set up

Steps to set up my Mac for development

## System Preferences

- Security and Privacy > Firewall > On
- Security and Privacy > General > App Store and identified developers

## Finder

### Show hidden files

Keyboard shortcut in Finder: `command` + `shift` + `.`

    defaults write com.apple.finder AppleShowAllFiles YES

### Show path bar

    defaults write com.apple.finder ShowPathbar -bool true

### Show status bar

    defaults write com.apple.finder ShowStatusBar -bool true

### Change the computer name

    sudo scutil --set HostName name-you-want

## Homebrew

    /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

Make sure all is good at this point

    brew cask install firefox

## PostgreSQL

### Install

    brew install postgresql

### Start

    brew services start postgresql

### Stop

    brew services stop postgresql

### Commmon commands in psql

`\q` Exit psql connection

`\c` Connect to a new database

`\dt` List all tables

`\du` List all roles

`\list` List databases

## Configure git

### `~/.gitconfig`

    [user]
      name   = Firstname Lastname
      email  = you@example.com
    [github]
      user   = username
    [credential]
      helper = osxkeychain

## Terminal

### `~/.bash_profile`

    export CLICOLOR=1
    export LSCOLORS=GxFxCxDxBxegedabagaced

### Customise the terminal prompt

#### Super simple version

    export PS1="\n\w\n$ "

#### Or include git branch

    parse_git_branch() {
      git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
    }

    export PS1="\[\033[36m\]\u\[\033[m\]@\[\033[32m\]\h:\[\033[33;1m\]\w\$(parse_git_branch)\[\033[m\]\$ "

### Aliases

      alias ll='ls -al'

### Font

`SF Mono Light 16pt`

Download [here](https://developer.apple.com/fonts/)

or

`Source Code Pro Light 17pt`

Download [here](https://github.com/powerline/fonts/tree/master/SourceCodePro)

## Node.js

### Download Node

    curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash

    nvm install node

    nvm use node

#### Later on to update Node

    nvm install node --reinstall-packages-from=node

## Gulp

    npm install --global gulp-cli

## Angular CLI

    npm install -g @angular/cli

## React

    npm install -g create-react-app

Or use npx

    npx create-react-app my-app

## SSH key

### List existing ssh keys

    ls -al ~/.ssh

### Generate a new one

    ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

#### Copy key to clipboard

    pbcopy < ~/.ssh/id_rsa.pub

#### Test SSH connection

e.g connect to GitHub

    ssh -T git@github.com

## Install applications and plugins

### Chrome

    brew cask install google-chrome

### Firefox

    brew cask install firefox

### Install FiraCode font

    brew tap caskroom/fonts
    brew cask install font-fira-code

### Visual Studio Code

    brew cask install visual-studio-code

#### Install the VS Code CLI Command

    Open the Command Palette (⇧⌘P) and type 'shell command' to find the Shell Command: Install 'code' command in PATH command

#### List installed extensions

    code --list-extensions | xargs -L 1 echo code --install-extension

#### Install extensions

    code --install-extension Angular.ng-template
    code --install-extension Arjun.swagger-viewer
    code --install-extension bierner.markdown-preview-github-styles
    code --install-extension ChakrounAnas.turbo-console-log
    code --install-extension christian-kohler.npm-intellisense
    code --install-extension christian-kohler.path-intellisense
    code --install-extension clinyong.vscode-css-modules
    code --install-extension CoenraadS.bracket-pair-colorizer
    code --install-extension DavidAnson.vscode-markdownlint
    code --install-extension dbaeumer.jshint
    code --install-extension dbaeumer.vscode-eslint
    code --install-extension donjayamanne.githistory
    code --install-extension DotJoshJohnson.xml
    code --install-extension dzannotti.vscode-babel-coloring
    code --install-extension eg2.tslint
    code --install-extension eg2.vscode-npm-script
    code --install-extension esbenp.prettier-vscode
    code --install-extension flowtype.flow-for-vscode
    code --install-extension formulahendry.code-runner
    code --install-extension GregorBiswanger.json2ts
    code --install-extension infinity1207.angular2-switcher
    code --install-extension jasonnutter.search-node-modules
    code --install-extension jaymorrow.NodeAssertionSnippets
    code --install-extension joelday.docthis
    code --install-extension mermade.openapi-lint
    code --install-extension Mikael.Angular-BeastCode
    code --install-extension mikestead.dotenv
    code --install-extension miramac.vscode-exec-node
    code --install-extension ms-mssql.mssql
    code --install-extension ms-python.python
    code --install-extension ms-vscode.csharp
    code --install-extension ms-vscode.powershell
    code --install-extension ms-vscode.vscode-typescript-tslint-plugin
    code --install-extension msjsdiag.debugger-for-chrome
    code --install-extension nathanchapman.JavaScriptSnippets
    code --install-extension PeterJausovec.vscode-docker
    code --install-extension pflannery.vscode-versionlens
    code --install-extension PKief.material-icon-theme
    code --install-extension quicktype.quicktype
    code --install-extension redhat.vscode-yaml
    code --install-extension sidneys1.gitconfig
    code --install-extension taniarascia.new-moon-vscode
    code --install-extension vscode-icons-team.vscode-icons
    code --install-extension vsmobile.vscode-react-native
    code --install-extension waderyan.nodejs-extension-pack
    code --install-extension xabikos.JavaScriptSnippets
    code --install-extension xabikos.ReactSnippets
    code --install-extension zhuangtongfa.Material-theme
