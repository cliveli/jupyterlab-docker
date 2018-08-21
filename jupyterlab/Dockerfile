FROM node:10-alpine

# Install required packages
RUN apk add --update-cache --virtual=.build-dependencies alpine-sdk \
    python-dev \
    py-pip
    # python3-dev

RUN pip2 install --upgrade pip
    # python3 -m pip install --upgrade pip --force-reinstall

# Install Jupyter Widgets
# RUN pip install jupyter
# RUN pip install ipywidgets
# RUN jupyter nbextension enable --py widgetsnbextension

# Install JupyterLab
# RUN pip install jupyterlab && jupyter serverextension enable --py jupyterlab
RUN pip2 install jupyterlab && jupyter serverextension enable --py jupyterlab

# TODO try pip3
# https://github.com/jupyterlab/jupyterlab#pip
# OR https://hub.docker.com/r/frolvlad/alpine-python3/~/dockerfile/
# apk add python3 && python3 -m ensurepip

# Install javascript kernel (require python2)
RUN npm --unsafe-perm i -g ijavascript && ijsinstall --install=global


# RUN apk add python3-dev && python3 -m pip install --upgrade pip --force-reinstall
RUN apk add python3-dev && python3 -m pip install --upgrade pip --force-reinstall && \
    python3 -m pip install ipykernel && \
    python3 -m ipykernel install --user
# https://ipython.readthedocs.io/en/stable/install/kernel_install.html


# WIP TODO try install jupyterlab w/ py3 without damage jupyterlab w/ py2
# multistage build? -> is kernel installed by COPYING FILES? or CONFIGS?
# Install JupyterLab
# RUN pip3 install jupyterlab && jupyter serverextension enable --py jupyterlab

# NOTE pip -> pip3; pip2
# NOTE python -> python2; python3
# NOTE ipython -> ipython3

ENV LANG=C.UTF-8
ENV HOME /root
ENV SERVER_PORT 8888

EXPOSE $SERVER_PORT
CMD jupyter lab --ip=* --port=$SERVER_PORT --no-browser --notebook-dir=$HOME --allow-root
