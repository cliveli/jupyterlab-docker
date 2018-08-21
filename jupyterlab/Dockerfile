FROM node:10-alpine

RUN apk add --update-cache --virtual=.build-dependencies alpine-sdk \
    python-dev \
    py-pip \
    python3-dev

RUN python3 -m pip install --upgrade pip && \
    python2 -m pip install --upgrade pip

RUN python3 -m pip install jupyterlab && \
    jupyter serverextension enable --py jupyterlab && \
    python2 -m pip install ipykernel && \
    python2 -m ipykernel install --user

RUN npm --unsafe-perm i -g ijavascript && \
    ijsinstall --install=global

# ===

# RUN python2 -m pip install --upgrade pip && \
    # python2 -m pip install jupyterlab && \
    # jupyter serverextension enable --py jupyterlab

# RUN npm --unsafe-perm i -g ijavascript && \
#     ijsinstall --install=global

# RUN apk add python3-dev && \
    # python3 -m pip install --upgrade pip --force-reinstall && \
    # python3 -m pip install ipykernel && \
    # python3 -m ipykernel install --user

ENV LANG=C.UTF-8
ENV HOME /root
ENV SERVER_PORT 8888

EXPOSE $SERVER_PORT
CMD jupyter lab --ip=* --port=$SERVER_PORT --no-browser --notebook-dir=$HOME --allow-root
