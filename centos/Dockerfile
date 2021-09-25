# Build Command:
# docker build --build-arg HTTP_PROXY=http://192.168.1.119:7890 -t centos-server .

FROM centos

RUN \
    # yum update -y && \
    yum install -y \
    wget \
    git \
    tmux \
    vim \
    zsh \
    rsync

# RUN \
#     yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm && \
#     yum update -y && \
#     yum install -y htop


# FUCK China's GFW
#
ARG github_base="https://github.com"
# ARG github_base="https://github.com.cnpmjs.org"

# vim_runtime
RUN \
    cd ~ && \
    git clone --depth 1 ${github_base}/ktw361/vim_runtime.git .vim_runtime && \
    cd .vim_runtime && \
    bash install_awesome_vimrc.sh

# dotfiles
RUN \
    cd ~ && \
    git clone $github_base/ktw361/dotfiles.git && \
    cd dotfiles && \
    bash minimal_install.sh

# Oh-my-zsh & plugins
RUN sh ~/dotfiles/oh-my-zsh-install.sh
RUN \
    git clone $github_base/agkozak/zsh-z ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-z && \
    git clone $github_base/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions && \
    git clone $github_base/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting && \
    cp ~/dotfiles/zshrc ~/.zshrc

# Install gogs from base environment
#
# gogs
# RUN \
#     cd /tmp && \
#     wget https://dl.gogs.io/0.12.3/gogs_0.12.3_linux_amd64.tar.gz && \
#     tar -xzvf gogs_0.12.3_linux_amd64.tar.gz && \
#     cd gogs_0.12.3_linux_amd64
# Add user "git", needed for gogs
# RUN useradd -ms /bin/zsh git


# Clash


WORKDIR /root
CMD ["/bin/bash"]
