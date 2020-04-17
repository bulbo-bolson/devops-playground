FROM centos:7

USER root

# fix systemd problem in centos container: https://hub.docker.com/_/centos/
RUN (cd /lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i == \
systemd-tmpfiles-setup.service ] || rm -f $i; done); \
rm -f /lib/systemd/system/multi-user.target.wants/*;\
rm -f /etc/systemd/system/*.wants/*;\
rm -f /lib/systemd/system/local-fs.target.wants/*; \
rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
rm -f /lib/systemd/system/basic.target.wants/*;\
rm -f /lib/systemd/system/anaconda.target.wants/*;
VOLUME [ "/sys/fs/cgroup" ]

# openssh
RUN yum -y install openssh-server
# fix ssh server daemon error in container
RUN /usr/sbin/sshd-keygen > /dev/null 2>&1 

# install puppet 5 server and agent
RUN rpm -ivh https://yum.puppetlabs.com/el/7/products/x86_64/puppetlabs-release-7-11.noarch.rpm && \
    yum -y install puppet-server puppet
RUN echo JAVA_ARGS="${PUPPETMASTER_JAVA_ARGS:--Xms512m -Xmx512m}" >> /etc/sysconfig/puppetserver

CMD ["/usr/sbin/init"]

