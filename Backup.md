



# Add repository

    add in docker-compose 
        - path.repo=/usr/share/elasticsearch/backup in the environment
    and mount   
        - /srv/docker-compose/elastic/backups:/usr/share/elasticsearch/backups

# elastic-restoring

1_ First we create a repository for our snapshots in the main cluster that has the indices:

    PUT /_snapshot/test_repo
    {
      "type": "fs",
      "settings": {
        "location": "test.repo"
      }
    }

Note: we can use kibanas settings to create repos too, go to stack management  > Snapshot and Restore  and make one from there instead.

If the location of repo.path is set in the elasticsearch config file as for example: /usr/share/elasticsearch/backup  then when we create a repo, if we just specify a name, if would count as /usr/share/elasticsearch/backup/<repo name>  so we dont need to write the whole path.

2_ Select the INDEX you want to back up
    GET _cat/indices

3_ Then we take a snapshot from the cluster that we want its data to be restored on another cluster:

    PUT /_snapshot/<repo name>/<snapshot name>?wait_for_completion=true
    {
      "indices": "data_stream_1,index_1,index_2",    # if we want all the indexes, dont write this line.
      "ignore_unavailable": true,
      "include_global_state": false
    }

    PUT /_snapshot/test_repo/test.repo?wait_for_completion=true
    {
      "indices": "business-audit-log-2023.01.07-000033,platform-exceptions-log-2023.02.21-000036,user-management-audit-log-2023.04.07-000021,map-helm-audit-log-2023.03.23-000020,routaa-app-audit-log-2023.01.07-000015",
      "ignore_unavailable": true,
      "include_global_state": false
    }

3_ Then we copy the repo directory : /usr/share/elasticsearch/backup/<repo name>  to the other clusters nodes, where its repo.path is located to, and lets say its also the same as the other cluster.

4_Repositories: Create Just Repositories in New Elastic Cluster & The snapshot is automatically detected

5_Restore: After copying the directory to the other clusters repo path (where it is shared between the nodes of that cluster) , we go into the other new cluster, and make a repository with the same name as we did with the first cluster, and then we can see the snapshot name for the created repo, we restore it like this :

    POST /_snapshot/<repo name>/<snapshot name>/_restore
    {
      "indices": "data_stream_1,index_1,index_2",   # if some indexes gives us an error, we then need to specify all the other indexes here.
      "ignore_unavailable": true,
      "include_global_state": false,
      "include_aliases": false
    }

    POST /_snapshot/test_repo/test.repo/_restore
    {
      "indices": "business-audit-log-2023.01.07-000033,platform-exceptions-log-2023.02.21-000036,user-management-audit-log-2023.04.07-000021,map-helm-audit-log-2023.03.23-000020,routaa-app-audit-log-2023.01.07-000015",all the other indexes here.
      "ignore_unavailable": true,
      "include_global_state": false,
      "include_aliases": false
    }

# Restore
