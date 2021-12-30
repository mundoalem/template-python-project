FROM mcr.microsoft.com/vscode/devcontainers/base:ubuntu-21.04

ENV DEBIAN_FRONTEND="noninteractive"

RUN apt-get update \
    && apt-get -y install --no-install-recommends \
        make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev \
        libsqlite3-dev wget curl llvm libncursesw5-dev xz-utils tk-dev libxml2-dev \
        libxmlsec1-dev libffi-dev liblzma-dev python3-pip python3-venv fish nodejs npm \
    && apt-get autoremove -y \
    && apt-get clean autoclean -y \
    && rm -r /var/cache/* /var/lib/apt/lists/*

RUN npm install snyk@latest -g

USER vscode

ENV HOME="/home/vscode"
ENV LANG="en_GB.UTF-8"
ENV PIPENV_VERBOSITY=-1
ENV PYENV_ROOT="$HOME/.pyenv"
ENV PATH="$PYENV_ROOT/bin:$HOME/.local/bin:$PATH"

WORKDIR $HOME

RUN python3 -m pip install --upgrade pip \
    && python3 -m pip install --user pipx \
    && python3 -m pipx ensurepath \
    && pipx install pipenv \
    && pipx install black==21.12b0 \
    && pipx install mypy==0.930

RUN curl -L https://github.com/pyenv/pyenv-installer/raw/master/bin/pyenv-installer | bash \
    && eval "$(pyenv init --path)" \
    && eval "$(pyenv virtualenv-init -)" \
    && pyenv install 3.9.9

RUN echo -e 'eval $(pyenv init --path)\neval $(pyenv virtualenv-init -)' >>$HOME/.profile
