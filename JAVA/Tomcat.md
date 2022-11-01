# Tomcat

[TOC]

## windows 操作

## linux 操作

1. 查看实时日志文件 ： `[tomcat路径]/logs/tail -f catalina.out`
2. 实时查看日志文件最后n行 ： `[tomcat路径]/logs/tail -n 200 -f catalina.out`
3. 退出tail命令 ： `[tomcat路径]/logs/ctrl + C`
4. 翻页查看 日志文件 ： `[tomcat路径]/less catalina.out`
    运行时直接显示启动日志：`[tomcat路径]/bin/catalina.sh]`
    `G`  //回到文本末尾
    `page up` //向上翻页
    `page down` //向下翻页

5. tail高亮展示关键词
    【此功能，可以在使用xshell的使用，直接在页面搜索 就可以，不用这么复杂的命令】

    `tail -n 200 -f dpe_partner_all.log | perl -pe 's/(关键词)/\e[1;31m$1\e[0m/g'`

    例如高亮显示ERROR
    `tail -n 200 -f dpe_partner_all.log | perl -pe 's/(ERROR)/\e[1;31m$1\e[0m/g'`

## tomcat 配置

$~~~~~$ tomcat 作为一个容器，优势在于有许多的配置，可以在不侵入服务的情况下进行。
$~~~~~$ 其配置文件在 tomcat 安装目录下的 conf/server.xml 。

打开配置文件，我们可以看到如下的信息

```xml
<?xml version="1.0" encoding="UTF-8"?>

<Server port="8005" shutdown="SHUTDOWN">
  <Listener className="org.apache.catalina.startup.VersionLoggerListener" />

  <Listener className="org.apache.catalina.core.AprLifecycleListener" SSLEngine="on" />

  <Listener className="org.apache.catalina.core.JreMemoryLeakPreventionListener" />
  <Listener className="org.apache.catalina.mbeans.GlobalResourcesLifecycleListener" />
  <Listener className="org.apache.catalina.core.ThreadLocalLeakPreventionListener" />

  <GlobalNamingResources>

    <Resource name="UserDatabase" auth="Container"
              type="org.apache.catalina.UserDatabase"
              description="User database that can be updated and saved"
              factory="org.apache.catalina.users.MemoryUserDatabaseFactory"
              pathname="conf/tomcat-users.xml" />
  </GlobalNamingResources>

  <Service name="Catalina">

    <Connector port="80" protocol="HTTP/1.1"
               connectionTimeout="20000"
               redirectPort="8443" />

    <Engine name="Catalina" defaultHost="localhost">

      <Realm className="org.apache.catalina.realm.LockOutRealm">

        <Realm className="org.apache.catalina.realm.UserDatabaseRealm"
               resourceName="UserDatabase"/>
      </Realm>

      <Host name="localhost"  appBase="webapps"
            unpackWARs="true" autoDeploy="true">
            <Context path="/" docBase="../webapps/MainPage" crossContext="true" reloadable="true"/>
            <Context path="/MainPageSQL" docBase="../webapps/MainPageSQL" crossContext="true" reloadable="true"/>

      </Host>
    </Engine>
  </Service>
</Server>
```

以上内容是我删除了注释，但这不代表注释不重要。相反，阅读注释可以了解的比本文更深内容。

在该文件中，我们通常只用关注以下几个内容

```xml

<!-- 容器关闭接口 -->
<Server port="8005" shutdown="SHUTDOWN">

<!-- 容器访问接口 -->
<Connector port="80" protocol="HTTP/1.1"
            connectionTimeout="20000"
            redirectPort="8443" />

<!-- 容器服务配置 -->
<Host name="localhost"  appBase="webapps"
      unpackWARs="true" autoDeploy="true">

      <Context path="/" docBase="../webapps/MainPage" crossContext="true" reloadable="true"/>
      <Context path="/MainPageSQL" docBase="../webapps/MainPageSQL" crossContext="true" reloadable="true"/>
```

下面对上面每个标签的含义作出解释

- `Server` : 服务，每个 server 就是一个 tomcat 服务
- `Connector` : 连接配置，每个服务中只有一个连接配置
- `Host` : 容器，也有人叫做虚拟机，每个服务可以有多个容器
- `Context` : url 服务前缀，如 `localhost:1200/vdx` ，在域名/ip地址、端口后面的就是该地址的 url 路径，tomcat 默认是通过服务的文件夹名来访问服务的，也就是说默认的 url 路径就是文件夹名

下面将依次对以上属性进行解释

- `<Server port="8005" shutdown="SHUTDOWN">`
  $~~~~~$ `port` : 关闭接口，访问该接口，并输入 `shutdown` 设置的值就可关闭容器。当存在多个 tomcat 容器时建议修改接口。
- `<Connector port="80" protocol="HTTP/1.1" connectionTimeout="20000" redirectPort="8443" />`
  - `port` : 容器内服务的 http 访问端口
  - `protocol` : 该端口的 http 协议 ，通常不会改变它
  - `connectionTimeout` : 连接超时时间，单位毫秒
  - `redirectPort` : 如果访问 `port` 端口的是 `https` 协议，就会跳转到该端口。

- `<Host name="localhost"  appBase="webapps" unpackWARs="true" autoDeploy="true">`
    该属性可以自定义多个容器，通过不同的 name 来访问不同的容器
  - `name` : 容器名，网络访问时 `www.123456.com` 或 `localhost` 就是访问的这个名
  - `appBase` : 容器位置，可以填绝对路径或相对路径，相对路径起始位置为 tomcat 根路径。

- `<Context path="/" docBase="../webapps/MainPage" crossContext="true" reloadable="true"/>`
    该属性可以修改服务的访问 url
  - `path` : 路径名
  - `docBase` : 服务的文件路径

以上内容需要注意包含关系。

## Springboot 项目部署

$~~~~~$ 对于 Springboot 而言，部署到 Tomcat 是一个不具备性价比的选择，因为 tomcat 的性质，注定了其运行效率与并发数量不会太高，通常一个 Spingboot 项目就能吃满，而且无法通过端口直接访问项目了。Springboot 官方也推荐直接打包成 jar 文件，使用 `java -jar XXX.jar` 通过内置的 tomcat 运行。
$~~~~~$ 但是对于小项目，或者想要利用 tomcat 容器的一些功能，还是可以的 tomcat 的。

1. 由于 tomcat 容器与 内置的 tomcat 插件有很大的不同，最影响的两点就是注册中心与启动类。

    1. Springboot的启动类在 tomcat 中无法被识别，所有我们需要修改启动类。
        原来的启动类是这样的

        ```java
        public class Application {

            public static void main(String[] args) {
                new SpringApplicationBuilder(Application.class).web(true).run(args);
            }
        }
        ```

        为了能让 tomcat 识别到启动类，我们需要继承SpringBootServletInitializer类，并重写覆盖configure方法，修改后的启动类如下

        ```java
        public class Application extends SpringBootServletInitializer {

            @Override
            protected SpringApplicationBuilder configure(SpringApplicationBuilder builder) {
                return builder.sources(Application.class);
            }

            public static void main(String[] args) {
                new SpringApplicationBuilder(Application.class).web(true).run(args);
            }
        }
        ```

    2. 然后，我们需要修改 pom.xml 配置文件，禁用 SpringBoot 的内置 tomcat ，内置 tomcat 在 `spring-boot-starter-web` 被引入了，因此我们需要把该依赖修改以下，禁用 tomcat

        ```xml
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
            <!-- 移除嵌入式tomcat插件 -->
            <exclusions>
                <exclusion>
                    <groupId>org.springframework.boot</groupId>
                    <artifactId>spring-boot-starter-tomcat</artifactId>
                </exclusion>
            </exclusions>
        </dependency>
        ```

    3. 如果我们配置了注册中心，那就更麻烦了，Springboot 默认的向注册中心注册是在启动时，但是项目放在tomcat 中可不会管你，所以我们需要新建一个事务类，用以向注册中心提交数据。

       ```java
       @Configuration
       @ConditionalOnConsulEnabled
       @ConditionalOnMissingBean(type= "org.springframework.cloud.consul.discovery.ConsulLifecycle")
       @AutoConfigureAfter(ConsulAutoServiceRegistrationAutoConfiguration.class)
       public class MyConsulListener implements ApplicationContextAware {

           @Autowired(required=false)
           private ConsulAutoServiceRegistration registration;

           public void setApplicationContext(ApplicationContext context) throws BeansException {
               if (registration != null){
                   registration.start();
               }
           }
       }
       ```

    然后，我们需要修改yml 配置文件，将该服务的端口号告诉 consul

    ```properties
    # 注意按照 yml 瀑布格式确认放入位置
    spring.cloud.consul.discovery.port=${server.port}
    ```

2. 之后，我们将项目打包成 war 格式，对于 maven 而言，我们需要先在配置文件中设置 `<packaging>war</packaging>` ，让项目以 war 形式打包，然后通过 `claean` 清除原来的编译文件，再通过 `package` 将项目打包。

3. 然后，我们就能在项目中看到一个 `target` 文件，在其中找到一个 war 文件，通常命名方式为我们 pom 文件中的 `<artifactId>-<version>.war` 。

4. 我们 war 文件放入我们的 tomcat 目录下的 `webapps` 中，启动 tomcat 就能访问了，注意访问 tomcat 访问是 `tomcat访问地址＋服务文件名`
   $~~~~~$ 但是在 tomcat 中依旧会出现不影响基础使用的报错，具体怎么解决我并未进行研究，因为做到这里，我已经选择用 Springboot 推荐的 jar 启动模式，自动启动的功能，但是我可以写一个 bat 文件来做到这件事。
