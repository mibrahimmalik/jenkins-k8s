FROM jenkins/jnlp-slave
# Running as root to have an easy support for Docker
USER root
# Compy kubeconfig file 
RUN mkdir /root/.kube
COPY config /root/.kube/config
#Install Docker, kubectl and helm
RUN apt-get -qq update && \
   apt-get -qq -y install curl && \
   curl -sSL https://get.docker.com/ | sh && \
   curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl && \
   chmod +x ./kubectl && \
   mv ./kubectl /usr/local/bin/kubectl && \
   curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get | bash
# Download terraform for linux
RUN wget https://releases.hashicorp.com/terraform/0.11.11/terraform_0.11.11_linux_amd64.zip
# Unzip
RUN unzip terraform_0.11.11_linux_amd64.zip
# Move to local bin
RUN mv terraform /usr/local/bin/
# Check that it's installed
RUN terraform --version 