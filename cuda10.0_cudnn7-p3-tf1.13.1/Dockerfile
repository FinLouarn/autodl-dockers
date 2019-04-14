FROM nvidia/cuda:10.0-cudnn7-runtime-ubuntu16.04

USER root

# install some basic utilities packages
RUN apt-get update -qq \
 && apt-get install -y --no-install-recommends\
    software-properties-common \
    python3-pip \
    gcc \
    curl \
    ca-certificates \
    sudo \
    python3.5-dev \
    git \
    vim\
    bzip2 \
    libx11-6 \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

# additional libraries
RUN pip3 install --upgrade pip
RUN pip3 install setuptools
RUN pip3 install wheel

# install numpy and other libraries for data science
RUN pip3 --no-cache-dir install -U numpy==1.14.5
RUN pip3 install pandas
RUN pip3 install scipy
RUN pip3 install matplotlib
RUN pip3 install sklearn
RUN pip3 install psutil
RUN pip3 install pyyaml

# install tensorflow
RUN pip3 install tensorflow-gpu==1.13.1

# Create a working directory
WORKDIR /app/codalab/

# Install HDF5 Python bindings
RUN pip3 install h5py
RUN pip3 install h5py-cache==1.0

# create a link to use python3 as as 'python'
RUN ln -s /usr/bin/python3 /usr/bin/python
