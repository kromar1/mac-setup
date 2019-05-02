# New macOS set up

Steps to set up my Mac for development

## System Preferences

- Security and Privacy > Firewall > Turn On Firewall

## Finder

### Show hidden files

Keyboard shortcut in Finder: `command` + `shift` + `.`

  or

    defaults write com.apple.finder AppleShowAllFiles YES

### Show path bar

    defaults write com.apple.finder ShowPathbar -bool true

### Show status bar

    defaults write com.apple.finder ShowStatusBar -bool true

### Change the computer name

    sudo scutil --set HostName name-you-want

## Homebrew

    /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

  make sure everything is fine

    brew doctor

## Configure git

### `~/.gitconfig`

    [user]
      name   = Firstname Lastname
      email  = you@example.com
    [github]
      user   = username
    [credential]
      helper = osxkeychain
    [pull]
      rebase = true

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

### Nord terminal colour theme

- [Download](https://github.com/arcticicestudio/nord-terminal-app) .terminal file
- Start Terminal.app and open the Preferences
- Switch to the Profiles tab located in the topbar
- Click on the gear icon and select the Import... entry
- Import the downloaded Nord.terminal file





### Exclude cache folders from time machine backup

    tmutil addexclusion "~/Library/Caches"
    tmutil addexclusion "/Libarary/Caches"

## Node.js

### Download NVM

    curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash

### Install Node

    nvm install node

    nvm use node

#### Later on to update Node

    nvm install node

  or

    nvm install node --reinstall-packages-from=node

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

#### Chrome extensions

- [Angular state inspector](https://chrome.google.com/webstore/detail/angular-state-inspector/nelkodgfpddgpdbcjinaaalphkfffbem)
- [Augury](https://chrome.google.com/webstore/detail/augury/elgalmkoelokbchhkhacckoklkejnhcd)
- [axe](https://chrome.google.com/webstore/detail/axe/lhdoppojpmngadmnindnejefpokejbdd)
- [ColorPick Eyedropper](https://chrome.google.com/webstore/detail/colorpick-eyedropper/ohcpnigalekghcmgcdcenkpelffpdolg)
- [Full Page Screen Capture](https://chrome.google.com/webstore/detail/full-page-screen-capture/fdpohaocaechififmbbbbbknoalclacl)
- [Grammarly for Chrome](https://chrome.google.com/webstore/detail/grammarly-for-chrome/kbfnbcaeplbcioakkpcpgfkobkghlhen)
- [IE Tab](https://chrome.google.com/webstore/detail/ie-tab/hehijbfgiekmjfkfjpbkbammjbdenadd)
- [JSON Formatter](https://chrome.google.com/webstore/detail/json-formatter/bcjindcccaagfpapjjmafapmmgkkhgoa)
- [Redux DevTools](https://chrome.google.com/webstore/detail/redux-devtools/lmhkpmbekcpmknklioeibfkpmmfibljd)
- [Wappalyzer](https://chrome.google.com/webstore/detail/wappalyzer/gppongmhjkpfnbhagpmjfkannfbllamg)
- [WhatFont](https://chrome.google.com/webstore/detail/whatfont/jabopobgcpjmedljpbcaablpmlmfcogm?hl=en)

### Firefox

    brew cask install firefox

### Install FiraCode font

    brew tap caskroom/fonts
    brew cask install font-fira-code

### Other Fonts

[San Francisco](https://developer.apple.com/fonts/)

or

[Source Code Pro](https://github.com/powerline/fonts/tree/master/SourceCodePro)


### Visual Studio Code

    brew cask install visual-studio-code

#### Install the VS Code CLI Command

  Open the Command Palette (⇧⌘P) and type 'shell command' to find the Shell Command: Install 'code' command in PATH command

#### List installed extensions

    code --list-extensions | xargs -L 1 echo code --install-extension

#### Install extensions

    code --install-extension Angular.ng-template
    code --install-extension arcticicestudio.nord-visual-studio-code
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
    code --install-extension eg2.vscode-npm-script
    code --install-extension esbenp.prettier-vscode
    code --install-extension flowtype.flow-for-vscode
    code --install-extension formulahendry.code-runner
    code --install-extension GregorBiswanger.json2ts
    code --install-extension Gruntfuggly.todo-tree
    code --install-extension infinity1207.angular2-switcher
    code --install-extension JamesBirtles.svelte-vscode
    code --install-extension jasonnutter.search-node-modules
    code --install-extension jaymorrow.NodeAssertionSnippets
    code --install-extension joelday.docthis
    code --install-extension mhutchie.git-graph
    code --install-extension Mikael.Angular-BeastCode
    code --install-extension mikestead.dotenv
    code --install-extension miramac.vscode-exec-node
    code --install-extension ms-kubernetes-tools.vscode-kubernetes-tools
    code --install-extension ms-mssql.mssql
    code --install-extension ms-python.python
    code --install-extension ms-vscode.csharp
    code --install-extension ms-vscode.vscode-typescript-tslint-plugin
    code --install-extension msjsdiag.debugger-for-chrome
    code --install-extension PeterJausovec.vscode-docker
    code --install-extension pflannery.vscode-versionlens
    code --install-extension PKief.material-icon-theme
    code --install-extension Prisma.vscode-graphql
    code --install-extension redhat.vscode-yaml
    code --install-extension taniarascia.new-moon-vscode
    code --install-extension vscode-icons-team.vscode-icons
    code --install-extension vsmobile.vscode-react-native
    code --install-extension xabikos.JavaScriptSnippets
    code --install-extension xabikos.ReactSnippets
    code --install-extension zhuangtongfa.Material-theme

## Angular CLI

    npm install -g @angular/cli

## React

    npm install -g create-react-app

or use npx

    npx create-react-app my-app

## Other dev tools

### Prettier

    npm install -g prettier

### Typescript

    npm install -g typescript

### TSLint

    npm install -g tslint

### ESLint

    npm install -g eslint

### JSHint

    npm install -g jshint

### JSDoc

    npm install -g jsdoc

### UglifyJS

    npm install -g uglify-js

### Karma

    npm install -g karma-cli

Note: this still requires local installation using

    npm install karma --save-dev

### Browserify

    npm install -g browserify

### http-server

    npm install -g http-server

### Gulp

    npm install --global gulp-cli

## PostgreSQL

### Install

    brew install postgresql

### Start background service (restarts at login)

    brew services start postgresql

or, if you don't want/need a background service you can just run

    pg_ctl -D /usr/local/var/postgres start

### Stop

    brew services stop postgresql

### To migrate existing data from a previous major version of PostgreSQL run

    brew postgresql-upgrade-database
