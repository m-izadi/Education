
Link: https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html

docker-compose up -d

# Docker-compose

# Step1 

### Docker-Compose

Copy [Docker-Compose File](Docker-Compose/docker-compose.yml) to Server

To access elastic with a certificate, you need to add your host in the docker-compose ***setup*** section

**<https://www.elastic.co/guide/en/elasticsearch/reference/8.7/docker.html#docker-file>**
## .env

Copy [.env](Docker-Compose/.env) file next to the Docker-compose file

**<https://www.elastic.co/guide/en/elasticsearch/reference/8.7/docker.html#docker-env-file>**

## Set Certificate To another Host
if you want connect to elastic you need copy and move certificate to server

Cert Path **/var/lib/docker/volumes/elastic_certs/_data/ca/**

* 1 Copy your CA to dir /usr/local/share/ca-certificates/
* 2 Use command: sudo cp ca.crt  ca.key /usr/local/share/ca-certificates/
* 3 Update the CA store: sudo update-ca-certificates


Test Connection

    curl https://IP:9200 -u elastic



____________________________________________________________________

--------------------------------------------------------------------

## Note:

   * Make sure that Docker is allotted at least 4GB of memory.

   * if Container dont run and give this error " Native controller process has stopped - no new native processes can be started "
        set in linux
            sysctl -w vm.max_map_count=262144
    Link: https://stackoverflow.com/questions/60182669/elastic-search-error-native-controller-process-has-stopped-no-new-native-pro      