---
title: "Spring Cloude Fegin & Hystrix"
categories: [MSA]
---

### Spring Cloude Fegin & Hystrix 사용법 




* fegin에서 hystrix 사용하기 (application.properties)
``` 
feign.hystrix.enabled=true 
```

* fegin에서 hystrix 사용하기 (어노테이션)
``` 
@EnableCircuitBreaker 
public class GatewayApplication {
    public static void main(String[] args) {
        SpringApplication.run(GatewayApplication.class, args);
    }
    이하 생략 
}
```
