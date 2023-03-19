## 1. Spring 이란?

- Java언어로 가장 많이 사용 프레임 워크 중 하나
- 자바 EE 어플리케이션을 빌드할 수 있는 오픈소스 경량 프레임워크
- Spring 에서는 의존성 주입(Dependency Injection), 제어역전(Inversion Of Control), 관점지향 프로그래밍(AOP)가 가장 중요한 요소 → 추후 정리 예정


## 2. Spring Boot란?

- 기존 스프링 프레임워크 위에 구축됨
    
    즉, Spring Framework 기반으로 만들어진 것인데, 개발자가 쉽게 Spring 기반의 어플리케이션을 빠르게 만들 수 있도록 도와줌
    
    - **설정 자동화, 내장 서버, 의존성 관리** 등의 특징을 가짐
- **독립 실행형(stand-alone)** 프로덕션 등급(production-frade)의 스프링 기반 어플리케이션을 쉽게 만들 수 있다
- 스프링 프레임워크를 사용하기 위한 **설정의 많은 부분을 자동화**하여 편하게 스프링을 활용할 수 있게 한다

즉, **Spring Boot는 Spring 프레임워크의 모든 기능을 포함하는 동시에 어플리케이션 개발을 훨씬 쉽게 만들어주는 도구다.** Spring Boot를 사용하면 보다 짧은 시간 안에 어플리케이션을 시작하고 개발할 수 있다.


## 3. Spring Boot을 사용하면…

1. **********************************Dependency 관리**********************************
- 어플리케이션 개발에 필요한 모든 Dependency를 프레임워크에서 관리
    - 사용되는 Dependency를 호환되는 버전으로 관리해주어야하는데, Spring Boot는 **SpringBoot-Starter를 제공하여 자동으로 호환되는 버전 관리** 가능 (미리 설정되어 있는 Starter 프로젝트 제공)
- Spring Framework의 경우, 의존성 관리 시, 설정 파일이 매우 길고 모든 dependency에 대해 버전관리도 하나하나 해줘야 한다
    
    ```python
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-web</artifactId>
        <version>5.3.5</version>
    </dependency>
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-webmvc</artifactId>
        <version>5.3.5</version>
    </dependency>
    ```
    
- Spring Boot Framework에서는 보다 쉽게 설정하고, 버전 관리도 자동으로 해준다
    
    ```python
    implementation 'org.springframework.boot:spring-boot-starter-web'
    ```
    
    Test와 관련한 라이브러리를 사용하려고 하는 경우도 마찬가지로, Spring에서는 Spring Test, JUnit, Hamcrest, Mockito 등 모든 라이브러리를 추가해줘야 하지만, Spring Boot에서는 spring-boot-starter-test만 추가해주면 된다.
    

2. **자동 설정(Auto Configuration) 사용**
- Spring에서는 Configuration 설정할 때도 매우 길며 모든 어노테이션, 빈 등록 등을 모두 설정해줘야 한다.
    
    ```python
    @Configuration
    @EnableWebMvc
    public class MvcWebConfig implements WebMvcConfigurer {
    
        @Autowired
        private ApplicationContext applicationContext;
    
        @Bean
        public SpringResourceTemplateResolver templateResolver() {
            SpringResourceTemplateResolver templateResolver = 
              new SpringResourceTemplateResolver();
            templateResolver.setApplicationContext(applicationContext);
            templateResolver.setPrefix("/WEB-INF/views/");
            templateResolver.setSuffix(".html");
            return templateResolver;
        }
    
        @Bean
        public SpringTemplateEngine templateEngine() {
            SpringTemplateEngine templateEngine = new SpringTemplateEngine();
            templateEngine.setTemplateResolver(templateResolver());
            templateEngine.setEnableSpringELCompiler(true);
            return templateEngine;
        }
    
        @Override
        public void configureViewResolvers(ViewResolverRegistry registry) {
            ThymeleafViewResolver resolver = new ThymeleafViewResolver();
            resolver.setTemplateEngine(templateEngine());
            registry.viewResolver(resolver);
        }
    }
    ```
    
- Spring Boot에서는 application.properties 나 application.yml 파일에 설정하면 된다
    
    ```python
    implementation 'org.springframework.boot:spring-boot-starter-thymeleaf
    ```
    
- `@SpringBootApplication` 어노테이션을 통해 외부 라이브러리, 내장 톰캣 서버 등이 실행할 수 있게 된다. 아래는 SpringBootApplication에 포함된 어노테이션과 그 기능.
    - `@ComponentScan` : @Component, @Controller, @Repository, @Service 라는 어노테이션이 붙어있는 객체들을 스캔해 Bean에 등록
    - `@EnableAutoConfiguration` : 스캔 이후 사전에 정의한 라이브러리들을 Bean에 등록

3. ********************내장 서버********************
- 서버 구동시간이 절반 가까이 단축됨
- Spring으로 개발한 어플리케이션의 경우, war 파일을 Web Application Server에 담아 배포했다
- Spring Boot Framework의 경우, Tomcat, Jetty와 같은 내장 WAS(내장 서블릿 컨테이너)를 가지고 있어 jar파일로 간편하게 배포가 가능하다

4. ****************************************************************************모니터링 관리를 위한 Spring Actuator(스프링 액추에이터) 제공****************************************************************************
- 서비스가 정상적으로 동작하는지 상태 모니터링 제공
- 스프링 부트에서 제공하는 상태 정보를 보다 쉽게 모니터링할 수 있게 기능을 제공


## 4. 정리

한마디로 말해 Spring Boot는 Spring 프레임워크에 비해

1. 간편한 설정이 가능
2. 의존성 관리가 편해지고 자동으로 권장 버전 관리
3. 내장 서버로 인한 간단한 배포 서버 구축
4. Spring Security, JPA 등의 다른 스프링 프레임워크 요소를 쉽게 사용

을 가능하게 한다.
