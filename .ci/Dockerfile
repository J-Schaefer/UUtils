FROM ubuntu:18.04

ARG SSH_PRIVATE_KEY=${HOME}\.ssh\id_rsa

# Preparation
# install git
RUN apt-get update
RUN apt-get install -y git


RUN mkdir /root/.ssh/
# Copy over private key, and set permissions
# Warning! Anyone who gets their hands on this image will be able
# to retrieve this private key file from the corresponding image layer
ADD ${SSH_PRIVATE_KEY} /root/.ssh/id_rsa
RUN cat /root/.ssh/id_rsa
# make sure your domain is accepted
RUN touch /root/.ssh/known_hosts
RUN ssh-keyscan github.com >> /root/.ssh/known_hosts

RUN git clone git@github.com:EpicGames/UnrealEngine.git UnrealEngine422/
RUN cd UnrealEngine422/
RUN .Setup.sh
RUN .GenerateProjectFiles.sh
RUN make