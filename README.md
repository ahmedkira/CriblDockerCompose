# CriblDockerCompose
Docker Compose Files to install Cribl Leader and Worker

Files:

docker-criblworker.yml
Cribl Worker Only: as the name indicates, for deploying just a worker. A leader should already be up and reachable. 
Replace this line with the leader IP & port: 
          CRIBL_DIST_MASTER_URL: tcp://cribl_leader@cribl:4200
Start with a command like to start up one worker: docker-compose -f docker-criblworker.yml up -d
To start up 2 workers, run a command similar to: docker-compose -f docker-criblworker.yml up -d --scale cribl_worker=2

docker-compose-cribl.yml
Cribl Worker AND leader running locally in docker.
Start with: docker-compose -f docker-compose-cribl.yml  up -d

docker-compose-cribl-splunk-nginx.yml
Compose file with:
- an nginx server sending transaction logs to a local worker
- Cribl Leader
- Cribl Worker
- Splunk instance
Start with: docker-compose -f docker-compose-cribl-splunk-nginx.yml  up -d
