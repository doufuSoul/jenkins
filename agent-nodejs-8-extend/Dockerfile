FROM quay.app.2dfire.com/jenkins/origin-jenkins-agent-nodejs-8:v4.0

MAINTAINER doufu

# Labels consumed by Red Hat build service
LABEL name="openshift3/jenkins-agent-nodejs-8-extend"

USER root

# Install extend module
RUN curl https://raw.githubusercontent.com/cloudrouter/centos-repo/master/CentOS-Base.repo -o /etc/yum.repos.d/CentOS-Base.repo && \
    curl http://mirror.centos.org/centos-7/7/os/x86_64/RPM-GPG-KEY-CentOS-7 -o /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7 && \
    DISABLES="--disablerepo=rhel-server-extras --disablerepo=rhel-server --disablerepo=rhel-fast-datapath --disablerepo=rhel-server-optional --disablerepo=rhel-server-ose --disablerepo=rhel-server-rhscl" && \
    INSTALL_PKGS="libpng-devel libtool automake autoconf nasm" && \
    yum ${DISABLES} install -y $INSTALL_PKGS && \
    rpm -V $INSTALL_PKGS && \
    yum clean all -y

RUN chown -R 1001:0 $HOME && \
    chmod -R g+rw $HOME

USER 1001
