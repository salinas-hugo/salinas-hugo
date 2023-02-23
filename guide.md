# Howto guide
## Remaping of keys
    mkdir ~/Library/KeyBindings/ \
    && vi ~/Library/KeyBindings/DefaultKeyBinding.dict
    {
      "\UF729"  = moveToBeginningOfParagraph:; // home
      "\UF72B"  = moveToEndOfParagraph:; // end
      "$\UF729" = moveToBeginningOfParagraphAndModifySelection:; // shift-home
      "$\UF72B" = moveToEndOfParagraphAndModifySelection:; // shift-end
      "^\UF729" = moveToBeginningOfDocument:; // ctrl-home
      "^\UF72B" = moveToEndOfDocument:; // ctrl-end
      "^$\UF729" = moveToBeginningOfDocumentAndModifySelection:; // ctrl-shift-home
      "^$\UF72B" = moveToEndOfDocumentAndModifySelection:; // ctrl-shift-end
    }

## Install xcode
    xcode-select --install

## Install brew
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

## Install zsh
    brew install zsh

## Install ohmyzsh
    sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

## Install git and configuration
    brew install git
    git config --global user.name "Hugo Salinas" \
    && git config --global user.email "hugo.salinas@striderintel.com" \
    && git config --global color.ui "auto" \
    && git config --global alias.tree "log --graph --decorate --pretty=online --abbrev-commit" \
    && git config --global alias.st "status" \
    && git config --global alias.ci "commit -v" \
    && git config --global alias.co "checkout" \
    && git config --global alias.br "branch" \
    && git config --global alias.unstage "reset HEAD --" \
    && git config --global alias.discard "checkout --" \
    && git config --global alias.last "log -1 HEAD" \
    && git config --global core.editor "vim" \
    && git config --global core.autocrlf "input" \
    && git config --global core.fileMode "false" \
    && git config --global push.default "simple"

## Install docker
    brew install --cask docker

## Install python and virtualenv
    brew install python@3.8
    pip3 install --upgrade pip
    pip3 install virtualenv

## Install general pip reqs
    pip3 install black

## virtualenv mini howto
### create the venv folder
    cd project_folder
    virtualenv venv
    virtualenv -p /opt/homebrew/opt/python@3.8/bin/python3.8 venv
### activate
    source venv/bin/activate
### create your reqs
    pip freeze > requirements.txt
### install reqs
    pip install -r requirements.txt
### deactivate
    deactivate
### clean a venv
    pip uninstall -y -r <(pip freeze)
    
## Install requirements for ribs-ui
    # needed by pymssql
    # pip install cython # only for python3.9
    # brew install freetds # only for python3.9
    # pylibmc
    brew install libmemcached
    then
        export LDFLAGS="-L/opt/homebrew/opt/libmemcached/lib"
        export CFLAGS="-I/opt/homebrew/opt/libmemcached/include"
    or
        pip install pylibmc --install-option="--with-libmemcached=/opt/homebrew/opt/libmemcached/"

### Install aggs
#### clone aggs
    git clone git@github.com:strider-technologies/aggs.git
#### install it in dev mode
    pip3 install -e aggs/

#### Install rust
    brew install rust
    pip3 install setuptools_rust

## Python 3.8 in Amazon Linux 2

    sudo amazon-linux-extras enable python3.8
    sudo yum install python3.8
    sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.8 1

    python3.8 --version
    python --version

    sudo pip3.8 install virtualenv
