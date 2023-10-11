ARG GO_VERSION=1.21
ARG ALPINE_VERSION=3.18

FROM docker.io/library/golang:${GO_VERSION}-alpine${ALPINE_VERSION}

# Install packages and Go language server
RUN apk add -q --update --progress --no-cache git sudo openssh-client zsh
RUN go install golang.org/x/tools/gopls@latest

RUN sh -c "$(wget -O- https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)" "" --unattended &> /dev/null
ENV ENV="/root/.ashrc" \
    ZSH=/root/.oh-my-zsh \
    EDITOR=vi \
    LANG=en_US.UTF-8
RUN printf 'ZSH_THEME="robbyrussell"\nENABLE_CORRECTION="false"\nplugins=(git copyfile extract colorize dotenv encode64 golang)\nsource $ZSH/oh-my-zsh.sh' > "/root/.zshrc"
RUN echo "exec `which zsh`" > "/root/.ashrc"
