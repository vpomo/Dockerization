FROM ubuntu:22.04
RUN apt-get update && apt-get install -y sudo curl 

RUN groupadd -r newuser && useradd -r -g newuser newuser
RUN adduser newuser sudo
RUN adduser --disabled-password \
--gecos '' docker
RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> \
/etc/sudoers
RUN curl -sL https://deb.nodesource.com/setup_18.x | sudo -E bash -
RUN apt-get install -y nodejs
RUN apt-get install -y gcc g++ make
RUN curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | gpg --dearmor | tee /usr/share/keyrings/yarnkey.gpg >/dev/null
RUN echo "deb [signed-by=/usr/share/keyrings/yarnkey.gpg] https://dl.yarnpkg.com/debian stable main" | tee /etc/apt/sources.list.d/yarn.list
RUN apt-get update && apt-get install -y yarn


RUN mkdir -p /home/newuser
RUN chown -R 999:999 /home/newuser

RUN mkdir -p /project
RUN chown -R 999:999 /project
RUN chmod -R 777 /project

RUN npm install -g npm@9.6.7

RUN apt-get update && apt-get install -y git

RUN apt-get update && apt-get install -y \
    python3 \
    python3-dev 

RUN apt-get update && apt-get install -y python3-pip

# RUN python3 -m pip install --user pipx
# RUN python3 -m pipx ensurepath

RUN pip install eth-brownie
RUN brownie --version


USER newuser
WORKDIR /home/newuser

WORKDIR /project

ENTRYPOINT ["/bin/bash"]







