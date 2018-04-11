log
======


unity log4net : https://forum.unity3d.com/threads/using-log4net-for-logging.8380/



Install-Package log4net
https://logging.apache.org/log4net/release/manual/configuration.html

Install-Package NLog.Config
https://github.com/NLog/NLog/wiki/Configuration-file



https://github.com/grafana/grafana - ui

ElasticSearch
http://localhost:9200/

https://github.com/mobz/elasticsearch-head - 단순 테이블 보기

LogStash
logstash.bat -f logstash.conf
입력 - input
필터 - filter
 grok을 이용 비정형 데이터에서 구조 도출
 mutate
 date
출력 - output


Kibana
http://localhost:5601


NSSM - the Non-Sucking Service Manager
https://nssm.cc/download

focus on pronunciation.
https://www.amazon.com/dp/0133046850/ref=cm_sw_r_cp_awdb_l5R.ybCQE0NQR




E L K
E : elasticsearch (db 겸 query machine)
L : logstash - collector | indexer
K : Kibana ( UI viewer )

docker - https://github.com/deviantony/docker-elk

kibana plugin - realtime tail - https://github.com/sivasamyk/logtrail
