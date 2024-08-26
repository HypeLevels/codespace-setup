FROM oven/bun

RUN apt-get update && \
    apt-get install -y \
    fontconfig \
    wget \
    unzip && \
    rm -rf /var/lib/apt/lists/*

RUN wget https://download.jetbrains.com/fonts/JetBrainsMono-2.304.zip -O /tmp/JetBrainsMono.zip && \
    unzip /tmp/JetBrainsMono.zip -d /usr/share/fonts/truetype/jetbrains-mono/ && \
    fc-cache -f -v && \
    rm /tmp/JetBrainsMono.zip
