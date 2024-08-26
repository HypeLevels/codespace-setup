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

RUN git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/themes/powerlevel10k

COPY .p10k.zsh ~/.p10k.zsh

RUN echo 'if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then\n' \
         '  source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"\n' \
         'fi\n' | cat - ~/.zshrc > temp && mv temp ~/.zshrc && \
    chsh -s $(which zsh) && \
    sed -i 's/ZSH_THEME="robbyrussell"/ZSH_THEME="powerlevel10k\/powerlevel10k"/g' ~/.zshrc && \
    echo '[[ ! -f ~/.p10k.zsh ]] || source ~/.p10k.zsh' >> ~/.zshrc

SHELL ["/bin/zsh", "-c"]
