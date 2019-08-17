# docker-devops-env

Environment for DevOps built with Docker. It consists of the following applications:

- Gitea to host Git repositories
- Sonarqube for source code analysis
- Jenkins to build/test projects
- Postgres database
- Caddy which serves as a reverse proxy

## Usage

The complete stack is started with Docker Compose as follows (-d starts the process in the background):

```
docker-compose up -d
```
