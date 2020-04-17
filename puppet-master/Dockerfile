FROM centos:7

USER root

# openssh
RUN yum -y install openssh-server
# fix ssh server daemon error in container
RUN /usr/sbin/sshd-keygen > /dev/null 2>&1 

# install puppet 5 server and agent
RUN rpm -ivh https://yum.puppetlabs.com/el/7/products/x86_64/puppetlabs-release-7-11.noarch.rpm && \
    yum -y install puppet-server puppet
RUN echo JAVA_ARGS="${PUPPETMASTER_JAVA_ARGS:--Xms512m -Xmx512m}" >> /etc/sysconfig/puppetserver

CMD ["/usr/bin/puppet", "master", "--no-daemonize"]

