FROM holo-vim-base:1.0

MAINTAINER holo holo3344@163.com

ARG APP_UID
ARG APP_GID
ARG APP_USER
ARG APP_GROUP
ARG APP_HOME

# Create system group
RUN groupadd -g ${APP_GID} ${APP_GROUP}
RUN useradd -d ${APP_HOME}/${APP_USER} --uid ${APP_UID} --gid ${APP_GID} ${APP_USER}

WORKDIR ${APP_HOME}/${APP_USER}

COPY ./package ./

RUN chown -R ${APP_UID}:${APP_GID} ${APP_HOME}/${APP_USER}
USER ${APP_USER}


RUN cd ${APP_HOME}/${APP_USER}/holo_vim_script && ./install.sh && \
    cd ${APP_HOME}/${APP_USER}/.vim/bundle/YouCompleteMe && ./install.py --clangd-completer

WORKDIR ${APP_HOME}/${APP_USER}
