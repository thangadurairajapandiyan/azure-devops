# Azure pipeline agent as docker container

### Create Docker Image
```
docker build -t dockeragent:latest .
```

### Create Docker container agent
```
docker run -e AZP_URL=<Azure DevOps instance> -e AZP_TOKEN=<PAT token> -e AZP_AGENT_NAME=mydockeragent dockeragent:latest
```
