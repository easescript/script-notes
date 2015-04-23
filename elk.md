## elasticsearch
    /usr/bin/java 
    -Xms256m -Xmx1g 
    -Djava.awt.headless=true -XX:+UseParNewGC -XX:+UseConcMarkSweepGC
    -XX:CMSInitiatingOccupancyFraction=75 -XX:+UseCMSInitiatingOccupancyOnly
    -XX:+HeapDumpOnOutOfMemoryError -XX:+DisableExplicitGC
    -Dfile.encoding=UTF-8 
    -Delasticsearch 
    -Des.pidfile=/var/run/elasticsearch/elasticsearch.pid 
    -Des.path.home=/usr/share/elasticsearch 
    -cp :/usr/share/elasticsearch/lib/elasticsearch-1.5.1.jar:/usr/share/elasticsearch/lib/*:/usr/share/elasticsearch/lib/sigar/* 
    -Des.default.path.home=/usr/share/elasticsearch 
    -Des.default.path.logs=/var/log/elasticsearch 
    -Des.default.path.data=/var/lib/elasticsearch 
    -Des.default.path.work=/tmp/elasticsearch 
    -Des.default.path.conf=/etc/elasticsearch 
    org.elasticsearch.bootstrap.Elasticsearch

## logstash
    /usr/bin/java 
    -Djava.io.tmpdir=/var/lib/logstash 
    -Xmx2048m 
    -XX:+UseParNewGC -XX:+UseConcMarkSweepGC -Djava.awt.headless=true
    -XX:CMSInitiatingOccupancyFraction=75 -XX:+UseCMSInitiatingOccupancyOnly 
    -jar /opt/logstash/vendor/jar/jruby-complete-1.7.11.jar 
    -I/opt/logstash/lib /opt/logstash/lib/logstash/runner.rb agent 
    -f /etc/logstash/conf.d 
    -l /var/log/logstash/logstash.log
