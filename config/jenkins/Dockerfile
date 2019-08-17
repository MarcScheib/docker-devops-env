FROM jenkins/jenkins:lts

USER root
RUN echo "Acquire::http::Pipeline-Depth 0;" > /etc/apt/apt.conf.d/99fixbadproxy && \
    echo "Acquire::http::No-Cache true;"   >> /etc/apt/apt.conf.d/99fixbadproxy && \
    echo "Acquire::BrokenProxy    true;"   >> /etc/apt/apt.conf.d/99fixbadproxy && \
    apt-get update && apt-get install -y sudo libltdl-dev \
      && rm -rf /var/lib/apt/lists/* && \
    groupadd -g 994 docker && \
    usermod -aG docker jenkins

USER jenkins
