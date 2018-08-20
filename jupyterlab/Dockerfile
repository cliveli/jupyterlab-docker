FROM node:10-alpine

# Install required packages
RUN apk add --update-cache --virtual=.build-dependencies alpine-sdk \
    python-dev \
    py-pip
    # python3

# Install Jupyter Widgets
# RUN pip install jupyter
# RUN pip install ipywidgets
# RUN jupyter nbextension enable --py widgetsnbextension

# Install JupyterLab
RUN pip install jupyterlab && jupyter serverextension enable --py jupyterlab

# TODO try pip3
# https://github.com/jupyterlab/jupyterlab#pip
# OR https://hub.docker.com/r/frolvlad/alpine-python3/~/dockerfile/
# apk add python3 && python3 -m ensurepip

# Install javascript kernel
RUN npm --unsafe-perm i -g ijavascript && ijsinstall --install=global

ENV LANG=C.UTF-8
ENV HOME /root
ENV SERVER_PORT 8888

EXPOSE $SERVER_PORT
CMD jupyter lab --ip=* --port=$SERVER_PORT --no-browser --notebook-dir=$HOME --allow-root
