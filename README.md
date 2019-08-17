# docker-devops-env

Environment for DevOps built with Docker. It consists of the following applications:

- Gitea to host Git repositories
- Sonarqube for source code analysis
- Jenkins to build/test projects
- Postgres database
- Caddy which serves as a reverse proxy

## Assumptions

The stack will run an a host with IP `10.1.2.48` and the hostname `devops`.

## Setup

First, check out the repository and change to created directory

```
git clone https://github.com/MarcScheib/docker-devops-env.git
cd docker-devops-env
```

In this directory, the basic configuration for all services and the volumes is already available. However, some directories require special ownership. Therefor, execute the following:

```
sudo chown -R 999:999 sonarqube/
```

In some cases, I had issues with routes in Docker (no route to host). In such cases, I had to configure `firwalld` (for CentOS).
Open `/etc/firewalld/zones/public.xml` and add the following between `<zone></zone>`:

```
 <rule family="ipv4">
   <source address="172.16.0.0/12"/>
   <accept/>
 </rule>
```

Afterwards, restart the firewall via

```
systemctl restart firewalld
```

Finally, the complete stack can be started with Docker Compose as follows (-d starts the process in the background):

```
docker-compose up -d
```

## Usage

You can reach the services in your browser via the following URLs now:

- https://devops/gitea
- https://devops/jenkins
- https://devops/sonar
