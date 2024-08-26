FROM oven/bun

RUN apt-get update && \
    apt-get install -y \
    fontconfig \
    wget \
    unzip \
    zsh \
    git \
    locales locales-all && \
    rm -rf /var/lib/apt/lists/*

ENV LC_ALL en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US.UTF-8

RUN wget https://github.com/ryanoasis/nerd-fonts/releases/download/v3.2.1/JetBrainsMono.zip -O /tmp/JetBrainsMono.zip && \
    unzip /tmp/JetBrainsMono.zip -d /usr/share/fonts/truetype/jetbrains-mono/ && \
    fc-cache -f -v && \
    rm /tmp/JetBrainsMono.zip

RUN sh -c "$(wget https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)" --unattended

RUN chsh -s $(which zsh)

RUN sed -i 's/ZSH_THEME="robbyrussell"/ZSH_THEME="agnoster"/g' ~/.zshrc

SHELL ["/bin/zsh", "-c"]
