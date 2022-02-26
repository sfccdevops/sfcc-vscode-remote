ARG VARIANT=16-bullseye
FROM mcr.microsoft.com/vscode/devcontainers/javascript-node:0-${VARIANT}

LABEL maintainer "Peter Schmalfeldt <peter@redvanworkshop.com>"
LABEL description="SFCC VS Code Remote Container"
LABEL vendor="Red Van Workshop"
LABEL version="1.0.0"

# Support Signed Commit Messages
RUN sudo apt-get update \
    && sudo apt-get install gnupg2 -y

# Install helpful scripts
RUN sudo apt-get install exa wget -y

# Copy Shell Scripts to Container
RUN mkdir -p /usr/local/lib/sfcc-remote
COPY docker-assets/scripts/* /usr/local/lib/sfcc-remote
RUN sudo chmod +x /usr/local/lib/sfcc-remote/*

# Copy Fonts for Nicer Terminal
COPY docker-assets/fonts/*.ttf /usr/local/share/fonts

# Copy / Replace Dot Files
COPY docker-assets/dotfiles/.* /home/node

# Configure Git to use Global .gitattributes to prevent EOL and Whitespace Conflicts
RUN su node -c "git config --global core.attributesfile /home/node/.gitattributes"

# Enable Node Version Manager
RUN su node -c "umask 0002 && . /usr/local/share/nvm/nvm.sh"

# Persist Bash History
RUN SNIPPET="export PROMPT_COMMAND='history -a' && export HISTFILE=/commandhistory/.bash_history" \
    && mkdir /commandhistory \
    && touch /commandhistory/.bash_history \
    && chown -R node /commandhistory \
    && echo $SNIPPET >> /home/node/.bashrc

# Persist VS Code Extensions
RUN mkdir -p /home/node/.vscode-server/extensions \
    /home/node/.vscode-server-insiders/extensions \
    && chown -R node \
    /home/node/.vscode-server \
    /home/node/.vscode-server-insiders

# Add Support for Live Share
RUN wget -O ~/vsls-reqs https://raw.githubusercontent.com/MicrosoftDocs/live-share/master/scripts/linux-prereqs.sh \
    && chmod +x ~/vsls-reqs \
    && ~/vsls-reqs
