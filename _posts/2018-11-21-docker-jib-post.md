---
title: "Docker JIB 활용하기"
categories: [Docker]
---

## JIB 이슈 

JIB로 도커에 이미지까지 생성했는데 이미지 수행후 /bash로 접근해서 디버깅 하고 싶을 때
[참고URL](https://github.com/GoogleContainerTools/jib/blob/master/docs/faq.md "참고")

구성하기 maven pom.xml
``` 
<configuration>
  <from>
    <image>gcr.io/distroless/java:debug</image>
  </from>
</configuration>

```
실행하기
```
docker run -it --entrypoint /busybox/sh <image name> 

```
