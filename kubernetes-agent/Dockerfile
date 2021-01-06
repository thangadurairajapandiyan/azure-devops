ARG PARENT_IMAGE
FROM $PARENT_IMAGE

RUN yum -y update && \
    yum install -y tar gzip openssl-libs krb5-libs zlib libicu shadow-utils iputils perl perl-Error less openssh-clients python && \
    rpm -ivh https://dl.iuscommunity.org/pub/ius/stable/CentOS/7/x86_64/git2u-core-2.16.5-1.ius.centos7.x86_64.rpm

RUN useradd --no-log-init -d /home/agent -ms /bin/bash agent

USER agent

WORKDIR /home/agent

RUN mkdir /home/agent/task-bin && \
    export PATH=/home/agent/task-bin:$PATH

RUN curl -LsS https://vstsagentpackage.azureedge.net/agent/2.179.0/vsts-agent-linux-x64-2.179.0.tar.gz | tar -xz

COPY --chown=agent:agent ./start.sh .
RUN chmod +x start.sh

CMD ["./start.sh"]
