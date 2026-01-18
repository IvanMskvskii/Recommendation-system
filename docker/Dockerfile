FROM ubuntu:22.04 

RUN apt-get update 
RUN apt-get install -y libxml2 libxslt-dev wget bzip2 gcc 

RUN wget --quiet https://repo.anaconda.com/miniconda/Miniconda3-py310_23.3.1-0-Linux-x86_64.sh -O ~/miniconda.sh && \
    /bin/bash ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh
ENV PATH=/opt/conda/bin:$PATH

RUN conda install -y -c conda-forge pytest jupyter scikit-learn

RUN pip install pandas matplotlib seaborn numpy scipy optuna regex

RUN conda install cornac -c conda-forge

ENV PYTHONDONTWRITEBYTECODE 1 

ADD . /home/lightfm/ 
WORKDIR /home/ 

RUN cd lightfm && pip install -e .
