```
$ docker run --rm --name filelog-tester -d \
             --volume "$(pwd)/test/logs:/var/tmp"
             filelog-tester:0.1.0
```

```
$ docker run --rm --network network-001 --name elasticsearch \ 
						 -d -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" \
              -v esdata:/usr/share/elasticsearch/data \
						  docker.elastic.co/elasticsearch/elasticsearch:7.2.0
```


```
$ docker run --rm --network network-001 --name logstash \
             -v "$(pwd)/config/logstash/pipeline/:/usr/share/logstash/pipeline/:ro" \
             -v "$(pwd)/config/logstash/config/:/usr/share/logstash/config/:ro" \
             docker.elastic.co/logstash/logstash:7.2.0
```

```
$ docker run --rm --network network-001 -p 5601:5601 \
						 --name kiba -e ELASTICSEARCH_HOSTS=http://elasticsearch:9200 \
						 docker.elastic.co/kibana/kibana:7.2.0
```


```	
$ docker run --rm -d --network network-001 --user=root \
             --volume="$(pwd)/config/filebeat/filebeat.yml:/usr/share/filebeat/filebeat.yml:ro" \
             --volume="$(pwd)/test/logs:/test/logs:ro" \
						 docker.elastic.co/beats/filebeat:7.2.0
```
