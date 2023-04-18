#

<https://www.elastic.co/guide/en/elasticsearch/reference/8.7/rest-apis.html>

information
    GET /

GET _search
{
  "query": {
    "match_all": {}}
}

GET /_health_report

GET _cluster/health

## Create Index

    PUT /graphhopper
    PUT gis

## see Index

    get gephhopper
    get gis

<https://www.elastic.co/guide/en/elasticsearch/reference/8.7/docs-index_.html>

## create date in the document with Manula ID

    PUT /<target>/_doc/<_id>
  
  Sample

    PUT /gis/_doc/1
    {
      "name":"mohammadreza",
      "age": "22"
    
    }

    PUT /gis/_doc/2
    {
      "name":"amirsaleh",
      "age": "23"
    
    }

## create date in the document with elastic ID

    POST gis/_doc
    {
      "mahdi":"habibian",
      "age":"29"
    }

## Delete Doc In Index

    DELETE /<index>/_doc/<_id>
    DELETE gis/_doc/6

## Read Data From Doc

    GET gis/_doc/1

## Read Data from Doc

    GET gis/_source/1

## Get all Documents

    GET gis/_search

## Get all Index

    GET _cat/indices
    GET _cat/indices/gis
    GET _cat/indices/gis/?v=true

## see number docs have in the index

    GET /gis/_count
    GET /gis/_count?q=name:mohammad             تعداد داکیومت هایی ک اسمشون محمد هست

Count API

## Get Number of docs in Index

    get gis/_count
    get _count?q=name:amirsaleh

## Delete API

    DELETE /gis/_doc/2

## Mulit Get

https://www.elastic.co/guide/en/elasticsearch/reference/current/docs-multi-get.html

    GET /_mget
    {
      "docs":[
       {
        "_index": "gis",
        "_id": "1"
       }, 
       {
        "_index": "gis",
        "_id": "2"
       } 
      ]
    }
-----------------------------------
    GET /gis/_mget
    {
      "docs":[
       {
        "_id": "1"
       }, 
       {
        "_id": "2"
       } 

      ]

    }
-----------------------------------
    GET /gis/_mget
    {

        "ids": ["1","2"]

    }


# Query DSL

* Leaf query clauses



* Compound query clauses

https://www.elastic.co/guide/en/elasticsearch/reference/8.7/query-dsl-bool-query.html
















## Reset Password

        /usr/share/elasticsearch/bin/elasticsearch-reset-password -u elastic
    or
        docker exec -it es01 bash
        /usr/share/elasticsearch/bin/elasticsearch-reset-password -u elastic

## Retrieve The Password

    Use the following command to retrieve the password for http.p12
        bin/elasticsearch-keystore show xpack.security.http.ssl.keystore.secure_password

    Use the following command to retrieve the password for transport.p12:
        bin/elasticsearch-keystore show xpack.security.transport.ssl.keystore.secure_password













## Note

- Note: max virtual memory areas vm.max_map_count [65530] is too low, increase to at least [262144]
