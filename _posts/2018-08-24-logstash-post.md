
---
title: "LogStash"
categories: [ELK, Logstash]
---

#### Installing Logstash
```
1. download & unzip 
2. start up 
```

#### 개념

DataSource -> INPUT|FILTER|OUTPUT -> Elastaticsearch


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


#### Filebeat를 통한 테스트 

#### 1. Filebeat 설정 

- filebeat.yml 
```
filebeat.prospectors:
- type: log
  paths:
    - /path/to/file/logstash-tutorial.log 
output.logstash:
  hosts: ["localhost:5044"]
```

- filebeat 실행 및 메시지 logstash에 메시지 전송 
```
sudo ./filebeat -e -c filebeat.yml -d "publish"
```

#### 2. Logstash 설정 

Logstash 설정파일(logstash.conf)

- 기본 정보 
```
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

- 변경 후 
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
bin/logstash -f first-pipeline.conf --config.test_and_exitor
#  --config.test_and_exitor => config file에 에러가 있는지 리포트
or
bin/logstash -f first-pipeline.conf --config.reload.automatic
# --config.reload.automatic => config파일 변경시 자동 리로드 수행
```


