FROM ubuntu:18.04

ARG SSH_PRIVATE_KEY=.ssh/id_rsa

# Preparation
# install git
RUN apt-get update
RUN apt-get install -y git

RUN ls /opt/jenkins-home

RUN cd UE4-22 && .Setup.sh && .GenerateProjectFiles.sh && make

# RUN mkdir /root/.ssh/
# # Copy over private key, and set permissions
# # Warning! Anyone who gets their hands on this image will be able
# # to retrieve this private key file from the corresponding image layer
# RUN echo $HOME
# COPY ../../../.ssh/id_rsa /root/.ssh/id_rsa
# RUN cat /root/.ssh/id_rsa
# # make sure your domain is accepted
# RUN touch /root/.ssh/known_hosts
# RUN ssh-keyscan github.com >> /root/.ssh/known_hosts

# # Install ssh client and git
# RUN apk add --no-cache openssh-client git
# # Download public key for github.com
# RUN mkdir -p -m 0600 ~/.ssh && ssh-keyscan github.com >> ~/.ssh/known_hosts
# # Clone private repository
# RUN --mount=type=ssh git clone git@github.com:EpicGames/UnrealEngine.git UnrealEngine422/

# RUN cd UnrealEngine422/
# RUN .Setup.sh
# RUN .GenerateProjectFiles.sh
# RUN make
