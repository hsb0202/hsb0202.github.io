---
title: "LogStash"
categories: [Logstash, ELK]
---


# 1. Installing Logstash
```
1. download & unzip 
2. start up 
```

# 2. 개념

``` DataSource -> INPUT|FILTER|OUTPUT -> Elastaticsearch ```

- INPUT 
 : Source로 부터 데이터를 소비
- FILTER 
 : 데이터를 정해진 룰에 따라서 필터링
- OUTPUT 
 : 목적지로 데이터를 전송

예시

```
cd logstash-6.4.0
bin/logstash -e 'input { stdin { } } output { stdout {} }'
```

> e 옵션은 Command라인상에 설정 정보를 추가하기 위함.


# 3. 테스트

## 3.1 Filebeat 실행

- 설정파일

```
# filebeat.yml 
# output을 logstash로 설정 

filebeat.prospectors:
- type: log
  paths:
    - /path/to/file/logstash-tutorial.log 
output.logstash:
  hosts: ["localhost:5044"]
```

- filebeat 실행 

```
sudo ./filebeat -e -c filebeat.yml -d "publish"
```

## 3.2 Logstash 실행 

- 설정 파일(기본값)

```
# logstash.conf
# The # character at the beginning of a line indicates a comment. Use
# comments to describe your configuration.
input {
}
# The filter part of this file is commented out to indicate that it is
# optional.
# filter {
#
# }
output {
}
```

- 설정파일(변경후)

```
input {
    beats {
        port => "5044"
    }
}
# The filter part of this file is commented out to indicate that it is
# optional.
# filter {
#
# }
output {
    stdout { codec => rubydebug }
}
```

- logstash 실행 

```
bin/logstash -f first-pipeline.conf --config.test_and_exit
#  --config.test_and_exitor => config file에 에러가 있는지 리포트
or
bin/logstash -f first-pipeline.conf --config.reload.automatic
# --config.reload.automatic => config파일 변경시 자동 리로드 수행
```
# 참고 자료
[mute처리](https://www.elastic.co/guide/en/logstash/current/plugins-filters-mutate.html "뮤트시키기") <br/>
[jdbc 플러그인](https://discuss.elastic.co/t/jdbc-mssql-server-connection/44324/2 "jdbc플러그인") <br/>
[jdbc 플러그인](https://medium.com/@erangadulshan.14/pushing-relational-data-to-elasticsearch-using-logstash-jdbc-input-plugin-48af81ed1000 "jdbc플러그인가이드")  <br/>
[date변환](https://discuss.elastic.co/t/converting-string-to-date/26748/2 "convert string to date")  <br/>
