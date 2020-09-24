# Use the specified pytorch image as base image, update apt-get, and install python3-pip.
FROM pytorch/pytorch:1.5.1-cuda10.1-cudnn7-runtime
RUN apt-get update && apt-get -y update
RUN apt-get install -y python3-pip
# The current directory is "worskapce". Copy over the requirements.txt file, and install the requirements via pip3.
COPY requirements.txt .
RUN pip3 -q install pip --upgrade
RUN pip3 install torchaudio
RUN pip3 install -r requirements.txt
# In "workspace", create the directory "container-vol" (we will mount our volume to "container-vol").
RUN mkdir container-vol
# Start jupyter notebook using the specified port.
CMD ["jupyter", "notebook", "--port=8888", "--no-browser", "--ip=0.0.0.0", "--allow-root"]