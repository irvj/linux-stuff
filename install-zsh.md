## Install And Configure Zsh

### Install Zsh

    sudo apt install zsh

### Install Oh-My-Zsh

    sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

### Install powerlevel10k

    git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k

Edit .zshrc to use powerlevel10k theme.

    ZSH_THEME="powerlevel10k/powerlevel10k"

### Install Plugins

    git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

    git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

Add plugins in .zshrc

    plugins=(
        command-not-found
        git
        docker
        docker-compose
        extract
        pip
        sudo
        zsh-autosuggestions
        zsh-syntax-highlighting
    )

### Configure powerlevel10K

Restart terminal and follow config.
