---
title: "Spring Cloude Fegin & Hystrix"
categories: [MSA]
---

### Spring Cloude Fegin & Hystrix 사용법 




* feign에서 hystrix 사용하기 (application.properties)
``` 
feign.hystrix.enabled=true 
```

* feign에서 hystrix 사용하기 (어노테이션)
``` 
@EnableCircuitBreaker 
public class GatewayApplication {
    public static void main(String[] args) {
        SpringApplication.run(GatewayApplication.class, args);
    }
    이하 생략 
}
```

* feigin Client 작성 예
  - fegin Client 예
    ```
    @FeignClient(value = "book-service", fallback=BooksClientFailback.class)
    public interface BooksClient {

        @RequestMapping(value = "/books/{bookId}", method = {RequestMethod.GET})
        Book getBookById(@PathVariable("bookId") Long bookId);
    }

    ```
  - Circuit Breaker
    ```
    @Component
    public class BooksClientFailback implements BooksClient {

        /**
         * Circuit Open
         */
        @Override
        public Book getBookById(Long bookId) {
            // TODO Auto-generated method stub
            System.out.println("Circuit Open !!! ");
            return new Book();
        }



    }
    ```

