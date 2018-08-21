FROM node:10-alpine

# NOTE manual install

RUN apk add --update-cache --virtual=.build-dependencies alpine-sdk python3-dev

RUN python3 -m pip install --upgrade pip --force-reinstall
#   this will install pip as copy of pip3
#   Q: pip3 install --upgrade pip3

RUN pip3 install jupyterlab

# Check dependencies:
# ls -al /usr/bin/ipython*; echo ''; ls -al /usr/bin/python*;  jupyter kernelspec list;
# pip -V; ipython -V

# Install required packages
# RUN apk add --update-cache --virtual=.build-dependencies alpine-sdk \
#     python-dev \
#     py-pip \
#     python3-dev

# Install Jupyter Widgets
# RUN pip install jupyter
# RUN pip install ipywidgets
# RUN jupyter nbextension enable --py widgetsnbextension

# Install JupyterLab
# RUN python3 -m ensurepip && \
#     python3 -m pip install jupyterlab && \
#     jupyter serverextension enable --py jupyterlab
# RUN pip install jupyterlab && \
#     jupyter serverextension enable --py jupyterlab

# # install ipython3
# RUN pip3 install ipython

# TODO try pip3
# https://github.com/jupyterlab/jupyterlab#pip
# OR https://hub.docker.com/r/frolvlad/alpine-python3/~/dockerfile/
# apk add python3 && python3 -m ensurepip

# TODO multiple python kernels
# https://blog.csdn.net/xingyuzhe/article/details/79490687

# ijavascript require gyp -> require python2
RUN apk add python-dev

# Install javascript kernel
# NOTE require python2 (gyp)
RUN npm --unsafe-perm i -g ijavascript && ijsinstall --install=global

ENV LANG=C.UTF-8
ENV HOME /root
ENV SERVER_PORT 8888

EXPOSE $SERVER_PORT
CMD jupyter lab --ip=* --port=$SERVER_PORT --no-browser --notebook-dir=$HOME --allow-root
