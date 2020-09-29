Failed to configure a DataSource: 'url' attribute is not specified and no embedded datasource could be configured.在初步搭建springboot应用，因为没有进行数据库配置，如地址值，数据库驱动，用户名，密码等，常常会出现上述错误，表示是无法配置DataSource：未指定‘URL’属性，无法配置嵌入数据源。

Springboot最大的一个好处就是自动配置，所以我们只需要配置相关属性的值，它就会自动配置，配置在application.properties文件中。

```java
#访问根路径

#应用名称
spring.application.name=springboot-stxcx

#访问端口号
server.port=8080

#编码格式
server.tomcat.url-encoding=utf-8

#数据库相关配置
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.datasource.url=jdbc:mysql://localhost:3306/stxcx
spring.datasource.username=root
spring.datasource.password='123456'
spring.datasource.max-idle=10
spring.datasource.max-wait=10000
spring.datasource.min-idle=5
spring.datasource.initial-size=5

#session生命周期
server.servlet.session.timeout=30m
```


当然，如果此时你还不想配置，你也可以声明一下
启动类头部声明：

```java
@SpringBootApplication(exclude= {DataSourceAutoConfiguration.class})
```


感谢观看，如果有帮到小伙伴，请点赞哦！！！
