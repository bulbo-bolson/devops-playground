FROM centos:7

USER root

# openssh
RUN yum -y install openssh-server
# fix ssh server daemon error in container
RUN /usr/sbin/sshd-keygen > /dev/null 2>&1 

# install puppet 5 server and agent
RUN rpm -Uvh https://yum.puppet.com/puppet5-release-el-7.noarch.rpm && \
    yum -y install puppetserver puppet

RUN echo "JAVA_ARGS=${PUPPETMASTER_JAVA_ARGS:-\"-Xms512m -Xmx512m\"}" >> /etc/sysconfig/puppetserver
COPY ./autosign.conf /etc/puppetlabs/puppet/autosign.conf

CMD /opt/puppetlabs/bin/puppetserver foreground

