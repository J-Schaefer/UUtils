ARG SSH_PRIVATE_KEY

FROM ubuntu:18.04

# Preparation
# install git
RUN apt-get update
RUN apt-get install -y git


RUN mkdir /.ssh/
RUN echo "${SSH_PRIVATE_KEY}" > /.ssh/id_rsa
# make sure your domain is accepted
RUN touch /root/.ssh/known_hosts
RUN ssh-keyscan github.com >> /root/.ssh/known_hosts

RUN git clone git@github.com:EpicGames/UnrealEngine.git UnrealEngine422/
RUN cd UnrealEngine422/
RUN .Setup.sh
RUN .GenerateProjectFiles.sh
RUN make