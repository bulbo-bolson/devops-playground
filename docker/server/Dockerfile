FROM centos:7
  
USER root

# openssh
RUN yum -y install openssh-server
# fix ssh server daemon error in container
RUN /usr/sbin/sshd-keygen > /dev/null 2>&1

# install puppet 5 agent
RUN rpm -Uvh https://yum.puppet.com/puppet5-release-el-7.noarch.rpm && \
    yum -y install puppet

CMD tail -f /dev/null

