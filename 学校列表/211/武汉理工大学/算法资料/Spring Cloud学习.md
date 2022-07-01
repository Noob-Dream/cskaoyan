# Spring Cloud学习

## application.yml

概念解释：

-   -   `Route（路由）`：路由是网关的基本单元，由ID、URI、一组Predicate、一组Filter组成，根据Predicate进行匹配转发。
    -   `Predicate（谓语、断言）`：路由转发的判断条件，目前`SpringCloud Gateway`支持多种方式，常见如：`Path`、`Query`、`Method`、`Header`等。
    -   `Filter（过滤器）`：过滤器是路由转发请求时所经过的过滤逻辑，可用于修改请求、响应内容。

### 开始使用

`Spring Cloud Gateway`目前有两种方式进行配置：

-   `application.yml`配置文件方式
-   通过`@Bean`注解 `RouteLocator `方法返回值

### route的组成部分

注意冒号后有空格

-   `id`：路由的ID
-   `uri`：匹配路由的转发地址
-   `predicates`：配置该路由的断言，通过`PredicateDefinition`类进行接收配置。
-   `order`：路由的优先级，数字越小，优先级越高。

###  Spring Cloud Gateway Predicates

每一个`Predicate`的使用，你可以理解为：`当满足这种条件后才会被转发`，如果是多个，那就是都满足的情况下被转发。

 Path 方式匹配转发

我们在`application.yml`配置文件内添加对应的路由配置，如下所示

```yml
spring:
  application:
    name: spring-cloud-gateway-sample
  cloud:
    gateway:
      routes:
        - id: blog
          uri: http://blog.yuqiyu.com
          predicates:
            # 匹配路径转发
            - Path=/api-boot-datasource-switch.html
# 端口号
server:
  port: 9090
```

在上面的配置中，当访问`http://localhost:9090/api-boot-datasource-switch.html`时就会被自动转发到`http://blog.yuqiyu.com/api-boot-datasource-switch.html`，这里要注意完全匹配`Path`的值时才会进行路由转发，对应的 `RouteLocator`方式该怎么进行配置

```java
@Bean
public RouteLocator routeLocator(RouteLocatorBuilder builder) {
  return builder.routes()
    .route("blog", r -> 
           r.path("/api-boot-datasource-switch.html")
           .uri("http://blog.yuqiyu.com"))
    	  .build();
}

id: blog
path: /api-boot-datasource-switch.html
uri:http: //blog.yuqiyu.com
```

```yml
spring:
  cloud:
    gateway:
      routes:
      - id: 163_route
        uri: http://www.163.com/
        predicates:
        - Path=/163
      - id: baidu_route
        uri: http://baidu.com:80/
        predicates:
        - Path=/baidu


```







### RouteLocator



## @RestController



### @GetMapping

