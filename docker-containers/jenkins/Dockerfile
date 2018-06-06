FROM jenkins



USER root
WORKDIR /var/jenkins_home/
RUN touch .profile

RUN wget -O - https://raw.githubusercontent.com/creationix/nvm/v0.11.1/install.sh | bash
#
#ENV NVM_DIR /var/jenkins_home/.nvm
#RUN echo " . /var/jenkins_home/.nvm/nvm.sh " >> .bashrc

RUN rm -f /var/jenkins_home/.ssh/known_hosts

RUN chmod -R 777 /var/jenkins_home
#RUN chown -R 1000 /var/jenkins_home

COPY /data/plugins.txt /usr/share/jenkins/plugins.txt
RUN tail -100000 /usr/local/bin/plugins.sh
#RUN /usr/local/bin/install-plugins.sh  /usr/share/jenkins/plugins.txt
RUN apt-get update
RUN apt-get install -y dos2unix
RUN dos2unix /usr/share/jenkins/plugins.txt && apt-get --purge remove -y dos2unix && rm -rf /var/lib/apt/lists/*

RUN xargs /usr/local/bin/plugins.sh  /usr/share/jenkins/plugins.txt




