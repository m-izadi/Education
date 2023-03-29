# Create Single node

    docker network create elastic

    docker run -d --name es01 --net elastic -p 9200:9200 elasticsearch:8.6.1

    docker exec -it es01 bash

## reset password

        /usr/share/elasticsearch/bin/elasticsearch-reset-password -u elastic
    or
        docker exec -it es01 bash
        /usr/share/elasticsearch/bin/elasticsearch-reset-password -u elastic

 Note: max virtual memory areas vm.max_map_count [65530] is too low, increase to at least [262144]