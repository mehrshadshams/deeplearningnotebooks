# deeplearningnotebooks

# ElasticSearch

How to start:

1. Run ElasticSearch:
```bash
docker run --rm --name elasticsearch -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:8.15.0
```

2. Reset ElasticSearch password
```bash
docker exec -it elasticsearch /usr/share/elasticsearch/bin/elasticsearch-reset-password -u elastic
```

3. Export password
```bash
export ELASTIC_PASSWORD="<password>"
```

4. Copy ElasticSearch cert
```bash
docker cp elasticsearch:/usr/share/elasticsearch/config/certs/http_ca.crt .
```

5. Verify connectivity
```bash
curl --cacert http_ca.crt -u elastic:$ELASTIC_PASSWORD https://localhost:9200
```