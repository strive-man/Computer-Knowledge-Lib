# JAVA启动项目-父项目示例

```java
<?xml version="1.0" encoding="UTF-8"?>

<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.ktkg.tust</groupId>
    <artifactId>kids-attention-center</artifactId>
    <version>1.0-SNAPSHOT</version>
//管理的子模块如下
    <modules>
        <module>kids-attention-commons</module>
        <module>kids-attention-gateway-9992</module>
        <module>renren-generator</module>
        <module>kids-attention-userregistration-9301</module>
        <module>kids-attention-member-9025</module>
        <module>kids-attention-emp-9601</module>
    </modules>
    // 这句话声明了当前的pom文件是父项目         
    <packaging>pom</packaging>
    <name>kids-attention-center</name>
    <url>http://www.example.com</url>
    //这里也很关键省的老是出现编译是的版本问题
	<properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <maven.compiler.source>11.0</maven.compiler.source>
        <maven.compiler.target>11.0</maven.compiler.target>
    </properties>

    <!--指定了相关依赖版本，如下-->
       //父项目处指定我们要用的依赖的版本这点非常重要
      //1是统一版本，之后的字模块中无需考虑版本的事，无需配置版本
      //2是版本的统一基本避免了，因为后期引入依赖出现依赖冲突问题，因为很多依赖引入进来它本身会有很多依赖
    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-dependencies</artifactId>
                <version>2.2.2.RELEASE</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
            <!--SB 和 SC 版本是需对应的-->
            <dependency>
                <groupId>org.springframework.cloud</groupId>
                <artifactId>spring-cloud-dependencies</artifactId>
                <version>Hoxton.SR1</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
            <!--配置cloud-alibaba-->
            <dependency>
                <groupId>com.alibaba.cloud</groupId>
                <artifactId>spring-cloud-alibaba-dependencies</artifactId>
                <version>2.1.0.RELEASE</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
            <dependency>
                <groupId>com.alibaba</groupId>
                <artifactId>druid-spring-boot-starter</artifactId>
                <version>1.2.8</version>
            </dependency>
            <dependency>
                <groupId>com.baomidou</groupId>
                <artifactId>mybatis-plus-boot-starter</artifactId>
                <version>3.4.3</version>
            </dependency>
            <!--日志输出 log4j2 和 sj4j 是配合使用的-->
            <dependency>
                <groupId>org.apache.logging.log4j</groupId>
                <artifactId>log4j</artifactId>
                <version>2.17.2</version>
            </dependency>
            <!--日志输出-->
            <dependency>
                <groupId>org.slf4j</groupId>
                <artifactId>slf4j-api</artifactId>
                <version>1.7.28</version>
            </dependency>
            <!--用于entity下的类-->
            <dependency>
                <groupId>org.projectlombok</groupId>
                <artifactId>lombok</artifactId>
                <version>1.18.20</version>
            </dependency>
            <dependency>
                <groupId>mysql</groupId>
                <artifactId>mysql-connector-java</artifactId>
                <version>8.0.31</version>
            </dependency>
            <!--JSR303数据校验-->
            <dependency>
                <groupId>org.hibernate</groupId>
                <artifactId>hibernate-validator</artifactId>
                <version>6.1.0.Final</version>
            </dependency>
            <!--junit,做测试用的-->
            <dependency>
                <groupId>junit</groupId>
                <artifactId>junit</artifactId>
                <version>4.11</version>
                <scope>test</scope>
            </dependency>
        </dependencies>
    </dependencyManagement>
</project>


        
```

```yml
//关于对数据库连接的yml文件配置示例
//driver-class-name: com.mysql.cj.jdbc.Driver，在连接数据库8的时候写这个读了个cj

spring:
  datasource:
    url: jdbc:mysql://localhost:3306/zgq_manage?useUnicode=true&characterEncoding=utf-8&useSSL=false
    driver-class-name: com.mysql.cj.jdbc.Driver
    username: root
    password: 123456
mybatis-plus:
  configuration:
    //实现数据库的短横线字段到Entity里是驼峰命名 video_info=>cvideoInfo
    map-underscore-to-camel-case: true 
  mapper-locations: classpath:/mapper/*.xml
```

