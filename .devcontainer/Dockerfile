FROM python:3.11.5-bookworm

RUN apt update && apt install -y graphviz

ARG USERNAME=container-user

COPY .tmp_uid .tmp_uid
COPY .tmp_gid .tmp_gid
RUN groupadd --gid `cat .tmp_gid` $USERNAME \
    && useradd --uid `cat .tmp_uid` --gid `cat .tmp_gid` -m $USERNAME

WORKDIR /tmp
COPY requirements.txt requirements.txt
USER $USERNAME
RUN python3 -m pip install jupyter
RUN python3 -m pip install -r requirements.txt
