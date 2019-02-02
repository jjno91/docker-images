FROM hashicorp/terraform

# update all packages
RUN sudo apt-get update

# https://docs.aws.amazon.com/eks/latest/userguide/install-aws-iam-authenticator.html
RUN sudo apt-get install golang-go
RUN go get -u -v github.com/kubernetes-sigs/aws-iam-authenticator/cmd/aws-iam-authenticator
RUN export PATH=$HOME/go/bin:$PATH && echo 'export PATH=$HOME/go/bin:$PATH' >> ~/.bashrc
RUN aws-iam-authenticator help

# https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl
RUN sudo apt-get install -y apt-transport-https
RUN curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
RUN echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
RUN sudo apt-get update
RUN sudo apt-get install -y kubectl
