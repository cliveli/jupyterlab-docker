FROM python:alpine

# Install required packages
RUN apk add --update-cache --virtual=.build-dependencies alpine-sdk \
    nodejs \
    python-dev  \
    npm

# Install Jupyter Widgets
# RUN pip install jupyter
# RUN pip install ipywidgets
# RUN jupyter nbextension enable --py widgetsnbextension

# Install JupyterLab
RUN pip install jupyterlab && jupyter serverextension enable --py jupyterlab

# Install javascript kernel
RUN npm --unsafe-perm i -g ijavascript && ijsinstall --install=global

ENV LANG=C.UTF-8
ENV HOME /root
ENV SERVER_PORT 8888

EXPOSE $SERVER_PORT
CMD jupyter lab --ip=* --port=$SERVER_PORT --no-browser --notebook-dir=$HOME --allow-root
